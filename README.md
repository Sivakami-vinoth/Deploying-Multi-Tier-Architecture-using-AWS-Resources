# Deploying-Multi-Tier-Architecture-using-AWS-Resources
Deploying Multi Tier Architecture using AWS Resources 

A firm wants to launch their new application. To reduce cost it has been decided that the entire application will be hosted on AWS. It’s a photo and video storage application. This application will store movies and videos, and customers can also upload photos and their custom made videos using this application.  

To buy videos, movies and wallpapers stored in the application customers have to pay some amount using their credit card. Customer will have to provide their home address and some other personal information as well. 

 Following are some of the requirements:  

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
Deploying multi tier archtecture using AWS Resources

<img width="473" alt="image" src="https://github.com/Sivakami-vinoth/Deploying-Multi-Tier-Architecture-using-AWS-Resources/assets/125202974/00f0f756-3c18-467e-b2ca-1bc112e6097b">

