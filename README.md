<!-- PROJECT LOGO -->
<br />
    <div align="center">
    <u><h2 align="center">DEPLOY STATIC WEBSITE ON AWS </h2></u>
    </div>
<br>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <!-- <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul> -->
    </li>
    <li><a href="#built-with">Built With</a></li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#steps">Steps</a></li>
      </ul>
    </li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>
<br>




<!-- ABOUT THE PROJECT -->
## About The Project

![Website](/img/for_readme/1.%20static_website.png)

In this project, a static website was deployed to AWS using S3, CloudFront, and IAM.
The files included are: 
1. index.html - The Index document for the website.
2. /img - The background image file for the website.
3. /vendor - Bootssrap CSS framework, Font, and JavaScript libraries needed for the website to function.
4. /css - CSS files for the website.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Built With

* [![AWS][AWS_LOGO]][AWS_URL]
* [![HTML][HTML_LOGO]][HTML_URL]
* [![CSS][CSS_LOGO]][CSS_URL]
* [![JQuery][JQuery.com]][JQuery-url]
* [![Bootstrap][BOOTSTRAP_LOGO]][BOOTSTRAP_URL]
* [![FontAwesome][FONTAWESOME_LOGO]][FONTAWESOME_URL]


<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- GETTING STARTED -->
## Getting Started

Here are the steps needed to successfully finish this project. 

### Prerequisites

1. You need to have an AWS account.

### Steps

1. ***Creating S3 Bucket.***
    * In AWS Management Console, search for S3 service. 
    * Create a new S3 bucket.
    * In the Bucket settings for <b>*Block Public Access section*</b>, uncheck the "Block all public access". It will enable the public access to the bucket objects via the S3 object URL.![Bucket_access](/img/for_readme/2.%20Bucket_Access.png)
    > **Note** - We are allowing the public access to the bucket contents because we are going to host a static website in this bucket. <b>*Hosting requires the content should be publicly readable.*</b> 
    * Click **Next** to create the bucket.
2. ***Creating S3 Bucket.***
    * Clone this Github Repository.
    * Open the S3 bucket.
    * Click on **Upload** button and upload all the files including:
        * index.html 
        * css folder
        * vendors folder
        * img folder
3. ***Secure Bucket via IAM***
    * Click on <b> Permissions </b> Tab 
    * Enter the following in the <b>*Bucket Policy* </b> section.
    ```
        {
        "Version":"2012-10-17",
        "Statement":[
                {
                    "Sid":"AddPerm",
                    "Effect":"Allow",
                    "Principal": "*",
                    "Action":["s3:GetObject"],
                    "Resource":["arn:aws:s3:::bucket_name/*"]
                }
            ]
        }
    ```
4. ***Configuring S3 bucket***
    * Go to the **Properties** Tab and go to the **Static Website Hosting** section.
    * Click on <b>Edit</b> button and enable <b>Static Website Hosting</b>
    * Set the default home page (index.html) and error page for the website.![Static_Website_Hosting](/img/for_readme/3.%20Static_Website_Hosting.png)
    * You should see the website endpoint under the Properties section now. ![Website_endpoint](img/for_readme/4.%20Website_Endpoint.png)

5. ***Distribute Website via CloudFront***
    * Search for <b>CloudFront Service</b> in the AWS console.
    * Create a CloudFront Distribution.
    * Use the following details to create a distribution:<br>

    Field | Value |
    ---|---|
    Origin > Domain Name | Don't select the bucket from the dropdown list. Paste the Static website hosting endpoint of the form|
    Origin > Enable Origin Shield | No
    Default cache behavior | Use default settings
    Cache key and origin requests | Use default settings
 
    ![CF_Setting1](/img/for_readme/5.%20CloudFront_Setting_1.png)
    ![CF_Setting2](/img/for_readme/6.%20CloudFront_Setting_2.png)

    * Leave the defaults for the rest of the options, and click "Create Distribution". It may take up to 10 minutes for the CloudFront Distribution to get created.

    * Once the status of your distribution changes from "In Progress" to "Deployed", copy the endpoint URL for your CloudFront distribution found in the "Domain Name" column.![CF_Link](/img/for_readme/7.%20CF_Link.png)


6. ***Accessing the Website***
    * The website can be accessed using the following links :
        * <b>Cloudfront Link - [dpl3a8z9pqhdf.cloudfront.net](https://dpl3a8z9pqhdf.cloudfront.net)</b>
        * <b>Bucket Website Endpoint - [shubhamkandwal-static-website.s3.amazonaws.com](https://shubhamkandwal-static-website.s3.amazonaws.com)</b>
        * <b>S3 Object endpoint URL - [shubhamkandwal-static-website.s3.amazonaws.com/index.html ](https://shubhamkandwal-static-website.s3.amazonaws.com/index.html)</b>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Name: Shubham Kandwal  
Email: shubham.0297@yahoo.in
Project Link: [Deploying_Static_Website_On_AWS](https://github.com/shubham0297/Deploying_Static_Website_On_AWS#prerequisites)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[AWS_LOGO]: https://img.shields.io/badge/AWS-FF9900?style=plastic&logo=amazonaws&logoColor=black
[AWS_URL]: https://aws.amazon.com/
[HTML_LOGO]: https://img.shields.io/badge/HTML-20232A?style=plastic&logo=HTML5&logoColor=WHITE
[HTML_URL]: https://html.com/
[FONTAWESOME_LOGO]: https://img.shields.io/badge/Font_Awesome-35495E?style=plastic&logo=fontawesome&logoColor=4FC08D
[FONTAWESOME_URL]: https://fontawesome.com/
[CSS_LOGO]: https://img.shields.io/badge/CSS-DD0031?style=plastic&logo=css3&logoColor=white
[CSS_URL]: https://www.w3.org/Style/CSS/Overview.en.html
[BOOTSTRAP_LOGO]: https://img.shields.io/badge/Bootstrap-563D7C?style=plastic&logo=bootstrap&logoColor=white
[BOOTSTRAP_URL]: https://getbootstrap.com
[JQuery.com]: https://img.shields.io/badge/jQuery-0769AD?style=plastic&logo=jquery&logoColor=white
[JQuery-url]: https://jquery.com 