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
<br />

![Screen Shot 2025-03-10 at 2 21 18 PM](https://github.com/user-attachments/assets/2128ea0c-9c0e-4461-a661-aeb128e5fe3a)

<p>
Login to DC-1 as jane_admin,
Open PowerShell_ise as an administrator,
Create a new File and paste the contents of the script into it
</p>
<br />

![Screen Shot 2025-03-10 at 2 28 39 PM](https://github.com/user-attachments/assets/f07c3806-7022-48d3-8e5a-cdbf7ba9bedc)

<p>
Run the script and observe the accounts being created
</p>
<br />

![Screen Shot 2025-03-10 at 2 45 56 PM](https://github.com/user-attachments/assets/6cce058d-6a28-4d8f-9d2a-3dded7629f52)

<p>
When finished, open ADUC and observe the accounts in the appropriate OU　(_EMPLOYEES)
</p>
<br />

![Screen Shot 2025-03-10 at 2 47 25 PM](https://github.com/user-attachments/assets/235c4b06-6bf6-4278-b3d6-34460c7045fb)

<p>
Logged into Client-1 with one of the accounts</p>
<br />

![Screen Shot 2025-03-10 at 2 49 17 PM](https://github.com/user-attachments/assets/e32562ad-8486-4861-94fc-96adf9918c93)

<p>
In dc-1, Configure Group Policy to Lockout the account after 5 attempts:
</p>
<br />

![Screen Shot 2025-03-11 at 9 42 07 AM](https://github.com/user-attachments/assets/b829a96a-8279-43b5-b653-8742a4ca9174)

<p>
Attempt to log in with it 6 times with a bad password
</p>
<br />

<img width="592" alt="Screen Shot 2025-03-11 at 9 49 22 AM" src="https://github.com/user-attachments/assets/7c8a1d88-89bb-4e8f-8bd2-e4cf5957de7b" />

<p>
Observe that the account has been locked out within Active Directory,
Unlock the account,
Reset the password,
Attempt to login with it
</p>
<br />

![Screen Shot 2025-03-11 at 9 50 40 AM](https://github.com/user-attachments/assets/a6693c0a-82ed-4e4c-a1db-b24c8d66cc4e)

<p>
Reset the password,
Attempt to login with it
</p>
<br />

<h3>
  Enabling and Disabling Accounts
</h3>
<p>
  Disable the same account in Active Directory
</p>

![Screen Shot 2025-03-12 at 1 03 35 PM](https://github.com/user-attachments/assets/ad1db6e1-1565-44e2-b3e7-a28a4ea8e633)

<p>
Attempt to login with it, observe the error message
</p>

<img width="590" alt="Screen Shot 2025-03-12 at 1 05 36 PM" src="https://github.com/user-attachments/assets/9ad3643e-dac3-4cde-9ba8-691e0b22e269" />

<p>
Re-enable the account and attempt to login with it.
</p>

![Screen Shot 2025-03-12 at 1 06 13 PM](https://github.com/user-attachments/assets/f7c28976-3807-48b5-a1ae-413dcfc39637)

![Screen Shot 2025-03-12 at 1 13 29 PM](https://github.com/user-attachments/assets/a0cb2fca-cecb-422a-84e5-03849cb2a640)


<h3>
  Observing Logs
</h3>

<p>
Observe the logs in the Domain Controller
</p>

![Screen Shot 2025-03-12 at 1 30 51 PM](https://github.com/user-attachments/assets/ba5cc4fb-746c-4fa7-bfc3-16ee50bf4227)


