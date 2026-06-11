## Create a new s3 bucket

```md
aws s3 mb s3://checksums-example-jzhu
```

## Create a file to do checksum on

```
echo "hello world" > myfile.txt
```

## Get checksum of a file for md5

```md
md5sum myfile.txt
# 5eb63bbbe01eeed093cb22bb8f5acdc3  myfile.txt
```

## Upload file to see

```
aws s3 cp myfile.txt s3://checksums-example-jzhu
aws s3api head-object --bucket s3://checksums-example-jzhu --key myfile.txt
```

## Upload a file w a different type of checksum

