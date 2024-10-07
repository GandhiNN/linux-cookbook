# Recipes

1. Create a dummy file of a certain n-bytes size (file contains jumbled binary data)
```
# Syntax: `dd if=/dev/urandom bs=<bytes_size> of=<file_name>`
dd if=/dev/urandom bs=1024 of=myfile
```

2. Disable SSL verification for a repository  
Maybe you are behind a company firewall which intercepts your CA key.
```
git config --local http.sslVerify false # only do this if you are certain there will be no issue
```

3. Build docker images (WSL2)
```
docker buildx build -t <image>:<tag> <dockerfile_dir>
```