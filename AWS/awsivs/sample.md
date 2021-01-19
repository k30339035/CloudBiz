IVS Region: us-west-2

```
aws s3api create-bucket --bucket <my-bucket-name> --region <my-region> \
--create-bucket-configuration LocationConstraint=<my-region>
```

```
aws s3api create-bucket --bucket sungsuivschat3 --region ap-northeast-2 --create-bucket-configuration LocationConstraint=ap-northeast-2
{
    "Location": "http://sungsuivschat.s3.amazonaws.com/"
}
```
```
sam package \
--template-file template.yaml \
--output-template-file packaged.yaml \
--s3-bucket <my-bucket-name>
```

```
sam package --template-file template.yaml --output-template-file packaged.yaml --s3-bucket sungsuivschat1
SAM CLI now collects telemetry to better understand customer needs.

        You can OPT OUT and disable telemetry collection by setting the
        environment variable SAM_CLI_TELEMETRY=0 in your shell.
        Thanks for your help!

        Learn More: https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-telemetry.html

Uploading to d5f16bfde93671728349011ce6e42432  2710 / 2710.0  (100.00%)

Successfully packaged artifacts and wrote output template to file packaged.yaml.
Execute the following command to deploy the packaged template
sam deploy --template-file C:\git\amazon-ivs-simple-chat-web-demo\serverless\packaged.yaml --stack-name <YOUR STACK NAME>

```

sam deploy \
--template-file packaged.yaml \
--stack-name <my-stack-name> \
--capabilities CAPABILITY_IAM


sam deploy --template-file packaged.yaml --stack-name sungsuivschat3 --capabilities CAPABILITY_IAM

sam deploy --template-file C:\git\amazon-ivs-simple-chat-web-demo\serverless\packaged.yaml --stack-name sungsuivschat


sam deploy \
--template-file packaged.yaml \
--stack-name <my-stack-name> \
--capabilities CAPABILITY_IAM \
--parameter-overrides TableName=<my-table-name>

*+-*
                                                        
sam deploy --template-file packaged.yaml --stack-name sungsuivschat2 --capabilities CAPABILITY_IAM --parameter-overrides TableName=products


