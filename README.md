# Active Directory Installation 
<p align="center">
<img width="566" src="https://www.31west.net/wp-content/uploads/2022/11/what-is-active-directory-and-why-is-it-used.png.avif" alt="active directory logo" /> </p>

<h1>On-premises Active Directory deployed in UTM</h1>
<p>In this part of my Active Directory HomeLab, I worked on outlining the steps of implementing an on-premises Active Directory within a macOS Virtual Machine through UTM --quite an unusual pairing.</p>

<p>As someone who was new to Active Directory before this project, I learned that tools like Active Directory allow for central user and device management, resource sharing, and seamless remote acess onto a singular virtual desktop.</p> 

<p>Active Directory is also popular and helpful industry-wise in many organizations due to the fact that the number of end users often outweighs the number of resources available.</p>

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

<p>Here's where things start to get a little complicated. You will need to select an ISO image to boot. I will explain more in later steps, but for now just continue through the setup steps.</p>

<p>Accept the defaults for Hardware and Storage settings. Just click Continue for each wizard.</p>

<p>If you'd like, you can enable a Shared Directory, which will be a folder already present on your Mac system that will be made available in your emulated Windows Server. This is optional. Click continue after your choice is made.</p>

<p>In Summary, make sure to rename the emulated VM to something relevant like Windows Server 2016. No other changes need to be made. Click Save.</p>

<p>We can now start installing Microsoft Server OS. Click Play button in UTM or right-click VM to choose Run. UTM's icon will pop up alone for a bit before leading to a prompt saying "Press a key to boot from the CD/DVD". Act quickly and press Enter (or a key other than the space bar) within a few seconds before the time is up. If you miss this window, don't worry! Just restart your VM using menu options and try again. </p>
