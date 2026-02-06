# Hosting Static Website and Implementing CI/CD

## Step 1: Create an Amazon S3 Bucket

The first step in our infrastructure setup is to create an S3 (Simple Storage Service) bucket, which will serve as the storage repository for our website files, including `index.html` and `error.html`.

### Step 1.1: Select an Appropriate Region
Choose a region that is geographically close to your target users. This proximity significantly reduces data latency, resulting in faster content delivery and improved user experience.

### Step 1.2: Name the S3 Bucket
Assign a unique and descriptive name to your bucket. AWS requires bucket names to be globally unique across all AWS accounts, so ensure the name is distinctive and follows AWS naming conventions (lowercase letters, numbers, and hyphens only).

### Step 1.3: Configure Security Settings - Block Public Access
Enable the "Block Public Access" settings for your bucket. This is a critical security measure that prevents unauthorized public access to your files. By enabling this setting, you ensure that your website assets can only be accessed through properly configured CloudFront distributions or IAM-authenticated requests, protecting your content from unauthorized exposure.

### Step 1.4: Retain Default Settings
Leave the remaining configuration options at their default values unless you have specific requirements. These defaults provide a secure and optimized baseline configuration for most static website hosting scenarios.

### Step 1.5: Create the Bucket
Click the "Create bucket" button to finalize the bucket creation process. Your S3 bucket is now ready to store your website files.

## Step 2: Upload Your Website Files to the S3 Bucket

After successfully creating your S3 bucket, the next crucial step is to upload your website files (`index.html` and `error.html`) to the bucket. This will make your content available for serving through CloudFront or direct S3 access.

### Step 2.1: Navigate to Your S3 Bucket
Open the AWS S3 console and locate the bucket you just created. Click on it to open the bucket's main view where you can manage its contents.

### Step 2.2: Initiate the Upload Process
Click the "Upload" button located in the bucket's interface. This action will open a file selection dialog window, allowing you to choose the files you want to upload from your local machine.

### Step 2.3: Select Your Website Files
In the popup dialog that appears, select your `index.html` and `error.html` files. You can select multiple files by holding the Ctrl key (Cmd on Mac) while clicking each file, or by using the file browser to navigate and select them all at once.

### Step 2.4: Configure Upload Settings (Optional)
Review the upload settings if needed. AWS provides options for setting storage class, encryption, and metadata. For a static website, the default settings are typically sufficient. You can proceed without modifications unless you have specific requirements.

### Step 2.5: Complete the Upload
Click the "Upload" button in the dialog to begin uploading your files. AWS will show a progress indicator as your files are transferred to the S3 bucket. Once complete, your website files are now stored in S3 and accessible for web hosting.

### Step 2.6: Verify File Upload
After the upload completes, verify that your files appear in the bucket's contents list. You should see both `index.html` and `error.html` listed with their respective sizes and upload timestamps. This confirms that your files have been successfully stored in S3.

## Step 3: Configure CloudFront Distribution for Content Delivery

CloudFront is AWS's Content Delivery Network (CDN) service that caches and distributes your website content from edge locations worldwide. This dramatically improves performance by serving your content from servers closest to your users, reducing latency and improving loading times globally.

### Step 3.1: Create a New CloudFront Distribution
Navigate to the CloudFront console in AWS. Click the "Create Distribution" button to begin setting up a new distribution. AWS will present you with options to choose between web or RTMP distributions. Select "Web" as we are hosting a static website.

### Step 3.2: Configure the Origin
In the Origin section, assign a descriptive name for your distribution. Then, in the "Origin Domain" field, select **Amazon S3** from the dropdown. Click "Browse S3 bucket" to open the bucket selection dialog, and choose the S3 bucket you created in Step 1. This tells CloudFront where to fetch your website content.

### Step 3.3: Select Default Settings
Review the default CloudFront settings, which include caching behaviors, compression, and security headers. For a static website, AWS's default configurations are typically well-optimized and secure. You can proceed with these defaults unless you have specific performance or security requirements.

### Step 3.4: Create the Distribution
After configuring your origin and reviewing the settings, click the "Create Distribution" button. AWS will create your CloudFront distribution and begin deploying it across its global edge network. This process typically takes 5-15 minutes to complete.

### Step 3.5: Configure Default Root Object
Once the distribution is created and shows a status of "Deployed," click on your newly created distribution to access its settings. Navigate to the "General" tab and locate the "Default Root Object" field. Enter `index.html` in this field. This setting ensures that when users visit your distribution domain without specifying a file, CloudFront automatically serves your `index.html` file.

### Step 3.6: Save Configuration Changes
Click the "Save Changes" button to apply your default root object configuration. AWS will save these settings, and your distribution will be ready to serve your website.

### Step 3.7: Access Your Live Website
Copy the **Distribution Domain Name** (it will look like `d123abc45xyz.cloudfront.net`). Paste this URL into your web browser's address bar and press Enter. Your static website is now live and being served globally through CloudFront! You should see your beautifully designed homepage with all the features we created. 