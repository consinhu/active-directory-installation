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

