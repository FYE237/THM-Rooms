## PATH : Comptia pentest+

## [OWAPS TOP 10 - ROOM](https://tryhackme.com/room/owasptop10)

### Injection
1.  OS command injection
    * Task 5 : COmmand injection practical: 

         2. How many non-root/non-service/non-daemon users are there?
            Answer : Check the file /etc/passwd
        4. What is the user's shell set as?
            Answer : We just need to correlate the current user's shell details in the /etc/passwd file.
        5. What version of Ubuntu is running?
            Answer: Another simple question that can be checked by a single command `lsb_release -a`.
        6. Print MOTD :
        Print out the MOTD. What favorite beverage is shown?
        This one was a bit confusing question as I did not know what MOTD meant. After some googling, I came to know MOTD stands for 'Message of The Day'. The issue that I faced with this challenge was before Ubuntu 16 the MOTD was saved in /etc/motd file which was not present in this system as it is not running on version 16. But on other versions, the files related to MOTD are stored in the directory /etc/update-motd.d. We just need to cat the files present in this folder and go through them to find the answer to this question.


####  Notes 

SOmetimes users don't change the default configuration. So it can be helpful to google, check repository on github and see if there is defaults values and try them.

### XSS Explained
1. Stored XSS - the most dangerous type of XSS. This is where a malicious string originates from the website’s database. This often happens when a website allows user input that is not sanitised (remove the "bad parts" of a users input) when inserted into the database.
2. Reflected XSS - the malicious payload is part of the victims request to the website. The website includes this payload in response back to the user. To summarise, an attacker needs to trick a victim into clicking a URL to execute their malicious payload.
3. DOM-Based XSS - DOM stands for Document Object Model and is a programming interface for HTML and XML documents. It represents the page so that programs can change the document structure, style and content. A web page is a document and this document can be either displayed in the browser window or as the HTML source.

    ### XSS Payloads
* Popup's (<script>alert(“Hello World”)</script>) - Creates a Hello World message popup on a users browser.
* Writing HTML (document.write) - Override the website's HTML to add your own (essentially defacing the entire page).
* XSS Keylogger (http://www.xss-payloads.com/payloads/scripts/simplekeylogger.js.html) - You can log all keystrokes of a user, capturing their password and other sensitive information they type into the webpage.
* Port scanning (http://www.xss-payloads.com/payloads/scripts/portscanapi.js.html) - A mini local port scanner (more information on this is covered in the TryHackMe XSS room).


### Cookies Practical
We canuse cookie to get which are stored in the browser. search storage in the inspect  tab to bypas access.

    Example of usecase display in this part : 

    if there is a usertype field in the cookies.We can set the value to admin. It will generate a new session ID. And therefore we gain access to admin pages through this session.


 

