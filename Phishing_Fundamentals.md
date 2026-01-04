# Exercise 1: Phishing Analysis Fundamentals
---
## 1. Objective
The goal of this lab was to dissect the components of an email to understand how phishing attacks work and how to detect them. I explored email addresses, delivery protocols, headers, and body content.
---
---
## 2. Walkthrough & Analysis

### Task 1: Introduction
I started the machine and reviewed the basic concepts of email analysis.
* **Status:** Completed.
---
### Task 2: The Email Address
It's only appropriate to start this room by mentioning the man who invented the concept of emails and made the @ symbol famous. The person responsible for the contribution to the way we communicate was Ray Tomlinson. 

The invention of the email dates back to the 1970s for ARPANET. Yep, probably before you were born. Definitely, before I was born. :)

So, what makes up an email address?

1. User Mailbox (or Username)
2. @
3. Domain

Let's look at the following email address, billy@johndoe.com.

1. The user mailbox is billy
2. @ (thanks Ray)
3. The domain is johndoe.com

To simplify this even further, think about the street on which you live on.

* You can think of your street as the domain. 
* The recipient's first/last name, along with the house number in this scenario, represents the user mailbox. 
* With this information, the postal worker delivering the mail knows into which mailbox to put the letter(s). 

Next, let's look at the network protocols used to send an email from the sender to the recipient.

**Answer the questions below.**

1. Email dates back to what time frame?
   * 1970s
---
### Task 3: Email Delivery 
A handful of protocols are involved with the "magic" that takes place when you hit SEND in an email client. 

By now, you should already know that certain protocols were created to handle specific network-related tasks, such as email. 

There are 3 specific protocols involved to facilitate the outgoing and incoming email messages, and they are briefly listed below.

* SMTP (Simple Mail Transfer Protocol) - It is utilized to handle the sending of emails. 
* POP3 (Post Office Protocol) - Is responsible transferring email between a client and a mail server. 
* IMAP (Internet Message Access Protocol) - Is responsible transferring email between a client and a mail server.

You should have noticed that both POP3 and IMAP have the same definition. But there are differences between the two.

The difference between the two is listed below: (credit AOL -- You got mail!)

**POP3**

Emails are downloaded and stored on a single device. Sent messages are stored on the single device from which the email was sent. Emails can only be accessed from the single device the emails were downloaded to.If you want to keep messages on the server, make sure the setting "Keep email on server" is enabled, or all messages are deleted from the server once downloaded to the single device's app or software.

**IMAP**

Emails are stored on the server and can be downloaded to multiple devices.Sent messages are stored on the server.Messages can be synced and accessed across multiple devices.

**Answer the questions below.**

1. What port is classified as Secure Transport (STARTTLS) for SMTP?
   * 587

2. What port is classified as Secure Transport for IMAP?
   * 993

1. What port is classified as Secure Transport for POP3?
   * 995
---
### Task 4: Email Headers
Great! We know how an email travels from point A to point B and all the protocols involved in the process. 

This task is to understand the components of what makes up an email message when it arrives in an inbox.

This understanding is necessary if you wish to analyze potentially malicious emails manually. 

Before we begin, we need to understand that there are two parts to an email:

* the email header (information about the email, such as the email servers that relayed the email)
* the email body (text and/or HTML formatted text)

The syntax for email messages is known as the Internet Message Format (IMF).

Let's look at email headers first. 

What do you look for when analyzing a potentially malicious email?

Let's start with the following email header fields:

1. From - the sender's email address
2. Subject - the email's subject line
3. Date - the date when the email was sent
4. To - the recipient's email address

This is usually clearly visible in any email client. Let's look at an example of these fields in the below image.

Warning: This is a snippet from an actual email. The email in the below image is from a honeypot Yahoo email address. Don't engage/interact with the email addresses or IP addresses revealed in this room.

<img width="1126" height="149" alt="image" src="https://github.com/user-attachments/assets/2fb444ba-e1d8-4563-9845-711ae03bf7f9" />

**Note:** The numbers in the above image correspond to the email header fields bullet list above.

Another method to obtain the same email header information, and more, is by viewing the 'raw' email details.

When looking at an email header in detail, it can be intimidating at first, but it's not so bad if you know what to look for. 

**Note:** Depending on your email client, whether a web client or a desktop app, the steps to view these email header fields will vary, but the concept is the same. 

In the below image, you can see how to view this information within Yahoo.

<img width="572" height="266" alt="image" src="https://github.com/user-attachments/assets/40e27ef6-8a80-4e8a-ab93-777630af70d4" />

Below is a snippet of the raw message for the email sample.

<img width="885" height="735" alt="image" src="https://github.com/user-attachments/assets/4d2abe7b-b3cf-4ab8-98cf-a0457fb2cc50" />

**Note:** The above image shows some, not all, of the information within an email's header. 

You can review this email in the Email Samples directory on the Desktop within the attached virtual machine. The email is titled email1.eml. 

From the above image, there are other email header fields of interest. 

1. X-Originating-IP - The IP address of the email was sent from (this is known as an X-header)
2. Smtp.mailfrom/header.from - The domain the email was sent from (these headers are within Authentication-Results)
3. Reply-To - This is the email address a reply email will be sent to instead of the From email address

To clarify, in the email in the sample above, the Sender is newsletters@ant.anki-tech.com, but if a recipient replies to the email, the response will go to reply@ant.anki-tech.com, which is the Reply-To, and NOT to newsletters@ant.anki-tech.com. 

Below is an additional resource from Media Template on how to analyze email headers:

https://web.archive.org/web/20221219232959/https://mediatemple.net/community/products/all/204643950/understanding-an-email-header

**Note:** The questions below are based on the Media Template article.

**Answer the questions below**

1. What email header is the same as "Reply-to"?
   * Return-Path

1. Once you find the email sender's IP address, where can you retrieve more information about the IP?
   * http://www.arin.net
 --- 
### Task 5: Email Body
The email body is the part of the email which contains the text (plain or HTML formatted) the sender wants you to view. 

Below is an example of a text-only email.

<img width="612" height="175" alt="image" src="https://github.com/user-attachments/assets/4d16af36-8249-4c90-8f63-997e2b69f64b" />

Below is an example of the HTML formatted email.

<img width="705" height="297" alt="image" src="https://github.com/user-attachments/assets/e2a5b946-f0fa-4b1b-b10f-234dbd708afb" />

The above email contains an image (which was blocked by the email client) and embedded hyperlinks.

HTML is what makes it possible to add these elements to an email.

To view an email's HTML code is the same approach shown below, but it may vary depending on the webmail client. 

In the example below, the screenshot is from Protonmail. 

<img width="393" height="321" alt="image" src="https://github.com/user-attachments/assets/3104cda9-1dcb-4e8f-af90-038778cf68f1" />

A snippet of the HTML code is shown below.

<img width="948" height="622" alt="image" src="https://github.com/user-attachments/assets/9a7abd55-d561-4612-ac40-322bd71b09f9" />

In this specific email web client, Protonmail, the option to switch back to HTML is called "View rendered HTML".

<img width="585" height="272" alt="image" src="https://github.com/user-attachments/assets/904480d3-44ef-4c86-b355-ddafd6b2feaf" />

Again, it will be different for other webmail clients.

Lastly, emails may contain attachments. The same premise applies; you can view an email's attachment from an email's HTML format or by viewing the source code. 

Let's look at a few examples below.

The following example is an HTML formatted email from "Netflix" with an attachment. The web client is Yahoo!

<img width="882" height="418" alt="image" src="https://github.com/user-attachments/assets/15180dcc-1b3a-4453-ace5-1a76bbe8779e" />

1. The email body has an image.
2. The email attachment is a PDF document.

Now let's view this attachment within the source code.

<img width="581" height="259" alt="image" src="https://github.com/user-attachments/assets/2a7d823e-22cc-4e3f-9576-967b595c7df9" />

From the above example, we can see the headers associated with this attachment:

* Content-Type is application/pdf. 
* Content-Disposition specifies it's an attachment. 
* Content-Transfer-Encoding tells us it's base64 encoded. 

With the base64 encoded data, you can decode it and save it to your machine.

**Warning:** When interacting with attachments, proceed with caution and make sure you don't double-click an email's attachment by accident. 

**Note:** Headers specific to 'content' can be found in various locations within an email message source code, and they're not only associated with attachments. For example, Content-Type can be text/html, and Content-Transfer-Encoding can have other values, such as 8bit. 

**Answer the questions below**

1. In the above screenshots, what is the URI of the blocked image?
   * https://i.imgur.com/LSWOtDI.png

1. In the screenshots above, what is the name of the PDF attachment?
   * Payment-updateid.pdf

1. In the attached virtual machine, view the information in email2.txt and reconstruct the PDF using the base64 data. What is the text within the PDF?
   * THM{BENIGN_PDF_ATTACHMENT}
---
### Task 6: Types of Phishing
Now that we covered the general concepts regarding emails and how they travel from sender to recipient, we can now talk about how this method of communication is used for nefarious purposes. 

Different types of malicious emails can be classified as one of the following:

* **Spam** - unsolicited junk emails sent out in bulk to a large number of recipients. The more malicious variant of Spam is known as MalSpam.
* **Phishing** -  emails sent to a target(s) purporting to be from a trusted entity to lure individuals into providing sensitive information.
* **Spear phishing** - takes phishing a step further by targeting a specific individual(s) or organization seeking sensitive information.
* **Whaling** - is similar to spear phishing, but it's targeted specifically to C-Level high-position individuals (CEO, CFO, etc.), and the objective is the same.
* **Smishing** - takes phishing to mobile devices by targeting mobile users with specially crafted text messages.
* **Vishing** - is similar to smishing, but instead of using text messages for the social engineering attack, the attacks are based on voice calls.   

When it comes to phishing, the modus operandi is usually the same depending on the objective of the email.

For example, the objective can be to harvest credentials, and another is to gain access to the computer. 

Below are typical characteristics phishing emails have in common:

* The sender email name/address will masquerade as a trusted entity (email spoofing)
* The email subject line and/or body (text) is written with a sense of urgency or uses certain keywords such as Invoice, Suspended, etc.
* The email body (HTML) is designed to match a trusting entity (such as Amazon)
* The email body (HTML) is poorly formatted or written (contrary from the previous point)
* The email body uses generic content, such as Dear Sir/Madam.
* Hyperlinks (oftentimes uses URL shortening services to hide its true origin)
* A malicious attachment posing as a legitimate document

We'll look at each of these techniques (characteristics) in greater detail in the next room within the Phishing module.

**Reminder:** When dealing with hyperlinks and attachments, you need to be careful not to accidentally click on the hyperlink or the attachment. 

Hyperlinks and IP addresses should be 'defanged'. Defanging is a way of making the URL/domain or email address unclickable to avoid accidental clicks, which may result in a serious security breach. It replaces special characters, like "@" in the email or "." in the URL, with different characters. For example, a highly suspicious domain, http://www.suspiciousdomain.com, will be changed to hxxp[://]www[.]suspiciousdomain[.]com before forwarding it to the SOC team for detection. CyberChef is a great tool that can help you with defanging, try it out for the following questions!

Analyze the email titled email3.eml within the virtual machine and answer the questions below.

**Note:** Alexa is the victim, and Billy is the analyst assigned to the case. Alexa forwarded the email to Billy for analysis. 

**Answer the questions below**

1. What trusted entity is this email masquerading as?
   * Home Depot

1. What is the sender's email?
   * support@teckbe.com

1. What is the subject line? 
   * Order Placed : Your Order ID OD2321657089291 Placed Successfully

1. What is the website for the - CLICK HERE URL in a defanged format? (e.g. https://website.thm)
   * hxxp[://]t[.]teckbe[.]com
---  
### Task 7: Conclusion
Before ending this room, you should know what BEC (Business Email Compromise) means.

A BEC is when an adversary gains control of an internal employee's account and then uses the compromised email account to convince other internal employees to perform unauthorized or fraudulent actions. 

**Tip:** You should be familiar with this term. I have heard this question asked before in a job interview. 

Within this room, we covered the following:
* What makes up an email address?
* How an email travels from sender to recipient.
* How to view the source code of an email header.
* How to view the source code of an email body.
* Understand the pertinent information we should obtain from an email we're analyzing.
* Some common techniques attackers use in spam and phishing email campaigns.

In the upcoming Phishing Analysis series, we'll look at samples of various common techniques used in phishing email campaigns, along with tools to assist us with analyzing an email header and email body. 

**Answer the questions below**

1. What is BEC?
   * Business Email Compromise
