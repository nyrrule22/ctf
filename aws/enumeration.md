# Enumeration

## S3

### Checks

* Do we have access to an S3 Bucket? i.e. navigate to the URL in a browser
  * https://bucket.aws.amazonaws.com
* Is it a static website?
  * View page source looking for other potential bucket URLs/sources or secrets
* Is it an XML representation of the bucket contents?
  * Any interesting \<Key> names we can navigate to
    * https://bucket.aws.amazonaws.com/\<Key>
      * Any additional URLs, secrets, etc.
* Do any logs or files contain an `AWS_SECRET_ACCESS_KEY` and an `AWS_ACCESS_KEY_ID`?
  * If so, we can try to authenticate and view more data

```bash
aws configure
AWS Access Key ID: <AWS_ACCESS_KEY_ID>
AWS Secret Access Key: <AWS_SECRET_ACCESS_KEY>

aws s3 ls  # Check which buckets are available to use
aws s3 ls <bucket-name>  # Check the contents of a bucket
aws s3api get-bucket-tagging --<bucket-name>  # Check for any bucket tags
# If you can't view specific file in a found bucket, you may be able to copy it locally
aws s3 cp s3://<bucket-name>/file-name .

aws lambda list-functions  # Check for any lambda functions
aws lambda list-tags --resource <FunctionArn>  # Check for lambda function tags

aws ec2 describe-tags  # Check for ec2 instance tags
```

### Potential Bad Request

When navigating to a S3 bucket URL and you get a `405 Request method 'GET' not allowed` error, you can try modifying the request type i.e. `POST`, `XPOST`, `PUT`, `HEAD`, `OPTIONS`, etc.
