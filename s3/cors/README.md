# Create website 1
## Create a bucket
```sh
aws s3 mb s3://cors-fun-jz
```
## Change block public access

```sh
aws s3api put-public-access-block \
--bucket cors-fun-jz \
--public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=false,RestrictPublicBuckets=false"
```

## Create a bucket policy

```sh
aws s3api put-bucket-policy --bucket cors-fun-jz --policy file://bucket-policy.json
```

## TUrn on static website hosting

```sh
aws s3api put-bucket-website --bucket cors-fun-jz --website-configuration file://website.json
```

## upload index.html file, iclude a resource that would be cross-origin

```sh
aws s3 cp index.html s3://cors-fun-jz
```

## view website and see if index.html is there

```sh
http://cors-fun-jz.s3-website.us-east-1.amazonaws.com
```

# Create website 2
```sh
aws s3 mb s3://cors-fun-jz-2
```

## Change block public access

```sh
aws s3api put-public-access-block \
--bucket cors-fun-jz-2 \
--public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=false,RestrictPublicBuckets=false"
```

## Create a bucket policy

```sh
aws s3api put-bucket-policy --bucket cors-fun-jz-2 --policy file://bucket-policy2.json
```

## TUrn on static website hosting

```sh
aws s3api put-bucket-website --bucket cors-fun-jz-2 --website-configuration file://website.json
```

## Upload js file

```sh
aws s3 cp hello.js s3://cors-fun-jz-2
```

## create API gateway with mock response and test endpoint
curl -X POST -H "Content-Type: application/json" https://1dhlrs8dza.execute-api.us-east-1.amazonaws.com/prod/hello

## upload index.html file, iclude a resource that would be cross-origin

```sh
aws s3 cp index.html s3://cors-fun-jz-2
```

## apply a CORS policy on bucket

aws s3api put-bucket-cors --bucket cors-fun-jz --cors-configuration file://cors.json
