# Recipes

1. Create a dummy file of a certain n-bytes size (file contains jumbled binary data)
```
# Syntax: `dd if=/dev/urandom bs=<bytes_size> of=<file_name>`
dd if=/dev/urandom bs=1024 of=myfile
```

2. Disable SSL verification for a repository  
- Maybe you are behind a company firewall which intercepts your CA key.
```
git config --local http.sslVerify false # only do this if you are certain there will be no issue
```

3. Build docker images (WSL2)
```
docker buildx build -t <image>:<tag> <dockerfile_dir>
```

4. Reconfigure DNS resolver in WSL2 after Windows 10 -> 11 upgrade

- Upgrading Win10 to Win11 will not affect your existing WSL2 installation, but you might encounter issues like:
```
$ ping github.com
ping: github.com: Temporary failure in name resolution
```

- Now, you might be thinking that something is wrong in DNS resolution and you want to check the content  
of /etc/resolv.conf
- When checking `/etc/resolv.conf` maybe you'll encounter the following error:
```
cat: /etc/resolve.conf: No such file or directory
```

- It's not there! So you need to create a new one:
```
sudo touch /etc/resolv.conf
```

- Then you add the name resolver configuration:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

- After that, you need to set `resolv.conf` immutable:
```
sudo chattr +i /etc/resolv.conf
```

5. Quick hack: cleaning up Rust folders
```
# Run this in the "parent" Rust folders
for i in `ls`; do cd $i; cargo clean; pwd; cd ..; pwd; done
```