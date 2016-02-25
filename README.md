# packer-aws-example
An example for creating AWS AMIs with packer. For more details on packer, visit http://packer.io

This example only focus on packer, using the AWS builder to create AWS AMI

# Install Packer
To install packer, please visit: https://www.packer.io/docs/installation.html

# General Packer Info
To validate a packer template file, run

	packer validate example.son

This will validate your example.json file to be valid and ready to build.

# Create an AMI (EBS)
Go to aws-ebs-ec2 and validate the packer file (just to be sure):

	packer validate example.son

The result should be something like this:

	Template validated successfully.

Alright, we are ready to build our AMI:

	packer build -var ‘aws_access_key=XXX’ -var ‘aws_secret_key=YYY’ example.json

This will build your AMI with packer. Be aware that this may take some time as packer spins up an instance using the defined source_ami property.

If your build succeeds, you will get a console output like this:

	Build 'amazon-ebs' finished.
	==> Builds finished. The artifacts of successful builds are:  

	--> amazon-ebs: AMIs were created:
	eu-central-1: ami-a5acad0a6

You can now use your newly created AMI to spin up EC2 instances!