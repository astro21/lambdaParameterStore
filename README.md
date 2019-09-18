# lambdaParameterStore
Sharing Secrets with AWS Lambda Using AWS Systems Manager Parameter Store
https://aws.amazon.com/blogs/compute/sharing-secrets-with-aws-lambda-using-aws-systems-manager-parameter-store/

The following blog post provides a CloudFormation template. When deploying the template, I keep getting the following error:

"The new key policy will not allow you to update the key policy in the future. (Service: AWSKMS; Status Code: 400; Error Code: MalformedPolicyDocumentException;"

The cause of the issue is that the following statement is missing in the key policy:

      {
            "Sid": "Allow use of the key",
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::<aws-account-id>:root"
            },
            "Action": "kms:*",
            "Resource": "*"
        }
 
 I updated the CloudFormation template provided in the blog post and was able to deploy the template successfully.
