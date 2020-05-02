![](https://travis-ci.org/aws-samples/aws-lambda-layer-kubectl.svg?branch=master)
![](https://codebuild.us-west-2.amazonaws.com/badges?uuid=eyJlbmNyeXB0ZWREYXRhIjoiNy9vYjN0bFpiN0VrdGFVOVRFL1ZHLzVLcjVsenNDcmJ0ejdIbW8raldHRzkvMGtVK1JhaUVnTk0vNWxucGdMc0JvU01JdUlNQkhpRzZqZEdPalRwL2hjPSIsIml2UGFyYW1ldGVyU3BlYyI6ImFQdnVlWmZFYi9abGhyZG8iLCJtYXRlcmlhbFNldFNlcmlhbCI6MX0%3D&branch=master)
[![](https://img.shields.io/badge/Available-serverless%20app%20repository-blue.svg)](https://serverlessrepo.aws.amazon.com/applications/arn:aws:serverlessrepo:us-east-1:903779448426:applications~lambda-layer-kubectl)


# lambda-layer-kubectl

**aws-lambda-layer-kubectl** is an [AWS Lambda Layer](https://docs.aws.amazon.com/en_us/lambda/latest/dg/configuration-layers.html) that encapsulates all the required assets to interact with **Amazon EKS** control plane and help you directly **`kubectl`** against Amazon EKS in AWS Lambda.



## Features

- [x] Ships all the required assests including **kubectl**, **aws-cli**, **make** and **jq** Just include the layer and you get everything required.
- [x] **Helm 3** included.
- [x] Amazon EKS authentication under the hood on bootstrap.



## Current Version

| kubectl      | v1.15.10-eks-bac369     |
| :----------- | :----------- |
| **awscli**   | **1.18.37** |
| **helm**     | **3.1.2**    |
| **jq**       | **1.6**      |
| **GNU Make** | **3.82**     |



## Layer structure

You got the layer structure as below under `/opt` in lambda custom runtime:

```
.
├── awscli
│   ├── PyYAML-5.1.2-py2.7.egg-info
│   ├── aws
│   ├── awscli
│   ├── awscli-1.16.292-py2.7.egg-info
│   ├── bin
│   ├── botocore
│   ├── botocore-1.13.28-py2.7.egg-info
│   ├── colorama
│   ├── colorama-0.4.1-py2.7.egg-info
│   ├── concurrent
│   ├── dateutil
│   ├── docutils
│   ├── docutils-0.15.2-py2.7.egg-info
│   ├── easy_install.py
│   ├── easy_install.pyc
│   ├── futures-3.3.0-py2.7.egg-info
│   ├── jmespath
│   ├── jmespath-0.9.4-py2.7.egg-info
│   ├── jq
│   ├── make
│   ├── pkg_resources
│   ├── pyasn1
│   ├── pyasn1-0.4.8-py2.7.egg-info
│   ├── python_dateutil-2.8.0-py2.7.egg-info
│   ├── rsa
│   ├── rsa-3.4.2-py2.7.egg-info
│   ├── s3transfer
│   ├── s3transfer-0.2.1-py2.7.egg-info
│   ├── six-1.13.0-py2.7.egg-info
│   ├── six.py
│   ├── six.pyc
│   ├── urllib3
│   ├── urllib3-1.25.7-py2.7.egg-info
│   ├── wheel
│   ├── wheel-0.29.0.dist-info
│   └── yaml
├── helm
│   └── helm
└── kubectl
    └── kubectl

32 directories, 9 files
```



## Supported Lambda Runtime

| lambda runtime | runtime attribute name in CFN/SAM | Remarks                                                      |
| -------------- | --------------------------------- | ------------------------------------------------------------ |
| Custom Runtime | provided                          | you need bundle the bootstrap in your lambda function bundle([example](https://github.com/aws-samples/aws-lambda-layer-kubectl/blob/master/samples/create-k8s-objects/bootstrap)) |



# HOWTO

You may install the Layer from `SAR` or just build it from scratch.


## OPTION #1 - Install from SAR(Serverless App Repository)

This is the recommended approach. We deploy the kubectl lambda layer straight from `SAR(Serverless App Repository)`

You may deploy it from the console, AWS CDK or CLI.

### Deploy from SAR console

|        Region        |                    Click and Deploy                     |
| :----------------: | :----------------------------------------------------------: |
|  **ap-northeast-1**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/ap-northeast-1/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **ap-east-1**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/ap-east-1/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **ap-northeast-2**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/ap-northeast-2/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **ap-northeast-3**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/ap-northeast-3/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **ap-south-1**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/ap-south-1/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **ap-southeast-1**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/ap-southeast-1/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **ap-southeast-2**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/ap-southeast-2/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **ca-central-1**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/ca-central-1/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **eu-central-1**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/eu-central-1/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **eu-north-1**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/eu-north-1/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **eu-west-1**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/eu-west-1/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **eu-west-2**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/eu-west-2/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **eu-west-3**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/eu-west-3/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **me-south-1**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/me-south-1/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **sa-east-1**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/sa-east-1/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **us-east-1**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/us-east-1/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **us-east-2**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/us-east-2/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **us-west-1**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/us-west-1/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **us-west-2**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://deploy.serverlessrepo.app/us-west-2/?app=arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl)|
|  **cn-north-1**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://console.amazonaws.cn/lambda/home?region=cn-north-1#/create/app?applicationId=arn:aws-cn:serverlessrepo:cn-north-1:487369736442:applications/lambda-layer-kubectl)|
|  **cn-northwest-1**  |[![](https://img.shields.io/badge/SAR-Deploy%20Now-yellow.svg)](https://console.amazonaws.cn/lambda/home?region=cn-northwest-1#/create/app?applicationId=arn:aws-cn:serverlessrepo:cn-north-1:487369736442:applications/lambda-layer-kubectl)|






### Deploy with AWS CDK

```js
import cdk = require('@aws-cdk/core');
import sam = require('@aws-cdk/aws-sam');
import lambda = require('@aws-cdk/aws-lambda');

// Keep the class name stable please
export class AppStack extends cdk.Stack {
    constructor(scope: cdk.Construct, id: string, props?: cdk.StackProps) {
        super(scope, id, props);
    
        const samApp = new sam.CfnApplication(this, 'SamLayer', {
          location: {
            applicationId: 'arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl',
            semanticVersion: '2.0.0-beta3'
          },
          parameters: {
            LayerName: `${this.stackName}-kubectl-layer`
          }
        })

      const layerVersionArn = samApp.getAtt('Outputs.LayerVersionArn').toString();
      new cdk.CfnOutput(this, 'LayerVerionArn', { value: layerVersionArn })

    }
}
```

or play with it at https://play-with-cdk.com?s=99acb08caf74fc982ebfa931da476888



### Deploy with AWS CLI

Alternatively, you may deploy it with AWS CLI.


```sh
$ APP_ID='arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl'

$ LATEST_VERSION=$(aws serverlessrepo get-application --application-id ${APP_ID} --query 'Version.SemanticVersion' --output text)

$ aws --region ${REGION_CODE_TO_DEPLOY} serverlessrepo create-cloud-formation-template \
--application-id  ${APP_ID} \
--semantic-version ${LATEST_VERSION}

{
    "Status": "PREPARING", 
    "TemplateId": "89be5908-520b-4911-bde7-71bf73040e47", 
    "CreationTime": "2019-02-20T14:51:56.826Z", 
    "SemanticVersion": "...", 
    "ExpirationTime": "2019-02-20T20:51:56.826Z", 
    "ApplicationId": "arn:aws:serverlessrepo:us-east-1:903779448426:applications/lambda-layer-kubectl", 
    "TemplateUrl": "..."
}
```
(change `REGION_CODE_TO_DEPLOY` to the region code to deploy this layer(e.g. `ap-northeast-1` or `us-west-2`)


Copy the `TemplateUrl` value and deploy with `cloudformation create-stack`


```sh
aws --region ${REGION_CODE_TO_DEPLOY} cloudformation create-stack --template-url {TemplateUrl} --stack-name {StackName} --capabilities CAPABILITY_AUTO_EXPAND \
--parameter ParameterKey=LayerName,ParameterValue=lambda-layer-kubectl
```

On stack create complete, get the stack outputs as below

```sh
$ aws --region ${REGION_CODE_TO_DEPLOY} cloudformation describe-stacks --stack-name {StackName} --query 'Stacks[0].Outputs'
[
    {
        "Description": "ARN for the published Layer version", 
        "ExportName": "LayerVersionArn-{StackName}", 
        "OutputKey": "LayerVersionArn", 
        "OutputValue": "arn:aws:lambda:ap-northeast-1:123456789012:layer:lambda-layer-kubectl:1"
    }
]
```


Now you got your own private Lambda Layer Arn for `lambda-layer-kubectl`.




## OPTION #2 - Build from scratch

1. check out this repository 

```sh
$ curl -L -o lambda-layer-kubectl.zip https://github.com/pahud/lambda-layer-kubectl/archive/master.zip
$ unzip lambda-layer-kubectl.zip
$ cd lambda-layer-kubectl-master
```

or just 

```sh
$ git clone https://github.com/aws-samples/aws-lambda-layer-kubectl.git
```

2. build the `layer.zip` bundle


```sh
# build the layer locally and bundle everything into a layer.zip file
$ make build
```

(this may take a moment to complete)


3. edit the `Makefile`

| Name                 | Description                                                  | required to update |
| -------------------- | ------------------------------------------------------------ | ------------------ |
| **LAYER_NAME**       | Layer Name                                                   |                    |
| **LAYER_DESC**       | Layer Description                                            |                    |
| **INPUT_JSON**       | input json payload file for lambda invocation                |                    |
| **S3BUCKET**         | Your S3 bucket to store the intermediate Lambda bundle zip.<br />Make sure the S3 bucket in the same region with your Lambda function to deploy. | YES                |
| **LAMBDA_REGION**    | The region code to deploy your Lambda function               |                    |
| **LAMBDA_FUNC_NAME** | Lambda function name                                         |                    |
| **LAMBDA_ROLE_ARN**  | Lambda IAM role ARN                                          | YES                |



### Required Policy for Lambda IAM Role

Please note your IAM role for Lambda will need `eks:DescribeCluster` as well as other ec2 read-only privileges depending on what you intend to do in your Lambda function. You may attach an inline policy as below to your Lambda IAM role.

```js
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeInstances",
                "ec2:DescribeTags",
                "eks:DescribeCluster"
            ],
            "Resource": "*"
        }
    ]
}
```



4. Deploy the Layer

```sh
# deploy and publish the layer.zip as a layer version
$ make sam-layer-deploy
```

This will deploy the `layer.zip` and publish as a new layer version. 

![](images/sam-layer-deploy.png)



OK. Now your layer is ready.

Please copy the value of `OutputValue`.


## Build and Publish your Layer to SAR(Serverless App Repository)

publish to SAR in `us-east-1` for AWS global regions
```bash
$ AWS_DEFAULT_PROFILE={PORFILE_NAME} LAMBDA_REGION=cn-north-1 S3BUCKET={YOUR_STAGING_BUCKET} SAR_APP_NAME={YOUR_SAR_APP_NAME} make publish-new-layerversion-to-sar
```

This will publish your layer as `{YOUR_SAR_APP_NAME}` to SAR(Serverless App Repository). You can optionally make it public in your SAR console.

## Note for AWS China regions

publish to SAR in `cn-north-1` for AWS China regions
```bash
$ AWS_DEFAULT_PROFILE={PORFILE_NAME} LAMBDA_REGION=cn-north-1 S3BUCKET={YOUR_STAGING_BUCKET} SAR_APP_NAME={YOUR_SAR_APP_NAME} make publish-new-layerversion-to-sar-cn
```

If you have successfully published to `cn-north-1` in AWS China region, the SAR URL would be:
```
https://console.amazonaws.cn/serverlessrepo/home?region=cn-north-1#/published-applications/arn:aws-cn:serverlessrepo:cn-north-1:{AWS_ACCOUNT_ID}:applications~lambda-layer-kubectl
```


## Deploy the sample stack with AWS CDK

The following sample provision an Amazon EKS cluster and sample lambda function with kubectl lambda layer and you can write your logic in `main.sh`

```ts
    const cluster = new eks.Cluster(this, 'EksCluster', {
      vpc,
      mastersRole
    })

    // publih a layer version from the layer.zip we built from build.sh
    const layerVersion = new lambda.LayerVersion(this, 'cdk-aws-lambda-layer-kubectl', {
      code: new lambda.AssetCode( path.join(__dirname, '../../layer.zip')),
      compatibleRuntimes: [ lambda.Runtime.PROVIDED ]
    })

    // create a lambda function with this layer
    const fn = new lambda.Function(this, 'KubectlLayerDemoFunc', {
      code: new lambda.AssetCode(path.join(__dirname, '../../func-bundle.zip')),
      handler: 'main',
      runtime: lambda.Runtime.PROVIDED,
      layers: [ layerVersion ],
      timeout: cdk.Duration.seconds(30),
      memorySize: 256,
      environment: {
        'cluster_name': cluster.clusterName,
      }
    })

    // add describe cluster permission to the lambda role
    fn.role!.addToPolicy(new iam.PolicyStatement({
      actions: [ 'eks:DescribeCluster' ],
      resources: [ cluster.clusterArn ]
    }))
    // add the lambda func role to the aws-auth config map as system:masters
    cluster.awsAuth.addMastersRole(fn.role!)
```
Read the full CDK sample in the [cdk](./cdk/README.md) directory


# More Samples
check [samples](./samples) directory


## Cross-Accounts Access

In some cases, you may need cross-account access to different Amazon EKS clusters. The idea is to generate different kubeconfig files and feed the lambda function via environment variables. Check [this sample](https://github.com/aws-samples/aws-lambda-layer-kubectl/issues/3) for more details.

![](images/cross-accounts-01.png)




## License Summary

This sample code is made available under the MIT-0 license. See the LICENSE file.
