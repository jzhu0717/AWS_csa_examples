## Create a user with no permissions

also generate out access keys

```sh
aws iam create-user --user-name sts-machine-user
aws iam create-access-key --user-name sts-machine-user --output table
```

Copy access key and secret, then edit credientials file to change away from default profile
```sh
aws configure
nano ~/.aws/credentials
```

Test who you are
```sh
aws sts get-caller-identity --profile sts
```

Make sure you don't have access to s3
```sh
aws s3 ls --profile sts
```
> aws: [ERROR]: An error occurred (AccessDenied) when calling the ListBuckets operation: User: arn:aws:iam::029179923921:user/sts-machine-user is not authorized to perform: s3:ListAllMyBuckets because no identity-based policy allows the s3:ListAllMyBuckets action

## Create a new role

Create a role that will access a new resource
```sh
chmod u+x bin/deploy
./bin/deploy
```

## Use new user credentials and assume role

```sh
aws iam put-user-policy \
    --user-name sts-machine-user \
    --policy-name StsAssumePolicy \
    --policy-document file://policy.json

aws sts assume-role --role-arn arn:aws:iam::029179923921:role/my-sts-fun-stack-StsRole-9Xdcau7QECkL --role-session-name s3-sts-fun --profile sts
```

```sh
aws sts get-caller-identity --profile assumed
```

```sh
aws s3 ls --profile assumed
aws s3 ls s3://sts-fun-jzhu0717 --profile assumed
```

## Cleanup

tear down cloudformation stack via AWS management console

```sh
aws iam delete-user-policy --user-name sts-machine-user --policy-name StsAssumePolicy
aws iam delete-access-key --access-key-id AKIAQNS2CJXIQYW3BPP7 --user-name sts-machine-user
aws iam delete-user --user-name sts-machine-user
```