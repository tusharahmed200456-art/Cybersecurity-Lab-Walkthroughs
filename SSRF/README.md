# PortSwigger Web Security Academy – Basic SSRF Against Another Back-End System

**Lab:** Basic SSRF against another back-end system  
**Category:** Server-Side Request Forgery (SSRF)  
**Difficulty:** Apprentice  
**Status:** Solved ✅  
**Tools Used:** Burp Suite, Burp Intruder  
**Platform:** PortSwigger Web Security Academy

---

## 1. Overview

In this lab, I learned how to identify and exploit a Server-Side Request Forgery (SSRF) vulnerability to access an internal back-end system.

The application contains a stock check functionality that makes server-side requests to another internal system.

By manipulating the stock check request, I was able to discover an internal service and access its administrative functionality.

## 2. My Methodology

### Step 1: Open the Lab

First, I opened the PortSwigger Web Security Academy lab and explored the application.

I identified the product stock check functionality.

### Step 2: Capture the Request in Burp Suite

I intercepted the stock check request using Burp Suite Proxy.

The request contained a parameter that controlled the internal stock check URL.

### Step 3: Send the Request to Intruder

I sent the captured stock check request to Burp Suite Intruder.

I used Intruder to test different internal port numbers and observe the server responses.

### Step 4: Identify the Internal Service

By changing the port number and comparing the responses, I identified an accessible internal service.

This helped me understand that the application could communicate with internal back-end systems.

### Step 5: Access the Admin Panel

After identifying the internal service, I modified the request to access the internal admin functionality.

I successfully accessed the administrative interface through the vulnerable stock check feature.

### Step 6: Delete the Carlos User

From the internal admin functionality, I accessed the user management section and deleted the Carlos account.

The lab was successfully solved.

## 3. Vulnerability Explained

**Server-Side Request Forgery (SSRF)** occurs when an attacker can manipulate a server into making requests to unintended internal or external resources.

In this lab, the vulnerable stock check functionality allowed me to manipulate the destination of a server-side request and reach an internal administrative service.

## 4. Tools Used

- Burp Suite Proxy
- Burp Suite Intruder
- PortSwigger Web Security Academy

## 5. Key Learning Outcomes

Through this lab, I learned:

- What Server-Side Request Forgery (SSRF) is.
- How to intercept HTTP requests using Burp Suite.
- How to use Burp Intruder to test internal port numbers.
- How internal back-end services can become exposed.
- How SSRF can potentially lead to unauthorized administrative access.

## 6. Security Recommendations

To prevent SSRF vulnerabilities:

- Validate and restrict user-controlled URLs.
- Block requests to internal and private IP addresses.
- Use strict allowlists for permitted destinations.
- Restrict unnecessary internal service access.
- Implement network segmentation and firewall rules.

## 7. Conclusion

This was a practical learning experience with Server-Side Request Forgery (SSRF).

I successfully identified an SSRF vulnerability, tested internal ports using Burp Suite Intruder, accessed an internal administrative service, and completed the lab by deleting the Carlos user.

**Status: Successfully Solved ✅**


---

**Disclaimer:** This write-up documents an authorized educational lab performed in the PortSwigger Web Security Academy environment.
