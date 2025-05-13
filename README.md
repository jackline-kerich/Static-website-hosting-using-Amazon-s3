Static-website-hosting-using-Amazon-s3
🌐 How to Host a Simple Static Website on AWS S3

Amazon S3 (Simple Storage Service) is ideal for hosting static websites because it serves files directly to users without requiring server-side processing. Static websites consist of fixed content like HTML, CSS, JavaScript, images, and other assets — all delivered exactly as stored. Unlike dynamic sites, S3 doesn’t support back-end logic but provides a cost-effective, scalable, and reliable storage solution for delivering static content such as personal websites, landing pages, or documentation.

---

🗂️ The S3 Bucket Architecture

This guide walks through creating and configuring an S3 bucket to host a static website, enabling public access, uploading web files, and testing the website functionality.

---

📋 Lab Steps

✅ Task 1: Sign in to AWS Management Console

1. Go to the AWS sign-in page.
2. Enter your **User Name** and **Password**, then click **Sign in**.
3. Set the default region to **US East (N. Virginia) - \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*`us-east-1`**.

---

✅ Task 2: Create an S3 Bucket

1. Navigate to **S3** via the **Services** menu.

2. Click **Create bucket**.

3. Use the following settings:

   * **Bucket type**: General purpose
   * **Bucket name: jackies-s3-bucket**
   * **Region**: `US East (N. Virginia) us-east-1`
   * **Object ownership**: ACLs disabled (recommended)
   * **Block Public Access**:

     * Uncheck **Block all public access**
     * Check **I acknowledge...**

4. Keep all other settings as default and click **Create bucket**.

---

✅ Task 3: Enable Static Website Hosting

1. Go to your new bucket and select the **Properties** tab.

2. Scroll to **Static website hosting** → click **Edit**.

3. Enable the following settings:

   * **Static website hosting**: Enable
   * **Hosting type**: Host a static website
   * **Index document**: `index.html`
   * **Error document**: `error.html`

4. Click **Save changes**.

---

✅ Upload Your Website Files

1. Upload the following HTML files to the root of your bucket:

   * `index.html`
   * `dashboard.html`
   * view`.html`
   * `error.html`

---

✅ Set Bucket Policy to Allow Public Access

1. Go to the **Permissions** tab of the bucket.
2. Click **Edit** next to **Bucket Policy**.
3. Copy the **ARN** displayed at the top (e.g., arn\:aws\:s3:::jackies-s3-bucket).
4. Paste the following policy (update the `Resource` with your actual bucket ARN):

```json
{
  "Id": "Policy1",
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1",
      "Action": [
        "s3:GetObject"
      ],
      "Effect": "Allow",
      "Resource": "arn:aws:s3:::jackies-s3-bucket/*",
      "Principal": "*"
    }
  ]
}
```
Click Save changes.

✅ Task 4: Test the Website
Copy the Static Website Endpoint from the bucket's Properties tab.

Paste it in your browser to load index.html.

✅ Task 5: Test the Error Page
Append a random string to the endpoint URL (e.g., /randompage) and press Enter.

The custom error.html page should load.


