# Deploying-Multi-Tier-Architecture-using-AWS-Resources
## Problem Statement: 

A firm wants to launch their new application. To reduce cost it has been decided that the entire application will be hosted on AWS. It’s a photo and video storage application. This application will store movies and videos, and customers can also upload photos and their custom made videos using this application. 
To buy videos, movies and wallpapers stored in the application customers have to pay some amount using their credit card. Customer will have to provide their home address and some other personal information as well.

 **Following are some of the requirements:**
 
1. The most important requirement is that the application should be very much secure and none of the servers (front-end UI, back-end application, database) should be available over Internet. 
2. Application should handle sudden spike in customer activity without any problem. 
3. Customer information should be kept secure as much as possible. 
4. It has been decided that 2 types of NoSQL databases would be used to store metadata information about videos and photos. 3 Relational databases would be used for transactional purposes. 
5. Performance is vital for the success of the product. Make sure that users get low latent responses wherever possible. 
6. Photos and videos should be stored securely at rest.
7. Access to AWS resources should be authorized as per business need, e.g. application developers should not have access to database servers. DBAs should not have any access to application servers.
 8. Whenever customer uploads a photo/video he or she should get an email notification. 
9. Photos/videos older than 2 years should be archived to save cost. 
10. Application should be highly available. It should not go down in the event of any data center failure. Disaster Recovery has to be set up to mitigate regional failures as well. 
11. Transactions should be as secure as possible. 
12. All the SysOps out there configure and use AWS CLI to provision all services.
As AWS administrators and architects you will have to make sure everything in the requirement is taken care of. Make sure to have provision to apply patches on the servers periodically. Also, make sure to have future provisioning for technology refresh. Following is the high-level architecture diagram suggested by the senior solutions architect. Set up the entire AWS environment based on this. Factor in DR setup as well.
 
<img width="602" height="351" alt="Image" src="https://github.com/user-attachments/assets/46eec17f-d7d9-462f-b3c7-b3d0a2f771e1" />

**Lab Environment:** 

Set up AWS environment with the following components. Remember, you DO NOT have to create the application, just set up the architecture using AWS services and make sure you understand which services to use where. This is a typical media services domain application, but with much less complexities.
1. AWS Account 
2. VPC components 
3. EC2 and EBS 
4. Load Balancer, Auto Scaling groups and scaling policies 
5. S3 
6. DynamoDB 
7. RDS DB Instance 
8. Route 53 
9. SNS 
10. Elastic Beanstalk (Optional, if you choose PaaS for your front end and back end applications. Better to use Elastic Beanstalk for one of the tiers) 
11. IAM Users, Roles and Groups 
12. Glacier 
13. ElastiCache


**Hint:**

Architecture has already been given; you have to first map the architecture with AWS services. Check the requirements multiple times; you have to implement all the provided requirements in AWS. Some services have to be pulled in and placed in the architecture to fulfill all the requirements. Lab environment already mentions all the required services, try to use those in the architecture and create the application. 
You DO NOT have to write any code or create the application as such. It will need a lot of coding and development knowledge. The purpose of this project is to make sure that you know how to implement AWS services to create an end-toend application. Draw the diagram first using AWS services and then provision the services as needed. You might incur some AWS charges, but those will be minimal. 
MAKE SURE TO TERMINATE ALL THE SERVICES ONCE YOU ARE DONE WITH THE EXERCISE.
**********************************************************************************************************************************

## ****Step:1 Create an VPC****

•	Login to AWS Console

•	Goto-> Services-> VPC

•	Click on Create VPC

<img width="602" height="141" alt="Image" src="https://github.com/user-attachments/assets/e37b02b9-d155-42b5-a9fa-611d7b4ca6b6" />

<img width="602" height="306" alt="Image" src="https://github.com/user-attachments/assets/0cad2e1d-45d6-4b99-b5c2-e4710dbd6722" />

<img width="602" height="428" alt="Image" src="https://github.com/user-attachments/assets/624fd155-e3ee-4e9d-b540-3d965cc3aff6" />

<img width="602" height="191" alt="Image" src="https://github.com/user-attachments/assets/cb7a3e30-0725-4286-8758-0ceb89a09691" />

## ****Step:2 Create Subnets****

<img width="602" height="125" alt="Image" src="https://github.com/user-attachments/assets/736a959a-6edb-4e23-b1bc-cbd040400cf9" />

<img width="602" height="258" alt="Image" src="https://github.com/user-attachments/assets/08857563-ce45-45de-a292-86982554c701" />

<img width="602" height="471" alt="Image" src="https://github.com/user-attachments/assets/9f7c4e1c-6e65-43f8-bbf6-56cb13dc435c" />

<img width="602" height="423" alt="Image" src="https://github.com/user-attachments/assets/44ac83f9-a249-468e-a26e-e7a1a81ade25" />

<img width="602" height="458" alt="Image" src="https://github.com/user-attachments/assets/1074e426-681e-41e8-be47-f3e694f16777" />

<img width="602" height="170" alt="image" src="https://github.com/user-attachments/assets/c7cea6bd-9b9c-4bcf-aaeb-20542d89d38c" />

## ****Step:3 Create Internet Gateway and attach to the VPC****

<img width="602" height="115" alt="image" src="https://github.com/user-attachments/assets/d4ce41a6-eb7f-4ee5-a50a-e58cae0db77e" />

<img width="602" height="464" alt="image" src="https://github.com/user-attachments/assets/815d5973-5726-4610-8f28-e4e4d2a4b055" />

<img width="602" height="233" alt="image" src="https://github.com/user-attachments/assets/cdc17a99-f939-44b2-99be-7990efd3e392" />

<img width="602" height="162" alt="image" src="https://github.com/user-attachments/assets/28b5e494-572c-4c4d-9ebe-7f942dab7e7e" />

<img width="602" height="291" alt="image" src="https://github.com/user-attachments/assets/50fcae90-62ce-430a-9ca0-610afc07786f" />

## ****Step:3 Create NAT Gateway****

<img width="602" height="170" alt="image" src="https://github.com/user-attachments/assets/bfa6c15f-90d6-40bb-9517-3ab4af0f62e4" />

<img width="602" height="461" alt="image" src="https://github.com/user-attachments/assets/350c55ad-ba2e-42d4-b26b-1e9f6360a77f" />

<img width="602" height="230" alt="image" src="https://github.com/user-attachments/assets/b58b2390-bb9a-4882-b441-0d15a8688191" />

<img width="602" height="202" alt="image" src="https://github.com/user-attachments/assets/7842bec3-05f3-4382-99d8-e63c23c4de3d" />

## ****Step: 4 Create Route tables for public subnets and Edit Route to add Internet gateway****

<img width="602" height="103" alt="image" src="https://github.com/user-attachments/assets/4d028815-906b-4e00-8435-667cabf00b3a" />

<img width="602" height="140" alt="image" src="https://github.com/user-attachments/assets/7b93fb6f-1cc0-4cd4-8c9d-5bc30203ea27" />

<img width="602" height="299" alt="image" src="https://github.com/user-attachments/assets/9d5d634d-7bb3-4db9-8106-29f0da5ba842" />

<img width="602" height="211" alt="image" src="https://github.com/user-attachments/assets/8ba61f09-2f53-4415-997b-7c29ca7e9175" />

<img width="602" height="257" alt="image" src="https://github.com/user-attachments/assets/b529c390-ee53-4500-ac2d-8d22efaa585a" />

<img width="602" height="158" alt="image" src="https://github.com/user-attachments/assets/80f5d9d6-a38a-4f19-9bc0-d11d5a0d8655" />

<img width="602" height="294" alt="image" src="https://github.com/user-attachments/assets/34416c65-e263-48d2-9ee5-434f549cd5f6" />

## ****Step:5 Create Route table for private subnet and Edit route to add NAT gateway****

<img width="602" height="105" alt="image" src="https://github.com/user-attachments/assets/10ebc141-a36b-45ca-95e4-ec82f39e6849" />

<img width="602" height="475" alt="image" src="https://github.com/user-attachments/assets/6c2cc411-b078-4f01-af3f-25ba01da5443" />

<img width="602" height="258" alt="image" src="https://github.com/user-attachments/assets/ba5f81a4-1d7d-4382-a492-d1ee892e6d6f" />

<img width="602" height="158" alt="image" src="https://github.com/user-attachments/assets/59c4e6bc-62aa-440f-8b02-5da7098618a5" />

<img width="602" height="307" alt="image" src="https://github.com/user-attachments/assets/d1bac290-42c7-40cc-a8bd-321455e755be" />

<img width="602" height="299" alt="image" src="https://github.com/user-attachments/assets/3a34d0ce-5f60-49b4-90db-fd8342f31bb5" />

<img width="602" height="228" alt="image" src="https://github.com/user-attachments/assets/0c5c6409-4edd-4536-a6fe-54502396a500" />

<img width="602" height="232" alt="image" src="https://github.com/user-attachments/assets/db88fd66-ee91-42e7-afd8-6842c0746bd4" />

## ****Step:6 Create 2 EC2 Instances one in public subnet and other one in private subnet****

<img width="602" height="198" alt="image" src="https://github.com/user-attachments/assets/30f1c26f-66a8-4f3d-b5bc-5df26009a77a" />

<img width="525" height="501" alt="image" src="https://github.com/user-attachments/assets/a0d37d4e-8152-4fb7-a4b8-6a0ef2969728" />

<img width="526" height="415" alt="image" src="https://github.com/user-attachments/assets/2fc9f6a7-2714-4dbd-b900-c7417ed2e507" />

<img width="602" height="318" alt="image" src="https://github.com/user-attachments/assets/f1b69e64-0427-4fe9-8f76-e1e180c4c2b5" />

<img width="602" height="63" alt="image" src="https://github.com/user-attachments/assets/27f4b7a2-6e2b-4fa9-b1ce-66da250bb4d4" />

## ****Similarly create one more instance in private subnet****

<img width="523" height="396" alt="image" src="https://github.com/user-attachments/assets/4d465cdc-5b1f-456a-8ef8-9503e29345a4" />

<img width="602" height="264" alt="image" src="https://github.com/user-attachments/assets/1b7a7285-1dc5-47e4-8906-f15e3bc60b2a" />

<img width="602" height="68" alt="image" src="https://github.com/user-attachments/assets/940df3e1-be02-4fdf-a318-94fb70e781a1" />

## ****Step:7 Create S3 bucket and uplaod files in it****

<img width="602" height="110" alt="image" src="https://github.com/user-attachments/assets/a138623a-1e3b-4386-9b2a-d4bcdae3bf4e" />

<img width="602" height="416" alt="image" src="https://github.com/user-attachments/assets/4a90036d-6ca7-4da0-9583-9b68967605f0" />

<img width="586" height="491" alt="image" src="https://github.com/user-attachments/assets/3d47d283-c7d9-4e13-bd78-89a0eaaf3ca9" />

<img width="602" height="331" alt="image" src="https://github.com/user-attachments/assets/2d442d99-802b-4bc1-a540-3fe0a5d5cdd4" />

<img width="578" height="445" alt="image" src="https://github.com/user-attachments/assets/a72509b3-8d80-4836-9281-72df3082582e" />

<img width="602" height="166" alt="image" src="https://github.com/user-attachments/assets/3712b769-b026-4637-be67-d9618b443f76" />

<img width="602" height="211" alt="image" src="https://github.com/user-attachments/assets/2cd21174-5022-4712-8a65-e931dafe0a32" />

<img width="602" height="396" alt="image" src="https://github.com/user-attachments/assets/a65eca65-e017-49cf-b9d2-2cbc53f84397" />

<img width="602" height="370" alt="image" src="https://github.com/user-attachments/assets/abe3542d-ce89-42d6-bb9b-67255116b056" />

<img width="602" height="235" alt="image" src="https://github.com/user-attachments/assets/3963be69-30f9-419f-904c-8f61d96b6abf" />

<img width="602" height="257" alt="image" src="https://github.com/user-attachments/assets/c136a540-64ea-486a-83c1-5488f1e16d54" />

<img width="602" height="390" alt="image" src="https://github.com/user-attachments/assets/ab78829a-7f78-4bb6-9f8e-8b0edaf08cb3" />

<img width="602" height="131" alt="image" src="https://github.com/user-attachments/assets/35c1d63c-ae5e-4db6-9c05-bbd7791adad2" />

<img width="602" height="143" alt="image" src="https://github.com/user-attachments/assets/e367addc-4672-4c38-a8b6-5c4c85c6a8af" />

<img width="602" height="483" alt="image" src="https://github.com/user-attachments/assets/5fa9b873-f13a-4a3d-827a-cf51159dc3fc" />

<img width="602" height="116" alt="image" src="https://github.com/user-attachments/assets/0e2b9fb0-9277-4008-b8be-b2971940c382" />

<img width="602" height="172" alt="image" src="https://github.com/user-attachments/assets/829e8a0c-de13-402f-9843-5002b879b0c7" />

<img width="602" height="115" alt="image" src="https://github.com/user-attachments/assets/70014459-0285-4848-b024-e468a35efb34" />




















































