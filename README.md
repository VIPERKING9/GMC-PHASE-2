# GMC-PHASE-2


DISCOVERING THE WEBPAGE URL

Tools Needed:
VMWARE

KALI LINUX

WEBPAGE VIRTUAL MACHINE

Configuring your webpage virtual machine
Step 1.download a webpage hosting page virtual machine from https://www.vulnhub.com/entry/drunk-admin-web-hacking-challenge-1,14/ for vmware

Step 2.install the virtual machine

Step 3. in the vmware application go to the settings then network adapter

Step 4. change it to custom (vmnet1) for both your kali linux and the web hosting page virtual machine
Discovering the webpage url


Step 1. log in to your kali VM



![Screenshot 2024-08-31 195545](https://github.com/user-attachments/assets/0d3f669c-02e5-4e1f-acac-020c927edbcf)




Step 2. Open the terminal and input sudo apt update -y



![Screenshot 2024-08-31 201558](https://github.com/user-attachments/assets/72756371-7696-452d-b400-6068100a409a)


ungrade with sudo apt upgrade -y


![Screenshot 2024-08-31 202053](https://github.com/user-attachments/assets/1f9a6738-9885-4aa2-9107-65f98d7df35b)



once done 


Step 4. install zapproxy


![Screenshot 2024-08-31 212947](https://github.com/user-attachments/assets/934cb17b-fa3a-4864-8757-0ab6342b0695)


step 5. install foxy proxy


![Screenshot 2024-08-31 214116](https://github.com/user-attachments/assets/5716d395-71ce-4bd3-a20f-67cc909fddc0)



now open foxy proxy to configure



![Screenshot 2024-08-31 214430](https://github.com/user-attachments/assets/7d418a7f-4c8e-4f85-832e-c6d6a52f8bfc)



click on options then click proxies



![Screenshot 2024-08-31 215601](https://github.com/user-attachments/assets/3007434c-21f9-4e4d-9c0d-03b164ae743b)




 Title: ZAP Type: HTTP: Hostname: 127.0.0.7 Port: 8080 Once finished, click ‘Save’



 Whenever we want to proxy through ZAP, head to the addon and select ZAP

Install ZAP certificate

If you don’t use ZAP’s built-in browserbrowse function, you will need to manually set up the certificate on your browser. If you tried accessing any site running SSL/TLS while using your browser outside of ZAP, you must configure it to use ZAP’s CA root certificate to avoid any certificate warnings.




![image](https://github.com/user-attachments/assets/061ed578-9584-4924-a60c-75a36c4885dd)




ZAP recommends you launch your browser through the “Quick Start” area but if you will rather configure your browser manually, here is how to install the Zap certificate- First, with ZAP running and your Foxyproxy enabled to use ZAP, head https://www.zaproxy.org/download/ once there,click “Download to download the certificate to your system.





![Screenshot 2024-08-31 223839](https://github.com/user-attachments/assets/0d2e889b-5dc2-4dab-9cc9-01b1ada4972f)




Now, go to your firefox search bar, type: preferences, and press enter. This will take you to the settings page. Search for “certificate” and find the option “ view certificates”




![Screenshot 2024-08-31 224507](https://github.com/user-attachments/assets/150fa463-0064-41d7-a5c4-ca49184e394b)




The view certificate let’s you see all your trusted CA certificates. You can import a new certificate for ZAP by pressing “import” and select the file you downloaded.




![Screenshot 2024-08-31 224557](https://github.com/user-attachments/assets/24ce918b-b027-44ba-ab10-2a96054362d1)




In the pop up, select “Trust this CA to identify websites,then click Ok.




![image](https://github.com/user-attachments/assets/d289f4e1-4a5f-4a77-872d-5868c411d6ae)



Any encrypted traffic will work when the ZAP proxy is turned on, allowing us to intercept requests.

 Starting ZAP We can start ZAP in kali in one of two ways; enter zaproxy in the terminal or open it from the applications menu under “Web Application Analysis’




 ![Screenshot 2024-08-31 225634](https://github.com/user-attachments/assets/1f6f9b00-921a-43f1-b5ce-41ebd5341039)



 Then it will open like this:




![Screenshot 2024-08-31 225909](https://github.com/user-attachments/assets/e88b1f3b-e0ca-4a3b-8148-56975657d7f1)




When you start ZAP, you will see a screen asking, “ Do you want to persist this ZAP session” Persistence will save everything to an HSQL database that you can access to view it’s contents or reload back into ZAP to see all of the request history, site information etc.

We will be choosing “No, I do not want to persist this session at this session at this moment in time”.




![Screenshot 2024-08-31 225952](https://github.com/user-attachments/assets/e20593b9-a037-4381-9247-86c9f4ef5537)




Before we start using ZAP, let’s examine the main interface and show where some of the key features are located. The interface has a lot of information, ZAP does many things.





![Screenshot 2024-08-31 230035](https://github.com/user-attachments/assets/bbe483b7-96f1-43f1-bbdc-3e7bdf5d6f54)



Features:

(1) Menu Bar: Here, you can create and manage sessions, create reports, find tools, get help and more.

(2) Toolbar: Includes button that provide shortcuts to the most commonly use features. (3) Tree window: Displays the hierarchical view of the site you are testing and the script tree. (4) Quickstart/Workspace Window: This is a quick and ebay way to use ZAP, especially if you are new. It is also displays request response and scripts you can edit. (5) Information Window, including: History tab: This shows a log of all the HTTP requests and responses sent and received through ZAP. Search tab: This allows you to search through the requests and responses. Alerts tab: Displays security alerts found during the scans. Output tab: provides detailed output from various scans and processes (6) Footer: Displays ZAP status information.

Alerts Counter: This displays a summary of the alerts found. It’s color-coded (like red, yellow, etc.) to represent the severity of the alerts found during the scanning process. Main Proxy: This is the main proxy configuration that ZAP uses, which is set to "localhost:8080." Current Scans: This section displays any currently running scans, with icons indicating their status or progress.

Update Addons

Before you begin using ZAP, you should always check for and update any addons that need to be updated. This ensures that you have the most up-to-date experience.

Press CTRL + U or use the toolbar shortcut to check for updates.



![Screenshot 2024-08-31 231846](https://github.com/user-attachments/assets/c2fb2833-91dc-4912-82a3-c97001564286)




This will open the installed add-ons. Next to each add-on, you can see its version number and a brief description of its function. If a newer version of an add-on is available, you'll see “Update” to the right of the description.

You can select the ones you want to update individually, but the best way is to update everything simultaneously. Select any add-on and “Update All” to initiate the update.



![Screenshot 2024-08-31 232234](https://github.com/user-attachments/assets/483a077f-4542-44b9-9386-3880f508808c)




ZAP Tips Before we begin, here are a few tips to remember when using ZAP.

Right-click everywhere and anywhere to see what options are available to you.





![Screenshot 2024-08-31 232636](https://github.com/user-attachments/assets/e4d57012-c005-455d-b621-cfb4e44290c5)







ZAP Spidering The first tool we’ll show you is the standard spider in ZAP. This spider requests web pages and analyzes them for links to other pages within the same web application. This recursive process keeps going as long as new links are discovered.

The spider builds out the site tree, showing you all the pages found.

This spider is quite fast and can be used for standard apps. However, you should still consider using this spider on more modern apps in conjunction with the AJAX spider.

You can select “Spider” from the “Tools” menu or use the CTRL + ALT + S shortcut to start it






![image](https://github.com/user-attachments/assets/eff8c6fb-6f1c-4538-803b-2735af6f24b5)





In the following window, enter the URL of the web app you are spidering and select “Recurse.” This tells ZAP to crawl all URLs or directories from the starting URL.

Once you’re ready, select “Start Scan.”




![Screenshot 2024-08-31 233227](https://github.com/user-attachments/assets/93dca1d5-640e-4518-b4b0-996909f1c5f2)





Once the spidering is finished, you’ll see all the nodes found for the web app. The lower-right corner indicates that 91 Nodes were found "Nodes Added: 47," which tells us the number of new items the Spider has found and added to the Sites tree during its crawl.





![Screenshot 2024-08-31 234000](https://github.com/user-attachments/assets/65ddcd7d-6a47-4064-a830-e5b97f650004)




ZAP AJAX Spidering

More modern apps use JavaScript, and the traditional ZAP spider doesn't really understand how to crawl these properly.

This is where the AJAX spider comes in. This spider launches a browser, clicks on things, and even fills out forms, giving you a more comprehensive web app overview. It tries to imitate a user's behavior while interacting with the application.

This spider is much slower than the standard one but works much better with today's modern apps.

To open the AJAX spider, use the “Tools” menu or the shortcut CTRL + ALT + X.

Here, you’ll set the URL of the app you want to test and the browser the spider will use. Options include Firefox, Chrome, and Safari.

You can also set advanced options. When you’re ready, select “Start Scan.”





![image](https://github.com/user-attachments/assets/1e10ebfd-b3c0-4077-b829-0b92a920ecaf)






Once the scan is finished, any nodes found will be shown in the site tree area with a red spider next to them. The AJAX spider crawled 1461 URLs compared to the standard spider's 138.






![image](https://github.com/user-attachments/assets/c938634d-f024-48bf-b998-197a6c55db0e)





ZAP Scanning Before discussing ZAP's scanning features, remember you should only use ZAP’s active scanning to attack an application you have explicit permission to test.

Passive Scanning Passive scanning just involves looking at the raw requests and responses. ZAP doesn’t actually do anything; it only looks at the traffic that passes through it. It analyzes this traffic to identify potential vulnerabilities without sending any new requests.

Passive scanning is safe to use on any web application.

When you spider a site, ZAP performs a passive scan and reports any alerts in the “Alerts” tab.






![image](https://github.com/user-attachments/assets/17bbbe1d-9888-4b3f-93a9-5da862ff649e)







Active Scanning

Active scanning attempts to find other vulnerabilities using known attacks against the selected targets. It can only find certain vulnerabilities, including XSS, SQL injection, buffer overflows, Log4Shell, and remote file inclusion.

The Active scanner cannot find logical vulnerabilities, such as broken access control.

You can set policies for your scans, although we won’t discuss that here. These policies allow you to set the threshold for the number of issues raised, and the strength options determine the number of attacks performed per parameter.

As with most tools in ZAP, you can set the options for active scanning. These include the number of hosts scanned concurrently, maximum scan duration, and whether to handle CSRF tokens.

Choose “Automated Scan” from the quick start menu to begin.







![image](https://github.com/user-attachments/assets/754b9e82-6633-4542-b762-6dbccdd8fceb)






This will open up the automated scan launch screen. Here, you’ll set the URL and which spider and browser you want to use. Once you’re ready, select “Attack” to begin.





![image](https://github.com/user-attachments/assets/6a326685-7eba-4714-85d0-c04a3ae0f2bf)





Once the scan is finished, you can find all the alerts raised by ZAP in the “Alerts” tab.





![image](https://github.com/user-attachments/assets/c2358ea5-7714-4056-a426-2211763cb702)





As you can see from the above screenshot, ZAP found 15 vulnerabilities organized by severity: high (red), medium (orange), low (yellow), and informational (blue).

ZAP shows you the number of vulnerabilities it has found. Let’s look closer at the SQL injection. Select the arrow next to it to see where the issue was found in the application. Then, select the URL to see detailed information about the alert.






![image](https://github.com/user-attachments/assets/f90bda8f-5707-4884-933a-388d72e19310)







ZAP provides quite a bit of information. On the right panel, you’ll see the URL where the alert was found and its risk and confidence level. You’ll also see a CWE and WASC ID from common software security vulnerability lists. Each vulnerability has its own ID number.

Next, you’ll see a description of the alert and how ZAP confirmed this alert. It notes the attack method used ("AND 1=1 --"). You’ll need to verify this to see if the vulnerability actually exists.

It also suggests a potential solution: do not trust client-side input and use server-side validation, such as prepared statements, to mitigate the risk.

Next, we will generate report





![image](https://github.com/user-attachments/assets/2fbbf1d0-cb6c-4e99-b58c-c13950707af2)







Next click on generate report



![Screenshot 2024-09-01 000119](https://github.com/user-attachments/assets/995d61ab-ab34-4666-bd5f-bbb83877019e)





here are the reports




![image](https://github.com/user-attachments/assets/6b7df43b-92f1-4e88-871c-4947ca334e16)



![image](https://github.com/user-attachments/assets/9849003b-42bd-4a4c-b4c4-eccbbbdfa46b)




![image](https://github.com/user-attachments/assets/cdb89f15-a0e2-410b-81f2-16305d9f0906)





![image](https://github.com/user-attachments/assets/a8122669-2bd8-4b2f-92c1-a6324ad47be5)





![image](https://github.com/user-attachments/assets/bbdfbe62-4004-40b7-a5f9-77790b273124)





![image](https://github.com/user-attachments/assets/15aa70f0-7dde-4d07-952f-2d65c818b4c8)






![image](https://github.com/user-attachments/assets/96a4a312-76b0-44b1-bce6-967035747d1c)





![image](https://github.com/user-attachments/assets/b5e13c70-30a8-4baf-bd31-cb5fc2c71a14)





![image](https://github.com/user-attachments/assets/589e4e83-d5bf-4d0a-b9dd-bcfdcd3d3e98)





![image](https://github.com/user-attachments/assets/b4582381-dc11-4b68-a400-2590d6da3e82)






![image](https://github.com/user-attachments/assets/4d40a1e7-563b-49a2-b67a-edc283c77886)





![image](https://github.com/user-attachments/assets/41faf418-372f-4ace-b046-1b9c2a7dc437)





![image](https://github.com/user-attachments/assets/523a2dc6-d05a-45a1-9dd7-42b64e03127d)






![image](https://github.com/user-attachments/assets/d07cd9dd-ea67-42af-b688-b49f1430267c)






![image](https://github.com/user-attachments/assets/539bd25f-40be-4bd0-922e-23855f08bf0f)





![image](https://github.com/user-attachments/assets/a269265a-4117-4414-85c1-bd05cf29834b)







![image](https://github.com/user-attachments/assets/aefc1e6c-eae1-4008-9d1e-1d31c776ec3d)


























































 








