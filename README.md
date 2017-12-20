
# AWS IOTA Full node

## Description 
This cloudformation template deploy a full IOTA node with automatic neighboors setup. 
Deploying this template will incurs cost.
You can [estimate the stack cost within the AWS Management console](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-paying.html)



## Disclamer
- Working @ AWS, opinions are my own.
- Deploying this cloudformation template will implies a cost. 
- This Cloudformation template automatically **accept Oracle-Java-isntaller-8 license**

## Requirements

- [Have an AWS Account](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-sign-up-for-aws.html)
- [Setup AWS CLI](https://aws.amazon.com/cli/?nc1=h_ls)
- Enough privileges to deploy the cloudformation template.
- [Review Oracle Java 8 license before proceeding](http://www.oracle.com/technetwork/java/javase/terms/license/index.html)


## Description 

This template setup an EC2 instance. 
When the deployment finish Nelson and IOTA Full node is runing. 
version: 
Nelson - 0.2.2

IRI - 1.4.1.4

## Let's GO ! 

### Setting up IOTA full node from here
Thanks to [SemkoDev](https://semkodev.com/) for hosting the cloudformation template on S3. 

[![alt text](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=IotaAwsFullNode&templateURL=https://s3-eu-west-1.amazonaws.com/nelson-iri/cloudformation.yml)

### Setting up IOTA full node with AWS CLI 

#### Step 1: fetch the template
`git clone https://github.com/iotFab/iota-aws-full-node.git`

#### Step 2: deploy the template 
`aws cloudformation create-stack --stack-name iotaws-full-node --template-body file://iota-aws-full-node/cloudformation.yml --parameters ParameterKey=KeyName,ParameterValue=<Your Keypair name>`

More information:
[AWS Cloudformation CLI commands](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-using-cli.html)
[Create an AWS EC2 Keypair](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html)


### Setting up IOTA full node with AWS management console 

#### Step 1: fetch the template
`git clone https://github.com/iotFab/iota-aws-full-node.git`

#### Step 2: deploy the template 
Follow the step by step  http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-using-console.html

## Contributing
- Donations always welcome: 
`MXSEWAKADLTATVETLEMSOUYFIQNYBL9DKPCBKBQYZZPETZCTEJWYU9ZRY9EINDCTKGFFNEZSJYRXXQTECOT9DFRYMW`

- Feel free to propose features or fixes


Thank you to http://iota.partners/ for providing DB storage and clear step by step to setup full node.


## TODO
- Setup [billing alerts](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/monitoring-costs.html) for better cost tracking
- Setup [auto-scaling group](http://docs.aws.amazon.com/autoscaling/latest/userguide/AutoScalingGroup.html)
- Add more parameters from Nelson and IRI in the template
- Provide [Amazon Elastic Ip](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html) as an option 
- Extend the region supported by this template



## License
Licensed under the [MIT license](https://opensource.org/licenses/mit-license.php).
Copyright (c) 2017 iotFab

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
