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
<h3>Step 1: Create and connect to Azure Virtual Machine (VM)</h3>
1. Create Virtual Machine with Windows Server: In the Azure portal, go to the "Virtual Machines" section and click on "Create a new VM". Choose a suitable Windows Server image (example -> Windows Server 2019 or 2022).</p>

![image](https://github.com/user-attachments/assets/0f737f05-31a0-4d6a-915b-58afe69c9fa8)

<br />
<br />
2. Configure VM settings: Select the desired region, size, network, and storage options for the VM. Ensure the VM is connected to a Virtual Network (VNet), as this will be necessary for the AD domain to communicate with other resources.</p>

![image](https://github.com/user-attachments/assets/a572d1cf-d255-4cc9-9fdb-0f4097178c1c)

<br />
<br />
3. Assign a public IP (optional): Assign a public IP if you need remote access to the VM, or use a private IP for secure internal access.</p>

![image](https://github.com/user-attachments/assets/cbd5010e-3da6-4d6b-97e4-219cfcf8a0ba)

<br />
<br />
4. Open Remote Desktop Connection in Virtual Machine and connect to it using Remote Desktop Protocol (RDP) by using the public IP or private IP (if configured with a VPN)</p>

![image](https://github.com/user-attachments/assets/8376390e-8e8b-42ee-a8f8-3efbf6938263)


<p>
<br />
<br />
<p>
<h3>Step 2: Install Active Directory Domain Services (AD DS)</h3>
1. Open Server Manager: Once logged in to the VM, open Server Manager on the Windows Server VM.</p>

![image](https://github.com/user-attachments/assets/b3a7b91b-4648-4b03-8748-e52f8f485b35)

<br />
2. Add Roles and Features: In Server Manager, click on Add roles and features, select Active Directory Domain Services (AD DS) under the Roles tab, and click Next to install the role. Follow the prompts to complete the installation.</p>

(Adding Roles)
![image](https://github.com/user-attachments/assets/12e6e490-5160-4748-ad7c-caf14cb3fe38)</p>

<br />
(Adding Features)

![image](https://github.com/user-attachments/assets/b06f9220-5914-45fb-87c6-f4d61f58d675)


<p>
<br />
<br />
<p>
<h3>Step 3: Promote the VM to a Domain Controller</h3>
1. Promote to Domain Controller: After installing AD DS, a notification will appear in Server Manager prompting you to promote this server to a Domain Controller. Click on the link to start the configuration.</p>

![image](https://github.com/user-attachments/assets/fc0ec558-8e74-46f2-a325-1a5a3e43c3eb)

<br />
2. Choose Domain Configuration: In the wizard, select whether you are creating a new forest or adding the VM to an existing domain. If this is the first Domain Controller, choose Add a new forest and specify the Root domain name (example -> example.com).</p>

![image](https://github.com/user-attachments/assets/04b10199-e756-4a26-ad60-38d75f560233)

<br />
3. Set Directory Services Restore Mode (DSRM) Password: Provide a secure DSRM password to be used for recovery purposes.</p>

![image](https://github.com/user-attachments/assets/5954b614-5321-416b-a3da-d88de449e117)

<br />
4. Complete the Promotion: Review your selections, and click Next to begin the promotion process. The server will automatically restart to apply the changes.</p>

![image](https://github.com/user-attachments/assets/eaba8a30-777d-4954-80da-d86bec283f45)

<p>
<br />
<br />
<p>
<h3>Step 4: Configure DNS Settings (VM)</h3>
1. DNS Server Configuration: The VM should automatically configure itself as a DNS server when promoted to a Domain Controller. Ensure that DNS settings are properly configured so that the Domain Controller can resolve domain names within the network.</p>

![image](https://github.com/user-attachments/assets/8e58a251-2da1-4e99-b702-122cb8cb32c8)

<br />
2. Check DNS Resolution: Test DNS resolution by pinging the domain name or checking the DNS server settings on the VM to ensure it’s properly handling domain name queries.</p>

![image](https://github.com/user-attachments/assets/103d2e67-a5b4-44dd-b877-a7602c7fef5c)

<p>
<br />
<br />
<p>
<h3>Step 5: Secure and Test the Domain Controller</h3>
1. Secure the Domain Controller: Configure firewall rules and Network Security Groups (NSGs) in Azure to restrict access to the Domain Controller and allow only authorized users or systems to communicate with it.</p>

![image](https://github.com/user-attachments/assets/7fea0cc4-a564-4946-b949-d0361d698ee1)

<br />
2. Test the Domain: Ensure that you can join other VMs or computers in the Azure environment to the domain. Test logging in with a domain account and verify that the Domain Controller is functioning as expected.</p>

![image](https://github.com/user-attachments/assets/2ed2f3dc-fd78-4a3c-8eb6-cd692831dadc)

