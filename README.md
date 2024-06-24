# Cloud Resume Challenge: How to deploy a static site to Amazon S3
![Cloud_resume_architectural_diagram](https://github.com/karungar/deploy-a-static-website-to-S3/assets/160833948/d413d9a5-8e89-4674-9f18-3417ea748c17)
 
**Introduction**

The project involves hosting a static website on Amazon Simple Storage Service (S3) bucket. 
CloudFront was used for distribution. SSL/TLS from AWS Certificate Manager is used for secure access to the Amazon S3 bucket.
The domain was purchased from (https://my.hostafrica.com/) Amazon Route 53 was used for creating the hosted zones.                                                                               

Step-by-step guidelines

# Prerequisites for the Cloud Resume Project

1. Sign up for an AWS account
2. Set up an IAM user with administrative access.
3. Acquring a domain name
4. Configure Route 53 hosted zones.

<!-- Configuring Amazon Route 53  -->
1. From the AWS Management Console search Route 53

1. 

<!-- Amazon Simple Storage Service configuration -->

1. Open the AWS Management console
2. In the services menu go to S3 and choose "Create Bucket"
   <img width="890" alt="Create Bucket" src="https://github.com/karungar/deploy-a-static-website-to-S3/assets/160833948/232c3bc5-3910-4938-aac7-a6a14ae34b95">
4. Select bucket type as "General Purpose" and Type the "Bucket Name" and the region.
    <img width="612" alt="Create a bucket" src="https://github.com/karungar/deploy-a-static-website-to-S3/assets/160833948/7ad327b3-e0de-46ee-803c-60ab7b899d10">
5. Do not uncheck the box in the option of "Block Public Access settings" because you will restrict access to CloudFront.
   <img width="462" alt="block public access" src="https://github.com/karungar/deploy-a-static-website-to-S3/assets/160833948/5c3c7f99-bccf-4b70-8ac4-1dd2e52cec86">
7. Keep everything default and click on "Create Bucket".
   


<!-- Creating a CloudFront Distribution -->
1. From the AWS Management Console services menu, select CloudFront under Network and Content Delivery.
2. Navigate to the left and select Distributions tab.
3. Now click on Create Distribution button.
   <img width="613" alt="CloudFront" src="https://github.com/karungar/deploy-a-static-website-to-S3/assets/160833948/c5313071-3ba1-4a52-91cc-007a61e20900">

5. Configure the distribution as follows:
    Origin Domain Name: Select the S3 Bucket you created.
    Enter a name for this origin(For Example CloudResumeChallenge)
6. Choose Origin Access Control(Recommended)
    Create OAC. In the description box write "This OAC restricts bucket access to CloudFront" 
7. For WAF select "Do not enable security protection"
8. Keep the rest of the settings as default, scroll down and click "Create Distribution"
    Wait for the CloudFront to be enabled and deployed. The Domain name that CloudFront 
    assigns to your distribution appears in the list of distributions.
9. A banner requiring the S3 bucket policy to be updated will pop up. Choose the Copy policy.
10. In the same banner choose the link "Go to the s3 bucket permissions to update policy". Paste the policy in the "Edit statement" field. Save the changes.
11. Return to the CloudFront console and review the details section for your new distribution. When the distribution is done deploying, the "Last modified" field changes from "Deploying" to a data and time. Record the domain name that CloudFront assigns to your distribution. 
Copy it on a browser tab and edit the URL by adding /index.html at the end. It should display the index.html file present in the bucket.

<!-- ACM Configuration to enable HTTPS-->
1. In this project we use SSL/TLS certificate from AWS Certificate MAnager. Choose AWS Certificate Manager in the AWS Management Console.
2. 

<!-- Aquiring a Domain Name --> 


<!-- Using Route53 for Domain Naming -->

<!-- Architectural Diagram   -->

1. The viewer requests the website at www.example.com.
2. If the requested object is cached, CloudFront returns the object from its cache to the viewer.
3. If the object is not in CloudFront’s cache, CloudFront requests the object from the origin (an S3 bucket).
4. S3 returns the object to CloudFront
5. CloudFront caches the object.
6. The object is returned to the viewer. Subsequent responses for the object are served from the CloudFront cache.

Project Challenges
1. Time constraints
2. Limited Knowledge of HTML and CSS. I used a resume template belonging to [Zablon](https://github.com/zablon-oigo)instead of creting one
    because time could not allow me to learn from scratch and finish the project on time. I am still learning the basics of HTML and CSS from some resources shared in my channel.
3. Limited knowledge of Git and GitHub actions. I asked my peers at Team Jade for assistance and also read 
    widely on the topics.

Key Takeaways
1. One of the key takeawyas from this challenge is that I should face my fears and use every opportunity to 
    learn something new. 
2.Main skills acquired are;
    -Drawing architectural diagrams using draw.io
    -Hosting a static website on Amazon Simple Storage Service
    -Configuring CloudFront as the website distribution
    -Configuring Amazon Route53 as the Domain Naming Service



Resources
https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html
https://docs.aws.amazon.com/acm/latest/userguide/acm-services.html
https://github.com/aws-samples/amazon-cloudfront-secure-static-site
https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html
https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-configuring-new-domain.html
https://repost.aws/knowledge-center/cloudfront-serve-static-website




