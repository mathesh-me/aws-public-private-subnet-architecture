# Secure VPC Architecture with Public and Private Subnets for Production Environment
## Overview :
This project's overview is depicted in the diagram below. The setup revolves around a Virtual Private Cloud (VPC) featuring both public and private subnets, thoughtfully distributed across two Availability Zones to ensure reliability.

Within each public subnet, there's a NAT gateway to facilitate outbound internet connectivity and a load balancer node for effective traffic distribution.

On the other hand, the project's servers reside in the private subnets. Their deployment and termination are automated through an Auto Scaling group, allowing them to dynamically adapt to workload changes. These servers play a pivotal role in receiving traffic from the load balancer and can access the internet through the NAT gateway when necessary


![image](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/9d656294-2011-4467-a620-63954d923710)

## Steps :
### Step 1 :
#### Create the VPC :
1. Open the Amazon VPC console by visiting https://console.aws.amazon.com/vpc/.
2. On the dashboard, click on "Create VPC."
3. Under "Resources to create," select "VPC and more."
4. Configure the VPC:<br>
   a. Provide a name for the VPC in the "Name tag auto-generation" field.<br>
   b. For the IPv4 CIDR block, leave it as default suggestion.<br>
5. Configure the subnets:<br>
   a. Set the "Number of Availability Zones" to 2 for increased resiliency across multiple Availability Zones.<br>
   b. Specify the "Number of public subnets" as 2.<br>
   c. Specify the "Number of private subnets" as 2.<br>
   d. For NAT gateways, choose "1 per AZ" to enhance resiliency.<br>
   g. For VPC endpoints, you can choose "None" .<br>
   h. Regarding DNS options, clear the checkbox for "Enable DNS hostnames."<br>

Once you've configured all the settings, click "Create VPC."

![p1](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/d80b1370-dd76-4043-b4f0-2c757e3c21c7)

![p2](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/722b69ac-f980-421b-8cb5-c3a5365e0a26)


![p3](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/32cb40b4-622a-4d13-b208-b0ab60c5cf2f)


![p4](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/35732232-120e-4fec-811f-03ad7c2a8438)
6. Now you can see you are successfully Created VPC .




### Step 2:
#### Creating the Auto Scaling Group :


![p5](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/a2e7f738-c9e5-4ab7-bfc9-abff65f3e235)


![p6](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/4312da54-b049-484e-ad2d-05e16b0f7163)


![p7](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/31663c3b-acd8-40de-b701-a470d6e6caaa)


![p8](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/6d0b515a-dbd5-41fd-8565-cad4039a9e8a)


![p8](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/d2d13f41-d10b-498a-8756-02e159bc6bd5)


![p9](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/34d0786d-e05c-48ff-a478-4cc8a407419b)
1. Now you have to choose the Key-pair you created.

![p9](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/89903e99-5673-493e-9e19-d92311fb4715)


![p11](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/c2c3f452-ef92-4ac0-9fc6-c12c55b3f5c7)


![p12](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/6ff77ba7-af88-41b7-8c8c-abcec09c2af8)


![p13](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/f1f3b337-6023-4d98-82f9-0b44727e2f76)
2. Scroll Down and then Click "Next".

![p14](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/2a17a34d-ef23-4607-b0b8-28dbfbcbf890)
3. Scroll Down and then Click "Next".

![p15](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/e195037c-ec37-4470-b503-cbb7abc0b14d)
4. Scroll Down and then Click "Next".

![p16](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/b15e60bf-9e9c-4741-ba93-16e724ecf1a5)
5. Scroll Down and then Click "Skip to Review".

![p17](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/c2e018ae-ffca-43e6-83e1-3fa812dcd93c)
6. Now your are Successfully Created Auto Scaling Group.<br>
7. Open the AWS Management Console.<br>
8. Navigate to the EC2 console by clicking on "Services" in the top-left corner, then selecting "EC2" under the "Compute" section.<br>
9. In the EC2 dashboard, you'll find the "Instances" link on the left-hand navigation pane. Click on "Instances."<br>
10. Here, you should see the list of EC2 instances associated with your account. Look for the instances created by your Auto Scaling Group.<br>
Since you mentioned that the Auto Scaling Group launched instances in different AZs, you can check the "Availability Zone" column to verify that these instances are indeed distributed across multiple AZs.

### Step 3 :
#### Creating the Bastion Host :

1. Launch Instance as Specified below .


![p18](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/c3c2bb90-6886-48f5-8d37-3168646203cf)


![p19](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/a902949d-6845-4d3c-b297-99542135eee0)


![p20](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/22d69a9d-2ce2-4334-94b4-4a4f5d12655a)


![p21`](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/750dea04-8fdc-40bd-baf4-efccdfb9dd5b)


![p22](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/5accdbf9-e13e-4cac-b2a7-c95d6f06104d)

### Step 4: 
#### SSH into Private Instance

1. SSH into the Bastion Host Instance:
   To SSH into the private instances, we first need to connect to our Bastion host instance. From there, we'll be able to SSH into the private instance.
2. Ensure the PEM File is Present on the Bastion Host:
   Additionally, make sure that the PEM file is present on the Bastion host. Without it, you won't be able to SSH into the private instance from the Bastion host.
3. Open a Terminal:
   Open a terminal window on your local machine.
4. Execute the Following Commands:
   a. If your PEM file is named something like `<aws demo.pem>`, you must remove spaces in the filename. Please rename the file to something like `<aws_demo.pem>`.
   b. Copy the PEM file to the Bastion host using the `scp` command. Replace `<pem file location>` with the local and remote file paths, and `<bastion host public IP>` with the Bastion host's public IP address. 
   Example:
      ```
      scp -i /Users/mathesh/Downloads/aws_demo.pem /Users/mathesh/Downloads/aws_demo.pem ubuntu@34.229.240.123:/home/ubuntu
      ```
   c. The above command will copy the PEM file from your computer to the Bastion host. Once the file is successfully copied, move on to the next step.
   d. SSH into the Bastion host using the following command:
      ```
      ssh -i aws_demo.pem ubuntu@34.229.240.123
      ```
    e. After SSHing into the Bastion host, use the `ls` command to check if the `aws_demo.pem` file is present. If it's not there, double-check your previous commands.
    f. Now, you can SSH into the private instance using the following command, replacing `<private IP>` with the private instance's IP address:
      ```
      ssh -i aws_demo.pem ubuntu@<private IP>
      ```
    g. We will deploy our application on one of the private instances to test the load balancer.
    h. After successfully SSHing into the private instance, create an HTML file using the Vim text editor:
      ```
      vim demo.html
      ```
    i. This will open the Vim editor. Copy and paste any HTML content you like into the editor.
    j. For example:
      ```html
      <!DOCTYPE html>
      <html>
      <head>
      <title>Page Title</title>
      </head>
      <body>

      <h1>This is an AWS Demo Production</h1>
      </body>
      </html>
      ```
     k. After pasting the content, save the file by pressing 'Esc' to exit insert mode and then entering `:w` to save.
     l. Finally, start a Python HTTP server on port 8000 to deploy your application on the private instance:
      ```
      python3 -m http.server 8000
      ```
Now, your application is deployed on the private instance on port 8000.
### Note :
We intentionally deployed the application on only one instance to check if the Load Balancer will distribute 50% of the traffic to one instance (which will receive a response) and 50% to another instance (which will not receive a response).

### Step 4 :
#### Creating the Load Balancer :

1. Access the EC2 Terminal.
2. Follow the steps outlined below.

![lb1](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/6e204024-11f4-4553-b583-8dc0b53a15ea)


![lb2](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/ae244b71-c4ba-4160-9bf9-0ea82d7e7e5f)


![lb3](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/3093dd4e-1acb-4ee5-9fe0-c0794f7336fd)


![lb4](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/84e79b0c-d25c-4471-aac5-d05a33d74801)


![lb5](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/58ce870b-9d5f-4343-bcf0-afe3edbcda27)


![lb6](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/bc12e1a3-4404-4427-b6e2-04183afd19fc)


![lb7](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/eebf3ea6-674e-43db-bac7-ca9c2f7dd951)


![lb8](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/b06c1553-2e2c-442a-bf14-88ff5b8d453b)


![lb9](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/db972f48-00d1-4d74-9cce-192ab6117e26)


![lb10](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/6444932a-0662-4953-abd9-c3de0a7d80a8)


![lb11](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/d6195b28-2e3f-4ead-9424-0976cc5600f8)


![lb12](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/12044558-3761-4f74-8e06-d4d32ae15cf2)


![lb13](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/04964ffc-e3c1-4197-b8e9-571e5e724d26)


![lb14](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/b753cdbf-2d5c-4667-9c4e-05dac0515b72)


![lb15](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/dc6e7431-0d6e-4138-a431-6ac29cccfdf7)


![lb16](https://github.com/itz-mathesh/aws-public-private-subnet-architecture/assets/144098846/f41fab30-1c22-41ad-bc92-24b06da4eb94)


Now We Successfully deployed Application securely in Private instance , We can access it through Internet using Load Balancer Securely .
