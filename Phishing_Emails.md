# Exercise 2: Phishing Emails in Action
---
## 1. Objective
The purpose of this exercise was to apply social engineering theory to real-world scenarios. I analyzed a series of actual phishing emails to identify common red flags such as urgency, typosquatting, and malicious payloads.
---
---
## 2. Walkthrough & Analysis

### Task 1: Introduction
I reviewed the basic principles of phishing defense and set up the lab environment.
* **Status:** Completed.
---
### Task 2: "Cancel your PayPal order"
The email sample in this task will highlight the following techniques:

* **Spoofed email address**
* **URL shortening services**
* **HTML to impersonate a legitimate brand**

Here are some quick observations about this email sample:

1. This is an unusual email recipient address. This is not the email address associated with the Yahoo account. 
2. This mismatch should immediately stand out. The sender's details (service@paypal.com) don't match the sender's email address (gibberish@sultanbogor.com). 
3. The subject line hints that you made a purchase or a transaction of some sort. If you don't recall this account, then it will grab your attention. This social engineering tactic is to prompt you to interact with the email with haste. 

<img width="1005" height="155" alt="image" src="https://github.com/user-attachments/assets/d1465a89-d420-45d5-9f78-bdea4e7de3e7" />

Now let's look at the contents of the email body.

Email Body Text (Image 1):

<img width="640" height="685" alt="image" src="https://github.com/user-attachments/assets/43b7a9e0-8256-41b2-a51e-9fbf037ad3be" />

The second half of the same email body text (Image 2):

<img width="494" height="588" alt="image" src="https://github.com/user-attachments/assets/e5c97921-927f-4743-8612-6d387d8c07ff" />

The email body compliments the sender information and subject line. The email was designed as a legitimate email from PayPal. 

There aren't any attachments associated with this email. The only interactive element in this email is the Cancel the order button/link. 

Let's investigate that further by reviewing the raw HTML source for the email...

Email Hyperlinks:

<img width="783" height="185" alt="image" src="https://github.com/user-attachments/assets/3d856fba-b741-499c-ba46-0580ac5d1a97" />

The link uses URL shortening services. It is not a good idea to click on the link if you don't know where the link is taking you. 

Luckily, there are online tools that we can use to let us know the destination of a shortened URL. 

<img width="699" height="481" alt="image" src="https://github.com/user-attachments/assets/56a65945-0f91-47ca-a1dc-c126c803624b" />

Strange. This link redirects to google.com. 

**Note:** Tools to expand shortened URLs will be discussed in the Phishing Emails 3 room.  

**Answer the questions below**

1. What phrase does the gibberish sender email start with?
   * noreply
---
### Task 3: "Track your package"
This email sample will highlight the following techniques:

1. **Spoofed email address**
2. **Pixel tracking**
3. **Link manipulation**

Here are some quick observations about this email sample:

1. The email is tailored to appear that it's sent from a mail distribution center of some sort. 
2. The subject line adds to the pretense with a 'tracking number.' 
3. The link in the email body matches the subject line. 

<img width="1022" height="200" alt="image" src="https://github.com/user-attachments/assets/6f6a1502-f46d-4e31-b86d-07789321dab5" />

**Note:** In this email sample, Yahoo blocked the images from automatically loading. Any guesses as to why? 

Typically one can hover the cursor over a link to see where the link is pointing to, but in this sample, that technique won't work because Yahoo disabled links in the email.  We can look at the raw source code for the email and find out. 

Email Hyperlinks:

<img width="1014" height="376" alt="image" src="https://github.com/user-attachments/assets/8be2047e-9042-42fd-baa3-db80fab93ad0" />

Here we see an image file, and it's explicitly called Tracking.png. These trackers send information back to the spammer's server. 

There are many reasons for spammers to embed tracking pixels (very small images) into their spam emails. To read more about this concept, refer to this post on The Verge here. 

Now we can understand why Yahoo automatically blocked the images in this email. Many email providers do the same. 

Back to the hyperlink, the link is pointing to a shady-looking domain. The only distribution center this domain can be associated with is malware, but further analysis is the only way to confirm that definitely. 

**Answer the questions below**

1. What is the root domain for each URL? Defang the URL.
   * devret[.]xyz
---  
### Task 4: "Select your email provider to view document"
This email sample will highlight the following techniques:
* **Urgency**
* **HTML to impersonate a legitimate brand**
* **Link manipulation**
* **Credential harvesting**
* **Poor grammar and/or typos**
  
Let's take a closer look...

<img width="834" height="509" alt="image" src="https://github.com/user-attachments/assets/cf82c048-3ba2-4473-acdd-d88ada72c3f5" />

Here are some quick observations about this email sample:

1. The email was sent on Thursday, July 15th, 2021.  
2. A sense of urgency is introduced in this email. Notice that the link to download the fax document expires on the same day.
3. There is an action to perform. In this case, a button to download the fax. 

<img width="910" height="584" alt="image" src="https://github.com/user-attachments/assets/b11a6c3a-24bf-4f0d-ae61-c1b17ea32f74" />

The above image shows the victim is redirected to a page created to pass as OneDrive. Notice that the URL is not anything Microsoft-related. 

There are two more links for the victim to interact with. The victim has to click either button to obtain the fax document that is set to expire. 

<img width="911" height="588" alt="image" src="https://github.com/user-attachments/assets/1390da97-1cca-4da7-9ae0-a2d4704987d8" />

The victim is directed to yet another site. This one was crafted to resemble Adobe. Again, notice the URL. It doesn't look like it's related to Adobe.

Also, notice the page title in the tab. It's called "Share Point Online", which is a Microsoft product.  There are a couple of grammatical errors as well. 

The victim has options to sign in with the email provider of their choice. 

<img width="992" height="573" alt="image" src="https://github.com/user-attachments/assets/bbf08fd7-1b5c-4358-a349-749ce2851aaa" />

Our victim chose to log in with Outlook because, per the instructions, "To read the document, please enter with the valid email credentials that this file was sent to."; the email was viewed in Outlook. 

<img width="901" height="573" alt="image" src="https://github.com/user-attachments/assets/6cd5a552-786a-416f-b36e-be5fb69a3a03" />

In this sample, we can tell that fake credentials were entered, but even if the victim would have entered valid credentials, the error message would be the same. This scenario happens because the victim is not really authenticating to an email provider. Instead, the credentials that were entered now reside on the criminal's server. The criminal's objective to harvest credentials has been met. 

Lastly, notice more grammatical errors. All this work they put into this, you would think they would run a spell check. 

This email sample was obtained from Any Run. If you wish to interact with the email and see the full analysis, refer to the link below.

**Analysis:** https://app.any.run/tasks/12dcbc54-be0f-4250-b6c1-94d548816e5c/#

**Answer the questions below**

1. This email sample used the names of a few major companies, their products, and logos such as OneDrive and Adobe. What other company name was used in this phishing email?
   * Citrix
---  
### Task 5: "Please update your payment details"
This email sample will highlight the following techniques:

* **Spoofed email address**
* **Urgency**
* **HTML to impersonate a legitimate brand**
* **Poor grammar and/or typos**
* **Attachments**
  
Here are some quick observations about this email sample:

1. This email is made to appear that it's from Netflix Billing, but the sender address is z99@musacombi.online. 
2. Here is the element of urgency. The account was suspended, so the victim must act quickly. 
3. There is more of this sense of urgency in the email body. 

<img width="1003" height="291" alt="image" src="https://github.com/user-attachments/assets/c2e58b52-d89f-46cc-acf7-ecd928e6db53" />

Also, notice the different misspellings of the word Netflix. Not sure what was the purpose of that. 

Typically, you'll see this technique when it comes to typosquatting, but that wasn't the case here. 

<img width="1413" height="34" alt="image" src="https://github.com/user-attachments/assets/1495733f-2858-47d7-85a3-73a0f9ab3690" />

Ok, here is the meat and potatoes of this email. Apparently, the victim needs to open the attachment (PDF) to update their Netflix account. 

<img width="850" height="675" alt="image" src="https://github.com/user-attachments/assets/4eed962c-6117-4ab1-89b3-dc85c0bd030f" />

Notice the phone number for 'Netflix'. At first glance, that is an unusual phone number to send to a US-based victim. 

<img width="980" height="550" alt="image" src="https://github.com/user-attachments/assets/b3a9c110-1a50-49e8-8fc9-7a13ab7a7108" />

The attachment contains an embedded link titled 'Update Payment Account'. 

We'll look at this email attachment in closer detail in the upcoming Phishing Emails 3 room. 

**Answer the questions below**

1. What should users do if they receive a suspicious email or text message claiming to be from Netflix?
   * forward the message to phishing@netflix.com
---
### Task 6: "Your recent purchase"
This email sample will highlight the following techniques:

* **Spoofed email address**
* **Recipient is BCCed**
* **Urgency**
* **Poor grammar and/or typos**
* **Attachments**

Here are some quick observations about this email sample:

1. This email is made to appear that it's from Apple Support, but the sender's address is gibberish@sumpremed.com. 
2. This email wasn't sent directly to the victim's inbox but rather BCCed (Blind Carbon Copy). The recipient email looks like another spoofed email to appear as a legitimate Apple email address. 
3. Here is the element of urgency. Action is required on behalf of the victim. 

<img width="1006" height="153" alt="image" src="https://github.com/user-attachments/assets/d766e954-4144-43d8-86a7-40f5abfb6c4b" />

There are a few noticeable typos in both the sender and recipient email addresses: donoreply and payament.

This particular email doesn't necessarily have an email body. It's totally blank. The email simply contains an attachment. 

<img width="334" height="161" alt="image" src="https://github.com/user-attachments/assets/719bcebb-9fc2-45f6-b172-d99fdcb9feab" />

This file extension you may not be familiar to you. A .DOT file is page layout template files associated with Microsoft Word. 

<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/1b579b58-8428-4a2f-9e31-779f62cf88e4" />

The above image shows what is contained within the attachment. You can see that the file contains a large image to resemble an App Store receipt. 

Notice the link contains certain keywords related to Apple: apps and ios. 

**Answer the questions below**

1. What does BCC mean?
   * Blind Carbon Copy

1. What technique was used to persuade the victim to not ignore the email and act swiftly?
   * Urgency
---
### Task 7: "DHL Express Courier Shipping notice"
This email sample will highlight the following techniques:

* **Spoofed email address**
* **HTML to impersonate a legitimate brand**
* **Attachments**
  
Here are some quick observations about this email sample:

1. The sender's email doesn't match the company that is being impersonated, which in this case is DHL.
2. The subject line gives the impression that there is a package DHL will ship for you.
3. The HTML in the email body was designed to look like it was sent from DHL. 

<img width="971" height="290" alt="image" src="https://github.com/user-attachments/assets/37b4fa00-b0fa-4193-b487-a9c810e90458" />

Looking at the source code for the email, the link to view the email as a web page doesn't contain an actual destination URL. 

<img width="607" height="44" alt="image" src="https://github.com/user-attachments/assets/242c4b9c-b4de-4cd9-a953-20918ea5e89d" />

...

<img width="553" height="194" alt="image" src="https://github.com/user-attachments/assets/17f30ab0-7bf6-456b-aac4-aeeaae080ecb" />

The only element the victim can interact with in this email is the email attachment, which, in this case is an Excel document. 

<img width="796" height="698" alt="image" src="https://github.com/user-attachments/assets/6eca534e-197d-45eb-ac03-f61a4b7eaa20" />

The image below shows what is contained within the attachment.

<img width="980" height="551" alt="image" src="https://github.com/user-attachments/assets/fe638140-e52e-4983-acd5-a21c0fd1484a" />

The attachment runs a payload that throws an error. 

<img width="978" height="551" alt="image" src="https://github.com/user-attachments/assets/05bcc627-3b01-46e3-b6e2-78bba189e1ae" />

We'll look at this email attachment in closer detail in the upcoming Phishing Emails 3 room. 

**Answer the questions below**

1. What is the name of the executable that the Excel attachment attempts to run?
   * regasm.exe
---
### Task 8: Conclusion
In this room, we looked at various phishing samples. 

Some of the samples shared similar techniques whereas, others introduced a new tactic for you to see and learn from. 

Understanding how to detect phishing emails takes awareness training.

Visit the resources below to acquaint yourself with other signs to look out for in phishing emails. 

Additional Resources:

* https://www.knowbe4.com/phishing
* https://www.itgovernance.co.uk/blog/5-ways-to-detect-a-phishing-email
* https://cheapsslsecurity.com/blog/10-phishing-email-examples-you-need-to-see/
* https://phishingquiz.withgoogle.com
