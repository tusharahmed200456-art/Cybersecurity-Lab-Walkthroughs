# Remote Code Execution via Web Shell Upload

**Platform:** PortSwigger Web Security Academy

**Category:** File Upload

**Difficulty:** Practitioner

**Status:** Solved

**Tools Used:** Burp Suite, Chrome

## 1. Lab Overview

In this lab, I learned about File Upload Vulnerability.

The website allowed users to upload a profile picture.

I found that the website also allowed PHP files to be uploaded and run on the server.

This led to Remote Code Execution (RCE).

## 2. Steps I Followed

### Step 1: Login

First, I opened the lab and logged in with the given account.

- Username: `wiener`
- Password: `peter`

### Step 2: Upload an Image

I went to the My Account page.

I uploaded a normal JPG image as my profile picture.

### Step 3: Use Burp Suite

I opened Burp Suite and checked the upload request.

I found this request:

`POST /my-account/avatar`

I also found the file name and upload type.

### Step 4: Create a PHP File

I created a file named `exploit.php`.

I added this code:

```php
<?php
echo file_get_contents('/home/carlos/secret');
?>
```

### Step 5: Upload the PHP File

I uploaded `exploit.php` as my profile picture.

The server accepted the file.

I got this message:

`The file avatars/exploit.php has been uploaded.`

### Step 6: Open the Uploaded File

I opened the uploaded PHP file in my browser.

URL:

`/files/avatars/exploit.php`

The PHP code ran on the server.

### Step 7: Get the Secret

The browser showed the secret value.

I successfully completed the lab.

## 3. What I Learned

- How file upload works.
- How to use Burp Suite Proxy.
- How to check HTTP requests.
- How to upload a PHP file.
- How a web shell works.
- How file upload can lead to RCE.

## 4. Security Impact

This type of vulnerability can cause:

- Remote Code Execution.
- Data theft.
- Server compromise.
- Unauthorized access.

## 5. How to Prevent It

- Allow only safe file types.
- Check uploaded file content.
- Do not trust file extensions.
- Store uploaded files safely.
- Do not allow PHP execution in upload folders.

## 6. Conclusion

I successfully completed this lab.

I learned how an unsafe file upload can allow an attacker to run PHP code on a web server.

This was a good practical experience with Burp Suite and File Upload Vulnerability.

**Practice Platform:** PortSwigger Web Security Academy
