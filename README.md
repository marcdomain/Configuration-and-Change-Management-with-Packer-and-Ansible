# Configuration-and-Change-Management-with-Packer-and-Ansible

Automating the deployment of infrastructure to AWS by using Packer to build machine images, and Ansible as a provisioner to the packer script.

## Installation

- If you’re using Homebrew on a macOS, install Packer using \
```$ brew install packer```
- If you're using Chocolatey on a windows machine, use \
```$ choco install packer```

## Setup

- Using the variables in ```.env.sample``` file as guide, create a ```.env``` file and supply the information specific to your AWS account.

## Build Machine Image

- Run the bash script in the root directory to source the ```.env``` file and run packer ```template.json``` file.

## Provisioning EC2 instance with the AMI you created

- From your AWS [console](https://console.aws.amazon.com/ec2/v2/home) (ensure you're in the same region the image was created), click on Services at the top menu and select EC2.
- Navigate to the left hand menu, under IMAGES, click on AMI.
- From the list of images presented to you, identify the image you just created and select it. Click on launch.
- Choose an instance type, and then choose Next: Configure Instance Details. t2.micro will be selected by default since the image was built with this instance_type.
- Click Next: Add Storage
- Click Next: Add Tags
- Add tags (optional) and proceed to create security group.
- In the port range column, input the port your app is running on.
- Set the source IP to 0.0.0.0/0 to allow traffic from all sources.
- Click "Review and Launch" to review your settings.
- Then click launch.
- Select an existing key pair or create a new key pair, select the acknowledge agreement box, and then choose Launch Instances.
- Navigate to EC2 dashboard and click on instances to view the instance you just created.
- Click on the instance from the list presented.
- Copy the IP address and past it in your browser URL to access the application.

## Medium Post

- Read up the article on medium [Using Packer & Ansible for Configuration and Change Management](https://medium.com/@marcus.devops/using-packer-ansible-for-configuration-and-change-management-8ae752fe1b2e)