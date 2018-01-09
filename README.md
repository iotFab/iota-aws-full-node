
# AWS IOTA Full node

## Description 
This cloudformation template deploys a full IOTA node with automatic neighbors setup. 
Deploying this template will incur cost.
You can [estimate the stack cost within the AWS Management console](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-paying.html)

This template sets up an EC2 instance.
When the deployment finishes, Nelson and IOTA Full node will be running.

Versions:

IRI - 1.4.1.6

Nelson - 0.3.16

You can specify new version through template's parameters

## Disclaimer
- Working @ AWS, any opinions are my own.
- Deploying this cloudformation template will incur a cost. 
- This Cloudformation template automatically **accepts Oracle-Java-isntaller-8 license**

## Requirements

- [Have an AWS Account](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-sign-up-for-aws.html)
- [Setup AWS CLI](https://aws.amazon.com/cli/?nc1=h_ls)
- Enough privileges to deploy the cloudformation template.
- [Review Oracle Java 8 license before proceeding](http://www.oracle.com/technetwork/java/javase/terms/license/index.html)

## Let's GO ! 

Note: To connect to your full node instance you need an AWS EC2 KeyPair.
[How to create an AWS EC2 Keypair](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html)
This will allow you to use iota-pm to monitor your full node.


### Setting up IOTA full node from here
Thanks to [SemkoDev](https://semkodev.com/) for hosting the cloudformation template on S3. 


[![alt text](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=IotaAwsFullNode&templateURL=https://s3-eu-west-1.amazonaws.com/nelson-iri/cloudformation.yml)

### Setting up IOTA full node with AWS CLI 

#### Step 1: Fetch the template
`git clone https://github.com/iotFab/iota-aws-full-node.git`

#### Step 2: Deploy the template 
`aws cloudformation create-stack --stack-name iotaws-full-node --template-body file://iota-aws-full-node/cloudformation.yml --parameters ParameterKey=KeyName,ParameterValue=<Your Keypair name>`

More information:
[AWS Cloudformation CLI commands](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-using-cli.html)

### Setting up IOTA full node with AWS management console 

#### Step 1: Fetch the template
`git clone https://github.com/iotFab/iota-aws-full-node.git`

#### Step 2: Deploy the template 
Follow the step by step  http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-using-console.html

### Monitor your IOTA node

If you have deployed the stack with a KeyPair, you should see the command in your stack outputs. 
This command enables port forwarding between your EC2 instance to your computer. 

This will looks like : 

`ssh -i "<your keypair>" -p 22 -L <your iota-pm-api-port>:localhost:<your iota-pm-api-port> ubuntu@<your ec2 ip>`

You can access in your browser `http://127.0.0.1:<your iota-pm-api-port>` until you shutdown the ssh connection.

To access this output section once the deployment is completed, you have 2 options : 
##### From AWS CLI:
`aws cloudformation describe-stack-events --stack-name iotaws-full-node`

##### From AWS Management Console: 
[Access AWS Console management Stack output section](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-view-stack-data-resources.html)

### Connect wallet with your IOTA node

To connect a wallet to your node refer to CustomNodeURL variable in your cloudformation output section.

Note: Your node need to be synced for this operation

You can also setup an Elastic IP to have a fixed public URL. 

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
- Integration with Cloudwatch logs or Cloudwatch custom metrics

## License
Licensed under the [MIT license](https://opensource.org/licenses/mit-license.php).
Copyright (c) 2017 iotFab

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
