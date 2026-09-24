# S3 Static Website Hosting Project 🌐

## Project Overview

In this project, I hosted a **static website using Amazon S3**.

### Technologies Used

* Amazon S3
* HTML
* AWS Management Console

---

## Architecture

```text
User
  ↓
S3 Bucket
  ↓
Static Website
```

---

## Steps

### 1. Create an S3 Bucket

* Open **Amazon S3**
* Click **Create bucket**
* Enter a globally unique bucket name
* Select the AWS Region
* Create the bucket

### 2. Upload Website Files

Upload the static website files into the bucket.

Example:

```text
index.html
error.html
style.css
images/
```

### 3. Enable Static Website Hosting

Go to:

```text
S3 Bucket
→ Properties
→ Static website hosting
→ Enable
```

Set:

```text
Index document: index.html
Error document: error.html
```

### 4. Configure Bucket Permissions

Configure the required bucket/object permissions so the website can be accessed publicly.

> For production workloads, avoid making an S3 bucket publicly accessible unless the architecture specifically requires it.

### 5. Access the Website

After enabling website hosting, S3 provides a **website endpoint**.

Example:

```text
http://bucket-name.s3-website-region.amazonaws.com
```

Open the endpoint in a browser to view the website.

---

## What I Learned

* Creating and configuring an S3 bucket
* Uploading objects to S3
* Static website hosting
* S3 bucket permissions
* Accessing a website through an S3 endpoint

---

## Result

✅ S3 Bucket Created
✅ Website Files Uploaded
✅ Static Website Hosting Enabled
✅ Website Successfully Accessed
