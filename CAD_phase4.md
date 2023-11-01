**Project :**

personal blog on IBM cloud static web apps

**Phase 4:**

Development part 2

**Name:**

Ram Prasath M

Rishaban R

Santhosh Kumar R

Vasanth B

Vignash M



**Phase 4:Development part 2**

In this part you will continue building your project. 

- Continue building the travel blog by setting up the IBM Cloud Static Web App and deploying the website. 
- Sign up for an IBM Cloud account.  
- Create a new Static Web App and follow the prompts to set up the repository, build pipeline, and deployment options. 
- Choose a static site generator like Jekyll or Hugo to make it easy to update and manage the blog content. This would involve converting your HTML content into template files that can be easily updated. 

Sign up for an IBM Cloud account

if you want to host a website using IBM Cloud Object Storage, you can follow these steps:

1. **Create an IBM Cloud Object Storage Instance**: If you don't already have an IBM Cloud Object Storage instance, you need to create one. Here's how to do it:
   1. Log in to your IBM Cloud account.
   1. Go to the IBM Cloud Dashboard.
   1. Click "Create Resource" and select "Storage" > "Object Storage."
   1. Follow the prompts to create your Object Storage instance.

![Screenshot (63)](https://github.com/Vasanthv7/Personal-Blog/assets/126228661/d7742c3e-ef17-4290-9dda-81779021fd9b)


1. **Set Up Your Object Storage Bucket**: Once your Object Storage instance is created, you'll need to set up a bucket to store your website's files. Buckets are containers for your objects (files). Here's how to create a bucket:
   1. In the Object Storage dashboard, click "Create bucket."
   1. Give your bucket a unique name and configure the bucket settings.
   1. You can choose the bucket location and set up public access if you want your website to be publicly accessible.

![Screenshot (64)](https://github.com/Vasanthv7/Personal-Blog/assets/126228661/6d6313b9-370f-42b7-9ff4-d0313358315d)


1. **Upload Your Website Content**: Upload your website's HTML, CSS, JavaScript, and other assets to your Object Storage bucket. You can do this using the IBM Cloud Object Storage web interface or by using the IBM Cloud CLI. For example, if you're using the IBM Cloud CLI, you can use the **ibmcloud cos** command to upload files.
1. **Set Up a Custom Domain**: If you want to use a custom domain for your website, configure your domain's DNS settings to point to your Object Storage bucket. This typically involves creating a CNAME record or an alias record that points to the Object Storage bucket's endpoint URL.
1. **Configure Object Storage Static Website Hosting**: IBM Cloud Object Storage offers static website hosting features. To enable website hosting, you'll need to configure your Object Storage bucket:
   1. In the Object Storage dashboard, select your bucket.
   1. Go to the "Configuration" tab.
   1. Enable static website hosting.
   1. Specify the index document (e.g., "index.html") and error document (if needed).
1. **Access Your Website**: Once your Object Storage bucket is configured for static website hosting and your DNS settings are updated, your website should be accessible via your custom domain or the Object Storage bucket's endpoint URL.
1. **Security and SSL Certificates**: Consider implementing security measures such as setting up SSL certificates to ensure secure connections to your website hosted in Object Storage.
1. **Backup and Versioning**: Implement backup and versioning strategies to protect your website's data.
**Optimization and Performance**: Continuously optimize your website for performance and cost efficiency. IBM Cloud Object Storage provides features for optimizing your content delivery.

By following these steps, you can easily host a static website in IBM Cloud Object Storage. This is a cost-effective solution for hosting simple websites and provides high availability and scalability.

10\.Content management

Choose a static site generator like Jekyll or Hugo to make it easy to update and manage the blog content. This would involve converting your HTML content into template files that can be easily updated

In this blog we choose hugo as the static site generator

By which we can able to handle the content after deploy the website on IBM cloud storage









Conclusion:

In this part you will continue building your project. Continue building the travel blog by setting up the IBM Cloud Static Web App and deploying the website. 



