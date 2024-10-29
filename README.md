<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com/watch?v=wS9BRmhKm50)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

1. Set Up Azure Active Directory: Create an Azure Active Directory (AAD) tenant via the Azure portal to manage users and groups.
2. Configure Domain Services: Enable Azure AD Domain Services (AAD DS) to provide domain-join capabilities and group policies without the need for on-premises infrastructure.
3. Sync On-Premises Directory (Optional): If applicable, set up Azure AD Connect to synchronize your on-premises Active Directory with Azure AD for a hybrid environment.
4. Assign Roles and Policies: Configure role-based access control (RBAC), security policies, and conditional access settings to manage user permissions and enhance security.

<h2>Deployment and Configuration Steps</h2>

<p>
  
![erererer](https://github.com/user-attachments/assets/421c604e-9d96-43e7-9f55-16217cdbc536)


<p>

1. Create Azure VM: Set up an Azure VM that will act as a domain controller in your Azure portal.
2. Install Active Directory Domain Services: On the Azure VM, install the Active Directory Domain Services role using Server Manager.
3. Promote to Domain Controller: Run the Active Directory Domain Services Configuration Wizard to promote the VM to a domain controller, creating a new domain or adding to an existing one.
</p>
<br />

<p>

![cxcxcxcx](https://github.com/user-attachments/assets/3e74dd9f-0fe8-4466-82f6-a707b88b2591)


<p>

4. Configure Virtual Network: Ensure the VM is connected to a virtual network that allows communication with your on-premises network.
5. Set Up VPN Gateway: Establish a site-to-site VPN connection between your on-premises network and Azure to enable secure communication.
6. Configure DNS Settings: Set the Azure VM’s DNS to point to your on-premises DNS server for proper name resolution.
</p>
<br />

<p>

![lklklklk](https://github.com/user-attachments/assets/49e6ade7-695a-4e30-9afe-92525f0c21f4)


<p>

7. Test Connectivity: Verify connectivity between on-premises resources and the Azure VM to ensure the setup works correctly.
8. Implement Replication (if needed): If adding to an existing domain, ensure Active Directory replication is functioning properly between the on-premises and Azure DC.
9. Monitor and Maintain: Set up monitoring for the Azure VM and perform regular maintenance to ensure high availability and security of the Active Directory environment.
</p>
<br />
