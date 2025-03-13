<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Creating Users, Group Policy, and Managing Accounts with Active Directory in Azure</h1>
This tutorial outlines how to configure Remote Desktop for non-administrative users, automate user creation with PowerShell, and manage group policies. Additionally, I’ll cover account lockouts and log monitoring to simulate a real-life IT environment.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022, 2vCPUs, 8GM RAM
- Windows 10 Pro (22H2), 2vCPUs, 8GB RAM

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Remote Desktop for non-administrative users on Client-1
- Create a bunch of additional users and attempt to log into client-1 with one of the users
- Dealing with Account Lockouts
- Enabling and Disabling Accounts
- Observing Logs

<h2>Deployment and Configuration Steps</h2>

<p>
Log into Client-1 as mydomain.com\jane_admin,
Open system properties,
Click “Remote Desktop”,
Allow “domain users” access to remote desktop
</p>
<p>
<img src="https://github.com/user-attachments/assets/2128ea0c-9c0e-4461-a661-aeb128e5fe3a" height="80%" width="80%"/>
</p>

<br>
<p>
Login to DC-1 as jane_admin,
Open PowerShell_ise as an administrator,
Create a new File and paste the contents of the script into it
</p>
<p>
<img src="https://github.com/user-attachments/assets/f07c3806-7022-48d3-8e5a-cdbf7ba9bedc" height="80%" width="80%"/>
</p>

<br>
<p>
Run the script and observe the accounts being created
</p>
<p>
<img src="https://github.com/user-attachments/assets/6cce058d-6a28-4d8f-9d2a-3dded7629f52" height="80%" width="80%"/>
</p>

<p>
When finished, open ADUC and observe the accounts in the appropriate OU　(_EMPLOYEES)
</p>
<p>
<img src="https://github.com/user-attachments/assets/235c4b06-6bf6-4278-b3d6-34460c7045fb" height="80%" width="80%"/>
</p>

<br>
<p>
Logged into Client-1 with one of the accounts</p>
<p>
<img src="https://github.com/user-attachments/assets/e32562ad-8486-4861-94fc-96adf9918c93" height="80%" width="80%"/>
</p>

<br>
<p>
In dc-1, Configure Group Policy to Lockout the account after 5 attempts:
</p>
<p>
<img src="https://github.com/user-attachments/assets/b829a96a-8279-43b5-b653-8742a4ca9174" height="80%" width="80%"/>
</p>

<br>
<p>
Attempt to log in with it 6 times with a bad password
</p>
<p>
<img src="https://github.com/user-attachments/assets/7c8a1d88-89bb-4e8f-8bd2-e4cf5957de7b" height="80%" width="80%"/>
</p>

<br>
<p>
Observe that the account has been locked out within Active Directory,
Unlock the account,
Reset the password,
Attempt to login with it
</p>
<p>
<img src="https://github.com/user-attachments/assets/a6693c0a-82ed-4e4c-a1db-b24c8d66cc4e" height="80%" width="80%"/>
</p>

<br>
<p>
Reset the password,
Attempt to login with it
</p>
<p>
<img src="https://github.com/user-attachments/assets/f19ff017-b9f4-45a6-ab24-66d62194549f" height="80%" width="80%"/>
</p>

<br />
<h3>
  Enabling and Disabling Accounts
</h3>
<p>
  Disable the same account in Active Directory
</p>
<p>
<img src="https://github.com/user-attachments/assets/ad1db6e1-1565-44e2-b3e7-a28a4ea8e633" height="80%" width="80%"/>
</p>

<br>
<p>
Attempt to login with it, observe the error message
</p>
<p>
<img src="https://github.com/user-attachments/assets/9ad3643e-dac3-4cde-9ba8-691e0b22e269" height="80%" width="80%"/>
</p>

<br>
<p>
Re-enable the account and attempt to login with it.
</p>
<p>
<img src="https://github.com/user-attachments/assets/f7c28976-3807-48b5-a1ae-413dcfc39637" height="80%" width="80%"/>
</p>
<p>
<img src="https://github.com/user-attachments/assets/a0cb2fca-cecb-422a-84e5-03849cb2a640" height="80%" width="80%"/>
</p>

<h3>
  Observing Logs
</h3>
<p>
Observe the logs in the Domain Controller
</p>
<p>
<img src="https://github.com/user-attachments/assets/ba5cc4fb-746c-4fa7-bfc3-16ee50bf4227" height="80%" width="80%"/>
</p>

<h2>Active Directory: Creating Users, Group Policy, and Managing Accounts in Azure is Now Complete </h2>


<b>We've successfully configured Remote Desktop for non-administrative users, automated user creation with PowerShell, and managed group policies. Additionally, we covered account lockouts and log monitoring to simulate a real-life IT environment!  </b>
<br />
<br />
</p>
