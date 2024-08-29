# Introduction to penetration Testing

- On Performing Penetration testing, there are some Additional Steps Than the 5 Phases of Ethical hacking.
    1. Pre-Engagement
    2. Information gathering
    3. Scanning
    4. Gaining Access
    5. Maintaining Access
    6. Proof-of-concept
    7. Post-Engagement.

1. **Pre-Engagement**

- This is the 1st Step, and the Main Legal Part of the process.
- This Is Held, Before Starting any kind of penetration tests.
- This Step will give you **full permission** and **Understanding** about the system you are going to Test on.
- This consists
    A. Scoping Questionnaires
    B. Pre-Engagement meeting
    C. Kick-off meeting

A. Scoping Questionnaire

- This Step will help us to **gather detailed information** about the target environment, including what assets will be tested(Scope), the type of testing required (e.g., black-box, white-box), any restrictions, and timelines.
- This scoping questionnaire should clearly explain our services and may typically ask them to choose one or more from Our Cyber Security Service.
- *Example:* we can hack on 172.16.2.32/18 but not on another subnets.

B. Pre-Engagement Meeting

- Here We will discuss the details gathered from the scoping questionnaire and clarify any uncertainties.
- **Participants:** Key stakeholders from both the client and the security team, including project managers, technical leads, and legal representatives.
- **Outcome:** This meeting finalizes the scope, discusses potential risks, and addresses any legal or compliance concerns.
- There are some Agreements you do on this step.
    - **Non-Disclosure Agreement(NDA)** refers to a *secrecy contract* between the client and the contractor regarding all written or verbal information concerning an order/project.

C. Kick-OFF meeting

- “Kick-Off” means be started
- Purpose of this Step is To officially start the engagement after all preparations are complete.
- Try to Discuss the engagement schedule, communication protocols, escalation processes, and the final testing approach(retest, or no-retest).
- It Finally Ensures everyone involved understands their roles and responsibilities and that the testing can proceed as planned.

2. **Information Gathering/Recon/Footprint/**

- **Information Gathering** is Collecting data about some network/host/system.
- *Footprinting* =>  *Footstep*  +  *printing(logging)*
- Most of the people find Footprinting boring, but it is a very important part of Ethical Hacking. Almost 85% of Hacking.

## Types of Information Gathering

- based on how we do the recon
    1. Active Footprinting
    2. Passive Footprinting

1. Active Footprinting

- is when we try to gather information directly by contacting that person.
- *Example:* When you go to the bank and ask for some information.
- Chatting with person on social media to know about them.
- Doing Active Footprinting without permission is **ILLEGAL!!**

2. Passive Footprinting

- is when you gather informations from another person,3rd party or by checking public sources.
- *Example:* To know the bank working time i can see the posted texts.
- To know someone name by reading the username.

### What type of information do you gather? 

- We gather different Kinds of Informations:
A. Host
    - Websites
    - Computers
    - Smart Phone
B. Network
    - Home Network
    - Companies networks
C. Person/Organization
D. Application

A. **website**

- The information we gather about a websites are
    - IP Addresses
    - Development frameworks
        - Technologies used and versions
    - Name
    - DNS information
    - VHOST, Subdomains

#### To get an IP

- Active recon(Terminal)
    - ping "website-link"
    - nslookup "website-link"
    - host "website-link"
- Passive recon
    - www.nslockup.io

#### Development frameworks

- browser extension
    - Wapplyzer
    - Builtwith
- Terminal tool
    - whatweb "website-link"

#### Details about domains

- Terminal tools
    - whois "website-link"
    - dig "website-link"

B. **Computer/Phone**

- The informations we gather about a Computers/Hosts are
    - IP Addresses
    - OS informations
    - HostName
    - MAC address
    - Open services or ports

C. **Networks**

- The informations we gather about a Networks are
    - IP Addresses
    - Architecture
    - Class and Type of Network
    - Subnets / VLANs
    - Hosts on that Network
    - Strength and security of that Network

## OSINT-OpenSource intelligence

- persons information can be gather by the **active** and **passive**.
- Gathering and Analyzing Different informatons based on **Public resource** passively is called **OSINT**(open source intelligence).
- we can get lot of informations for system, user, host, ... through passive activity.

### Search Engines

- **Search Engines** are website those used to search any Document and Medias on the internet.
- They are very essential tools for performing **OSINT**.
- *Example*: google, Bing, Yahoo, …

### Shoadn

- It is a specialized search engine designed to find and index internet-connected devices, often referred to as the **"search engine for the Internet of Things (IoT)"**.
- Unlike traditional search engines like Google or Bing that index web pages, Shodan focuses on discovering devices such as servers, routers, webcams, industrial control systems, and other IoT devices If They are Publicly Exposed.
- Link: https://www.shodan.io/

### Maltego

- A powerful data *mining and visualization* tool used for link analysis.
- It helps in mapping relationships between entities like people, domains, IP addresses, and more.
- Graphical representation of relationships, making it easier to analyze complex networks.

D. **Personal informations**

- The informations we gather about a Persons are
    - Full Name
    - Address
    - Physical Address
    - All Social Media Address
    - Phone address
    - What the person loves
    - Job
    - Friends
    - Status
    - skills
- There are many methods To Gather these informations, Lets See about Personal informations :...

### Getting Names by Phone number

- For this purpose you can use https://www.truecaller.com/
- You can get the phone number from social media like telegram, some posted promotion, from websites.
- You can Get Email and Locations too.

### Getting social medias Addresses

- If you have Full name of a person, Just use search engines(google,bing,yahoo)
- Also you can use tool called **sherlock** from github.

### Getting physical Addresses

- Peoples share their living place on social medias info page.
- Else there are many methods: 
    - Sending links and when people access the link u can get the IP then you can just **geolocate** the place.
- If you got the private ip address of someone you can insert it to *https://www.iplocation.net*
- The method of getting the IP might be tricky but detail we will learn on Social Engineering class.

### Knowing people's behavior and Obsession

- Peoples are being open on social medias, so we Security Testers have access about person behaviors and likes.
- *Example*: **instagram** is the best place to get info about some user.
- Also by seeing **telegram** Profiles you can get more information about their,religion status,mindset, ideology, family.
- By checking their followings/friends you can get more common pictures and events, etc….

E. **Application/software**

- The informations we gather about a Applications are
    1. **Static Analysis**: Analyzing with Codes(no Execution).
        - Which programming language used
            - *Android App*: Java,Kotlin, Flutter, JS?
            - *Desktop*: JS, C#, C++?
        - Which framework used
        - File Structure and Assets.
    2. **Dynamic Analysis**: Analysis with Executing the program.
        - Their logic and Function
        - Their Requests with servers.

### Reverse image search

- **Reverse image search** is a technique of searching with images.
- We all search with text but we can search with images to This can give as more information.
- *Ex*: think like user posted a picture with a background of some area, if the user didnt talk about the place we can just search the image and the search engines will give as some similar photos where they are taken in same place(not 100% accurate).
- We can use:
    1. https://tineye.com/
    2. https://www.labnol.org/reverse/
    3. https://images.google.com/ 

### Google Dorking(Google Hacking)

- **Google hacking** is using different Google operators to effectively optimize search results.
- It also involves using Google to *identify vulnerabilities in websites.*
- Results are highly customizable.

#### Basic Operators

- For inclusion of something common (+) 
- Terms you want to exclude (-)
- Search for an exact term (“ ")
- ( * ) any word (wild card)
    - If you include * within a query, it tells Google to try to treat the star as a placeholder for any unknown term(s) and then find the best matches.
- ( | ) boolean ‘OR’

#### Adavanced Operators

- These are Syntaxes used by Google.	
    - **intitle** ==> Google returns results with the word/phrase found within the title of the page.
        - Example:- intitle:index.of
                  - intitle:”Hackers Bible”
    - **inurl** ==> Finds a specific term within the URL.
        - Example:- inurl:view/index.shtml
    - **filetype** ==> Searches for a specific filetype
        - Example:- “Hacking” filetype:pdf
                  - filetype:txt
    - **Intext** ==> Google returns links that contains Texts from that link.
        - Example:- intext:”Hackers in Ethiopia”


### Google Hacking Database(GHD)

Link ==> https://www.exploit-db.com/google-hacking-database