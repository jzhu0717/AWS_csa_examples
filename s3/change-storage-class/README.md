## Create a bucket

aws s3 mb s3://class-fun-jz0717

## Create a file
 
echo "Hello world" > hello.txt
aws s3 cp hello.txt s3://class-fun-jz0717 --storage-class STANDARD_IA

## Cleanup

aws s3 rm s3://class-fun-jz0717/hello.txt
aws s3 rb s3://class-fun-jz0717



