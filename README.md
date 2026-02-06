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