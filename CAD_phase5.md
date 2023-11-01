**Project :**

personal blog on IBM cloud static web apps

**Phase 5:**

Project Documentation & Submission

**Name:**

Ram Prasath M

Rishaban R

Santhosh Kumar R

Vasanth B

Vignash M



Phase 5: Project Documentation & Submission  

In this part you will document your project and prepare it for submission.



Document the travel blog project and prepare it for submission.

Documentation

Outline the project's objective, design thinking process, and development phases.

Describe the website structure, content creation, and technical implementation details.

Include screenshots or images of the blog's user interface.

Submission

Share the GitHub repository link containing the project's code and files.

Provide instructions on how to deploy the blog using IBM Cloud Static Web Apps.

Write a detailed README file explaining how to navigate the website, update content, and any dependencies.

Creating a travel blog website using Hugo and deploying it on IBM Object Storage involves several steps. Here's a step-by-step guide to help you get started:

**1. Install Hugo:**

Before you can create your travel blog website, you need to install Hugo. Hugo is a static site generator that will help you build your website quickly and easily.

You can install Hugo by following the installation instructions on the [official Hugo website](https://gohugo.io/getting-started/installing/).

**2. Create a New Hugo Project:**

Once Hugo is installed, you can create a new Hugo project by running the following commands in your terminal:

hugo new site your-blog-name

cd your-blog-name

This will create a new Hugo project directory with the specified name.

![hugo_menu](https://github.com/Rishirishaban/Personal-Blog/assets/147408175/44c902f9-f336-4c8d-b61b-a2b08b2a28eb)


**3. Choose or Create a Hugo Theme:**

You can choose an existing Hugo theme for your travel blog or create a custom theme if you have design skills. You can find Hugo themes on the Hugo Themes website.

To add a theme to your project, you can either clone it into the themes directory of your project or use Git submodules.

![theme](https://github.com/Rishirishaban/Personal-Blog/assets/147408175/f1a86d40-d5b0-46f0-aff4-7aed66112c6d)


\# Cloning a theme (replace theme-url with the theme's Git repository URL)

git clone theme-url themes/theme-name

\# Or using Git submodules

git submodule add theme-url themes/theme-name

**4. Configure Your Hugo Site:**

Hugo sites are configured using a configuration file called **config.toml** (or **.yaml** or **.json** if you prefer those formats). You can create or edit this file to customize your site's settings, including the site title, description, and other options.

**5. Create Content:**

You can create blog posts, pages, and other content using Hugo's built-in content management commands. For example, to create a new blog post:

bashCopy code

hugo new posts/my-first-post.md 

This will create a new Markdown file in the **content/posts** directory. You can add your content to these Markdown files.

**6. Customize Your Content:**

Edit the Markdown files to add your travel blog content, including text, images, and other media. You can use Hugo's Markdown formatting options to structure your content.

**7. Test Your Website Locally:**

To see how your website looks locally, run the Hugo development server:

bashCopy code

hugo server -D 

This will start a local development server, and you can access your website by opening a web browser and navigating to [**http://localhost:1313**](http://localhost:1313).

![dark](https://github.com/Rishirishaban/Personal-Blog/assets/147408175/022a174d-052a-46ad-a58f-345e5b0e5f4c)


**8. Build Your Website:**

When you're satisfied with your website's appearance, build it using the following command:

bashCopy code

hugo 

This will generate the static HTML files for your website in the **public** directory.

**9. Deploy Your Website to IBM Object Storage:**

To deploy your website to IBM Object Storage, follow these steps:

- Sign in to your IBM Cloud account and create an Object Storage instance if you haven't already.
- Obtain your Object Storage credentials, including your endpoint URL, access key, and secret key.
- Use a tool like **rclone** to sync the contents of your **public** directory with your Object Storage. Install **rclone** and configure it with your Object Storage credentials:

bashCopy code

rclone config 

Follow the prompts to configure **rclone** with your Object Storage details.

- Sync your Hugo-generated site to IBM Object Storage:

bashCopy code

rclone sync public/ your-object-storage-remote: 

Replace **your-object-storage-remote** with the remote name you configured in **rclone**.

**10. Configure Your Object Storage for Website Hosting:**

In the IBM Cloud Object Storage dashboard, configure your bucket for static website hosting. Set the index document (usually **index.html**) and error document (usually **404.html**) if needed.

**11. Make Your Website Public:**

Ensure that your Object Storage bucket is publicly accessible. Adjust the permissions accordingly to allow public access to the objects.

**12. Access Your Travel Blog Website:**

Once you've completed these steps, your travel blog website should be live and accessible using the public URL provided by IBM Object Storage.

Remember to regularly update your website by creating and publishing new blog posts and content using Hugo, and then syncing the changes to your Object Storage bucket using **rclone**.






