# Active Directory Installation 
<p align="center">
<img width="566" src="https://www.31west.net/wp-content/uploads/2022/11/what-is-active-directory-and-why-is-it-used.png.avif" alt="active directory logo" /> </p>

<h1>Active Directory Deployed in UTM on a macOS Host</h1>
<p>In this part of my Active Directory HomeLab, I worked on outlining the steps of implementing an on-premises Active Directory within a macOS Virtual Machine through UTM.</p>

<p>As someone who was new to Active Directory before this project, I learned that tools like Active Directory allow for centralized user and device management, resource sharing, and seamless remote access onto a singular virtual desktop.</p> 

<p>Active Directory is also popular and helpful industry-wise  due to the fact that the number of end users often outweighs the number of resources available. It is also an important security tool that allows IT administrators to easily manage access and permissions for a given organization.</p>

<h2>Environments and Technologies Used</h2>

- UTM Virtual Machines
- Active Directory Domain Services

<h2>Operating System Used</h2>

- Windows Server 2016

<h2>Basic Deployment and Configuration Steps</h2>

- Windows Server Setup
- Promoting server to Domain Controller
- Create Active Directory domain
- Create organizational units (OUs) for different departments
- Create user accounts and groups within OUs

**Setting up Windows Server VM**
<p> To preface, I am working on an M1 Mac. If you have an Intel, you will need to follow different steps. I recommend referencing the article at this link: https://tcsfiles.blob.core.windows.net/documents/AIST3720Notes/WindowsServeronanIntelMac.html </p>
  
<p>We will need to find installation media or an ISO image corresponding to a Windows Server OS. I found mine at the official Microsoft Windows page, but just make sure to find a reliable one because this is getting downloaded on your main OS. Anything from 2016 onwards should work fine.</p>

<p>Start by opening UTM. If you do not have UTM, you can find it online or in the App store on your Mac. I would also create a separate folder to store all your related downloads for easy access. In UTM, choose Create a New Virtual Machine ( File > New from the menu or clicking the plus sign next to existing VMs also work) and choose Emulate, not Virtualize. This is because the M1 chip is unable to fully virtualize a Windows Server architecture.</p>

<p>Here's where things start to get a little complicated. You will need to select an ISO image to boot. I will explain more in later steps, but for now just select the file installed earlier and continue through the setup steps.</p>

<p>Accept the defaults for Hardware and Storage settings. Just click Continue for each wizard.</p>

<p>If you'd like, you can enable a Shared Directory, which will be a folder already present on your Mac system that will be made available in your emulated Windows Server. This is optional. Click continue after your choice is made.</p>

<p>In Summary, make sure to rename the emulated VM to something relevant like Windows Server 2016. No other changes need to be made. Click Save.</p>

<p>We can now start installing Microsoft Server OS. Click Play button in UTM or right-click VM to choose Run. UTM's icon will pop up alone for a bit before leading to a prompt saying "Press a key to boot from the CD/DVD". Act quickly and press Enter (or a key other than the space bar) within a few seconds before the time is up. If you miss this window, don't worry! Just restart your VM using menu options and try again. Once successful, you will see a Microsoft Server OS Setup window. Either accept or change the parameters based on your preferences. Then click Next.</p>

<p>The setup will prompt for a product key; just click "I don't have a product key". The next screen will ask you to select the type of operating system you want installed. For this page, you'll want to pick something that includes Desktop Experience or else you'll get only the command prompt when you open the server. Click Next.</p>

<p>Now, you might end up with an error screen saying "Windows cannot find the Microsoft software license terms" after hitting Next. This issue typically arises when an installation media is selected durin the initial VM creation stage when it should be added after. It's just confusing because in UTM, users are required to select an ISO prior to booting the VM, but there's a relatively quick and easy fix. First, in the top right corner of the VM window, find the small circle icon and eject the ISO. This will cause the VM to be unable to display anything, but you can add back in the ISO by right clicking on the VM in the list format after it's stopped and going to Edit > IDE drive > Browse. Find the file containing the installation media and select it. Then, repeat the last two steps before this paragraph and you should be able to get back to where we left off.</p>

<p>This time after selecting the proper OS type, you should be met with a notice and license terms screen. Check the accept box and click Next.</p>

<p>On the next screen, choose Custom Install since we are building from scratch not upgrading. Once you hit the Custom option, the setup wizard will ask for where you want to install your OS. Just keep it at the default location. For me, it was also the only option. Click Next.</p>

<p>Windows will begin the installation process. It will take likely half-an-hour or longer so you can either use your computer to do other things during this or leave it alone. Just make sure you do not shut it down or put it to sleep during this time.</p>

<p>After the installation is complete, the entire VM will restart and re-display the "Press a key to boot from CD/DVD". Do NOT hit a key this time and just wait for the system to start up with the newly installed Windows Server. In a bit, you will be prompted for a password for the built-in administrator (you) to use to sign in. Hit Finish.</p>

<p>VM will take you to the lock screen where Windows Server will require you to Ctrl+Alt+Delete to unlock. Since we are on a Mac, the Alt key will be replaced with Option. Make sure to also click into the VM window before entering the key combination. After you bypass the lock screen, enter you Admin password and press enter.</p>

<p>Server Manager will automatically start launching and we can move on to the second and third parts of this activity. If there is a network discovery popup, select the option that makes your server discoverable.</p>

**Promoting Server to Domain Controller and Creating an Active Directory Domain**

<p>Once Server Manager is finished launching (it is going to take a while because everything is a slower and more laggy on an emulated VM), navigate to the Manage tab and select Add Roles and Features. A wizard will pop up afterwards and we will select destination server, server roles, and role services as well as promote the server as a domain controller.</p>

<img src="screenshot1.png">

_This step will load for while once a destination server is selected. Do NOT click the red "X" that shows up in the top right corner. Clicking it will cancel the loading process_

<img src="screenshot2.png">
<img src="screenshot3.png">

_Make sure to enable all the same roles and services as I have in the two screenshots above in order for Active Directory to function properly. For any other pages, just hit next all the way through until you get to Results_

<img src="screenshot6.png">

_In the Results page, hit Install. When installation is finished, do NOT close the window. In order to promote our server to domain controller, click on the blue text under Active Directory Domain Services that I've circled in red._

<img src="screenshot7.png">
<img src="screenshot8.png">
<img src="screenshot9.png">

_Active Directory Domain Services Configuration Wizard should open up. In Deployment Configuration, toggle the Add a new forest option and input your root domain name (make something up in the format "example.local"). You will also be prompted for a password to your directory services in Domain Controller Options. Afterwards, in Additional Options, make sure to verify your NetBIOS domain name, which would be the part of the root domain before .local_

**OUs, Groups, and Users in Active Directory**

<p>System will restart after finishing the previous steps for installing Active Directory. Once you're back in, you can locate the Active Directory services we installed in the startup menu on Windows Server. Click into Active Directory Users and Computers.</p>

<p>To create OUs or organizational units, groups, and users, I've included some screenshot examples.</p>

<img src="screenshot4.png">
<img src="screenshot5.png">

<p>When IT people say OU, they're abbreviating for organizational unit, which you probably already caught on to. OUs are basically container-like structures that carry different types of objects such as users, groups, computers, servers, etc. In a real world setting, OUs can be used to categorize departments based on geography, function, or people.</p>

<p align="center"><img width="500" src="https://media.licdn.com/dms/image/v2/D5612AQEGP6tY0_ONlg/article-inline_image-shrink_400_744/article-inline_image-shrink_400_744/0/1711164399502?e=1757548800&v=beta&t=UBamXwstgbA2RusKGQrEcib2r_SQy_F3Uf583GzquiE"></p>

<p>Groups can be slightly more complicated and there are a a few considerations that must be made before creating a group, specifically group scope and group type. Group Scope refers to the extent to which a group's members and permissions can be applied within a domain. There are three main levels which are Universal, Global, and Domain (local).</p>

<p align="center"><img width="500" src="https://i.sstatic.net/BmAHl.jpg"></p>

<p>There's also Group Type. Security Group Types are used to assign permissions to shared resources while Distribution Group Types are mainly used for email lists and cannot be used to assign permissions.</p>
