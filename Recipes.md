# Recipes

1. Create a dummy file of a certain n-bytes size  
```
# Syntax: `dd if=/dev/urandom bs=<bytes_size> of=<file_name>`
$ dd if=/dev/urandom bs=1024 of=myfile
```

2. Disable SSL verification for a repository  
Maybe you are behind a company firewall which intercepts your CA key.
```
git config --local http.sslVerify false # only do this if you are certain there will be no issue
```