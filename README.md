<h1>Multi-VPC Account Architecture Lab</h1>


<h2>Description</h2>
In this project I created three VPCs with private subnets. Each VPC has subnets in two Availability Zones (AZs) within the Region. I deployed one EC2 instance per VPC to demonstrate that, by default, VPCs provide network isolation. Created a VPC Peering Connection, which is a networking connection between two VPCs that enables you to route traffic between them using private IPv4 addresses or IPv6 addresses. Ultimately establishing VPC point-to-point peering links between each VPC that was created. Next I took a more scalable approach and utilized the AWS Transit Gateway (TGW). I removed the point-to-point peering connections between the VPCs that we established earlier, and setup a Transit Gateway (TGW) to interconnect all three of the VPCs.
<br />


<h2>Applications and Services Used</h2>

- <b>VPC</b> 
- <b>EC2</b>
- <b>IAM</b> 

<h2>Environments Used </h2>

- <b>AWS Linux</b> 

<h2>Lab Walk-through:</h2> 

<p align="center">
Lab 1.1 Create Three VPCs: <br/>
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/515dc8c0-3160-4bd5-a4d5-f518da622f35" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

<p align="center">
Step 1: Navigate to VPC Dashboard Services <br/>
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/9d184a70-4c94-4a9f-86cb-0cb2b93902a5" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

<p align="center">
Step 2: Navigate to your VPCs and click "Create VPCs" <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/e5dd7f65-04f1-4e4f-95be-e483a83d5bfc" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

<p align="center">
Step 3: Choose settings and click Creat VPC <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/1f5aeb62-cff3-4e24-b79e-3792c70fac54" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

<p align="center">
Step 4: Repeat the first three steps to create VPC B and VPC C.  <br/>  

<p align="center">
After completing these steps, you should have three new VPCs and default listed under "Your VPCs:"   <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/f0da0175-678e-4688-bd52-4dc01ff47e62" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

<p align="center">
1.2 Create Subnets: Ceate two subnets for each VPC, one per availability zone (AZ). <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/61b6a580-3b22-45e8-a8d4-e42c9e51fc35" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

<p align="center">
Step 1: Navigate to Subnets pannel <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/5113df4d-cf74-4b3f-9139-333253c5826a" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

  <p align="center">
Step 2: Click on create subnet and choose VPC <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/c4096bf0-d89d-4ad8-84c9-7cc9ea028855" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center">
Step 3: Create subnets with names that reflect VPC and AZ placement such as VPC A - AZ1, select AZ and provide subnet CIDR  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/22cc18f6-09a9-4dc3-b286-a3ab96c74344" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center">
Step 4: Click on Add new subnet to add one more subnet into AZ2 with name like VPC A - AZ2 <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/1c0fb269-900a-49b8-8d86-c6716cc4f1c2" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

<p align="center">
Step 5: Repeat the steps above to create subnets for VPC B and VPC C <br/>

 <p align="center">
After you finish these steps, six new subnets should be available <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/31170a09-324e-402f-bfac-3c8710c9d02c" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center">
1.3 Deploy Internet Gateways <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/756d6bfc-33ce-4624-8342-cd0bf59556c3" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center">
Step 1: Navigate to Internet Gateways (IGW) and click create internet gateway <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/1685f6e5-446c-4f57-9020-9af481bc2366" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center">
Step 2: Give it a name such as VPC A - IGW. Click "Create internet gateway" <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/31268fea-b7f9-42ce-88b4-afcfc8e116ce" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center">
Step 3: Select newly created IGW and click on "Attach to VPC" <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/10fb13d6-a81a-4751-a7d6-df8ca6ff30c1" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center">
Step 4: Attach this IGW to VPC A <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/36dd0f40-b191-494b-b6c1-77618af1b7b4" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

<p align="center">
Step 5: Repeat these steps to create and attach IGWs in VPC B and VPC C <br/> 

 <p align="center"> 
After you finish these steps you should have an IGW for the default VPC and three newly created IGWs <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/2c69c011-b2f2-4d98-96b0-3c87f0bf4e74" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center">
1.4 Updating Routing Tables <br/> 

 <p align="center">
Step 1: In VPC dashboard, navigate to Route Tables <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/7f91bdf1-b7e4-4394-bbbf-45826ca9eca5" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center">
Step 2: Assign names to the Route Tables by identifying what VPC a given Route Table belongs to <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/d2c69df6-3989-4ef1-a01d-e0c729227066" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center">
Step 3: Navigate to VPC A Route Table and click on Routes tab. Click on Edit Routes <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/cf6ebb04-023c-4f22-9511-c8e92ef1fa41" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center">
Step 4: Modify Route Table to add the default route 0.0.0.0/0 pointing to the Internet Gateway <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/4e64e62f-323c-443f-9290-30246ed9de4a" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center">
Step 5: Repeat these steps for VPC B and VPC C route tables <br/> 

 <p align="center">
2.1: Create EC2 Instances in VPCs <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/77e23ddc-cf55-42f5-920d-3334df393852" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center">
Step 1: Navigate to Roles in the IAM dashboard and Create an IAM Role for EC2 Instances <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/bbfb126e-7df5-44b0-973b-37c3e2980649" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center">
Step 2: Under common use cases click on EC2 then click next <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/0ef79fbc-43e7-4fdb-ab11-f379cead9965" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center">
Step 3: Under filter policies, search for AmazonSSMManagedInstanceCore and select it  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/d45ad999-0437-4d51-93a4-f5934322d7cd" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center">
Step 4: Under filter policies, search for AmazonS3FullAccess and select it  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/4bac6740-8cfe-4142-b6c5-484cc962d11a" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center">
Step 5: Cick on next, Enter the Role name Ec2SsmIamRole, Verify that the AmazonSSMManagedInstanceCore and AmazonS3FullAccess policies are listed, click create role at the bottom right   <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/58cdd188-d448-4d0b-be5b-ce2160e5cfd7" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center">
2.2 Launch EC2 Instances  <br/>

 <p align="center">
Step 1: Navigate to EC2 dashboard and click launch instances   <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/328fa424-ae62-4d13-9fe9-7ab48886c2b5" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center">
Step 2: Name the instance EC2 VPC A - AZ!, from quick start select Amazon Linux, Choose Amazon Linux 2 AMI (HVM), SSD Volume Type 64-bit (x86), keep the selected Free tier eligible t2.micro instance type   <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/43cd93cf-737e-4a82-b75f-e35f2c6f8a40" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center">
Step 3: Scroll down to "Key pair(login)", choose Proceed without a key pair (Not recommended). note: you will use SSM session Manager to access the shell running on the EC2, so a key pair is not needed in the lab   <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/a1b529a1-3a36-4e60-a600-3a20b6011aa6" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center">
Step 4: Scroll down to "Network settings" and click Edit, Choose VPC A for the VPC and Subnet VPC A - AZ1 from the VPC and Subnets dropdowns, For Auto-assign Public IP choose Enabled from dropdown   <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/6260c92d-a04d-4f74-b629-38ec4879034d" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center">
Step 5: Scroll down in "Network settings" section under "Firewall(security groups)" and choose Create security group, Name the Security Group VPC A EC2 Security Group, Modify the Inbound Rules on the Security Group to permit ICMP traffic from any address in the internal network - 10.0.0.0/8.  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/124d822e-a8c6-43e3-8c2d-23a589f2c283" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center">
Step 6: Scroll down and expand "Advanced details" section, From the "IAM instance profile", choose Ec2SsmIamRole from the dropdown   <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/b3374488-1895-446a-adb1-d6fa4a2f2452" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center">
Step 7: Scroll down and click on Launch instance   <br/>

 <p align="center">
Step 8: Launch two more EC2 instances and assign them names accordingly, One in "VPC B" AZ1 named EC2 VPC B - AZ1, The other one in "VPC C" AZ1 named EC2 VPC C - AZ1, After few minutes you should have 3 EC2 instances in the "running" state     <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/bf2040ac-6bab-4461-8d31-64e68231ca60" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center">
3.1 Test inter-VPC communication   <br/>

 <p align="center"> 
Step 1: Proceed to EC2 Console, Select EC2 VPC A - AZ1 and click Connect   <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/50225df5-114a-4805-b58b-72770404fc28" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
Step 2: Click Connect to connect using Session Manager   <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/d1f856c0-6c88-4901-a73c-3b69ccc1923b" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center"> 
Step 3: Terminal session should open in a new browser tab, From the EC2 instance in VPC A try pinging the private IP addresses of EC2 instances in VPC B and VPC C   <br/> 

 <p align="center"> 
Lab 1.2 VPC Peering   <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/807ef3ff-6214-47de-b581-41704000f0d6" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
Step 1: Navigate to VPC pannel, click on peering connections, next, click on create peering connection  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/4fb1a7d5-6844-4de6-bb10-6885ff1039fb" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
Step 2: Specify the Peering connection name tag, Under "Select a local VPC to peer with", select "VPC A" ID as VPC (Requester)    <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/b09383f3-41f7-43c0-ac7e-88a227dca78b" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
Step 3: Under "Select another VPC to peer with", for Account, select "My Account" and for Region, select region for this workshop us-east-1, For VPC (Accepter), select "VPC B" ID, then click on "create peering connection"     <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/439a3353-de38-40a7-a32d-ae70fd6cffe7" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center"> 
Step 4: Newly created peering connection will be in "Pending Acceptance" state, Select the connection, navigate under "Actions" and click "Accept Request"    <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/0d97ef3a-094f-4448-bfaf-e49aa6436549" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
Step 5: Repeat these steps to create "VPC A" to "VPC C" peering connection, You should now have two active peering connections as shown below    <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/e77121d1-ab4f-4fad-8694-69b3b9bd2698" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
2.1 Update Route Table for VPC A    <br/> 

 <p align="center"> 
Step 1: Select VPC A Route Table, click on Routes tab, click Edit Routes   <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/16d34119-440b-4f6b-b960-45efdf3feef3" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
Step 2: Add route entries for "VPC B" and "VPC C" using their CIDR ranges (10.1.0.0/16 and 10.2.0.0/16 respectively)  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/34214ae2-3d3a-457a-a636-eb52b2427089" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
2.2 Route Tables for VPC B   <br/>

 <p align="center"> 
Step 1: Add route entries for "VPC A" using CIDR range (10.0.0.0/16)  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/72987611-5262-4000-9521-081d54d0d488" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
2.3 Update Route Table for VPC C  <br/>

<p align="center"> 
Step 1: Add route entries for "VPC A" using CIDR range (10.0.0.0/16)  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/1d59c2d1-43f5-490d-a628-b974a5da1846" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
2.4 Check EC2 Connectivity in VPC A  <br/>

 <p align="center"> 
Step 1: Proceed to the EC2 Console, Connect to the EC2 instance in "VPC A" using Connect button in the EC2 console Session Manager (refer to Lab1.1 )  <br/>

 <p align="center"> 
Step 2: Ping EC2 instances in "VPC B" and "VPC C". Use private Addresses of the Instances, If peering and routing are configured correctly, you should be able to ping both instances. <br/>

 <p align="center"> 
Step 3: Connect to EC2 instance in VPC B  <br/>

 <p align="center"> 
Lab 1.3 Transit Gateway (TGW)  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/e483f534-b782-4c8e-b6b3-98e5a9fc7c83" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
Step 1: Delete VPC Peering Connections, Navigate to VPC Dashboard - Peering Connections, Select "VPC A <-> VPC C" and delete peering connection  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/4d1f489f-c87b-4a39-8c04-1b40d43c5146" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
Step 2: Select the checkbox to delete related route table entries to avoid traffic a blackhole filtering scenario  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/b7623636-b140-4bdc-9586-929f3693835a" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
Step 3: Repeat deletion of VPC peering for "VPC A <-> VPC B" connection  <br/> 

 <p align="center"> 
2.1 Create Transit Gateway  <br/> 

 <p align="center"> 
Step 1: Navigate to Transit Gateways Console and click on Create Transit Gateway  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/2b0db161-b9ab-4e6c-be54-b7053872fa9f" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
Step 2: Create Transit Gateway using default settings. Please note that the Amazon side ASN or Multicast support cannot be changed after the transit gateway is created  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/4bf35b66-6a3a-4eec-9a9a-3896d7f19698" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
2.2 Create Transit Gateway Attachments Subnets  <br/> 

 <p align="center"> 
Step 1: Navigate to VPC Subnets, Create two subnets for VPC A, 1 per AZ, VPC A - AZ1 TGW (10.0.2.0/28) and VPC A - AZ2 TGW (10.0.3.0/28)  <br/> 

 <p align="center"> 
Step 2: Create 2 subnets for VPC B 1 per AZ, VPC B - AZ1 TGW (10.1.2.0/28) and VPC B - AZ2 TGW (10.1.3.0/28)  <br/> 

 <p align="center"> 
Step 3: Create 2 subnets for VPC C 1 per AZ, VPC C - AZ1 TGW (10.2.2.0/28) and VPC C - AZ2 TGW (10.2.3.0/28)  <br/> 

 <p align="center"> 
2.3 Create Transit Gateway Attachments  <br/> 

 <p align="center"> 
Step 1: Under "VPC Dashboard" - "Transit Gateways", navigate to Transit Gateway Attachments  and click on "Create Transit Gateway Attachment."  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/8db741b9-a505-4183-b7fc-580fdc87f3f5" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
Step 2: Create the VPC attachment for both availability zones in "VPC A" by choosing subnets we created on previous step for TGW  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/8d7ba039-f7dd-4188-a5f9-8cad8eb237c5" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
Step 3: Repeat these steps to create attachments for "VPC B" and "VPC C", Upon completion, you should see three Transit Gateway attachments  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/3cdd7f7b-225a-4f2a-bea4-60caec32faff" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
3.1 Check Transit Gateway Route Table <br/>

 <p align="center"> 
Step 1: Navigate to Transit Gateways, then click Transit Gateway Route Tables  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/b1bc63bd-e7d8-4f8a-8d68-703f2b454343" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
Step 2: You should see one Route Table, click on it, Click on "Routes" tab, Your routing table should be populated with "VPC A", "VPC B", "VPC C" routes   <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/61eb0cee-307e-4290-b585-51ebccf40929" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

 <p align="center"> 
4.1 Update Route Tables of VPCs <br/>

 <p align="center"> 
Step 1: Navigate to route tables, select VPC A Route Table, Click on "Routes" tab and click "Edit routes"  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/89afae90-0db6-4300-85c9-0bc11183d0d0" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center"> 
Step 2: Add route entries for "VPC B" and "VPC C", To simplify the configuration, create a single 10.0.0.0/8 route pointing to the Transit Gateway  <br/> 
<img src="https://github.com/brycehallcloud/Multi-VPC-Account-Architecture/assets/144934324/249a796f-e8f3-4c4c-9643-5a3632e41037" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 <p align="center"> 
Step 3: Repeat these steps for VPC B's and VPC C's Routing Tables <br/>

 <p align="center"> 
5.1 Check EC2 Connectivity via TGW <br/>

 <p align="center"> 
Step 1: Proceed to EC2 Console, Connect to EC2 instance in "VPC A" (via "Session Manager"), Ping private IPs of instances deployed in "VPC B" and "VPC C", Connect to EC2 instance in "VPC B". Ping private IPs of instances deployed in "VPC A" and "VPC C"  <br/> 

 <p align="center"> 
Lab 1.4 Clean Up <br/>

 <p align="center"> 
Step 1: Terminate EC2 Instances <br/>

 <p align="center"> 
Step 2: Delete Transit Gateway and Aattachments <br/>

 <p align="center"> 
Step 3: Delete the three VPC's <br/>

 <p align="center"> 
Step 4: Delete the IAM Role <br/>







































 


 













 

 







   
 






 

  
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
