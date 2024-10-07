# Recipes

1. Create a dummy file of a certain n-bytes size
Syntax: `dd if=/dev/urandom bs=<bytes_size> of=<file_name>`

```
dd if=/dev/urandom bs=1024 of=myfile
```