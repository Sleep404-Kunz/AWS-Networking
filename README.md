# AWS-Networking

**Objectives:**
- Explain components of VPC
- Deploy VPC with public subnets
- Deploy Amazon EC2 instance into a VPC.

**VPC:** is a virtual network that is deidcated to your AWS account, logically isolated from other virtual networks in the Cloud and used to lauch resources.

## Task A: VPC configuration

1. Choose the VPC services and go to **_Your VPCs_** tab.
2. Choose to create VPC.
3. This page is the VPC configuration page.

   <img src = "https://github.com/user-attachments/assets/f9e408bb-afbd-4acd-a0da-50d7ff6b5fb8" width = "400">
4. Select **_VPC and more_** in **_Reosources to create_**. 
5. Then I made the following configuration settings:

   <img src = "https://github.com/user-attachments/assets/12758e52-c7de-44fc-ac93-6223879990e6" width = "310">

   This configurations gives me a preview as shown below on the right hand side:

   <img src = "https://github.com/user-attachments/assets/4fa95492-5083-491e-af90-063329c33165" width = "600">

6. Next I assign proper subnet CIDR blocks so that there are no overlaps:

   <img src = "https://github.com/user-attachments/assets/f111c015-0ec7-4607-811c-c23d728f51c1" width = "300">

7. The final VPC preview is a shown below:

    <img src = "https://github.com/user-attachments/assets/8a0cf686-6dc1-4950-9967-f2ba70d173c2" width = "600">

8. After reviewng the VPC configurations, I choose create VPC. The VPC is set up with a default route table, internet gateway and security groups which will be configured later on.

   <img src = "https://github.com/user-attachments/assets/f0c9a454-bf2d-485f-9c5e-ac994e7786a9" width = "210">

   As it is right now, the VPC's default security group does not allow traffic from outside the VPC. I add a new security group to my custom Lab VPC.
   
   <img src = "https://github.com/user-attachments/assets/2f17604e-9853-45ea-b85f-57ad1f3400cd" width = "550">

## Task B: Security Group addition

1. Select **_Security groups_** and choose **_create security group_**
2. I provide the following configurations to the security group to allow HTTP access to outside sources over the internet.
   **<ins>It is important to select the correct VPC when applying the security group</ins>**
   
   <img src= "https://github.com/user-attachments/assets/d3bc3d96-46d9-4195-a775-499d7a255308" width = "400">

3. In the **_Inbound rules_** section choose **_Add rule_**
   For **_type_** choose  **_HTTP_**
   From  **_Source_** dropdown choose  **_Anywhere-IPV4_**
   For  **_Description_** enter  **_Allow web access_**
   Then choose creat security group.      

   <img src = "https://github.com/user-attachments/assets/d495f933-0ea6-4190-8f4b-7ad7b9211530" widht = "400">

The VPC is configured and the necessary security group to connect to external IP through the internet has been added to the VPC as well. Next I create an EC2 instance in the VPC.

## Task C: Configuring an EC2 instance to launch in a custom VPC

1. In the **_Launch instancce_** section choose the **_Launch instance_** button.
2. Make the following configurations in the **_Launch an instance_** page. Keep the **_Amazon Linux_** default image in the **_AMI_** section.

   <img src = "https://github.com/user-attachments/assets/346f1a00-31e0-44fd-8f39-341389bfb085" width = "350">

3. Select the **_Amazon Linux 2 AMI_** in the AMI list
   
   <img src = "https://github.com/user-attachments/assets/46a94d6f-cb3f-446f-9404-9b9705cfded6" width = "400" >

4. For the **_Key pair (login)_** I proceeded without it.
5. In the **_Network Settings_** choose **_edit_** and the following configurations were made. Once again it is important to choose the correct VPC for the EC2 to be launched into:

   <img src = "https://github.com/user-attachments/assets/99eb7b84-a3a0-4607-9f91-daf11f4ef541" width ="400">

   Select the **_public1_** subnet and enable **_Auto-assign public IP_**. Choose the **_WebServer2-SG_** security group added earlier after choosing **_Select existing security group_**

6. Choose **_Launch instance_** and the instance is created in the VPC.

## Conclusion

With this we have created a custom VPC and deployed an EC2 instance within it which is allowed to be accessed by external public IPs using the HTTP service.
