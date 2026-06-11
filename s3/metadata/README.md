## Create bucket

aws s3 mb s3://metadata-bucket-jzhu

## Create new file

echo "Hello world" > hello.txt

## Upload file w metadata

aws s3api put-object --bucket metadata-bucket-jzhu --key hello.txt --body hello.txt --metadata KeyName1=string,KeyName2=string,Planet=Mars

## Get metadata thru headobject

aws s3api head-object --bucket metadata-bucket-jzhu --key hello.txt 