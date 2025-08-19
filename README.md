<p align="center">
<img width="auto" height="auto" alt="AD" src="https://github.com/user-attachments/assets/8997adb8-3e38-4019-9da5-6fadf4bab369" />
</p>

# Deploying and Configuring Active Directory
*Step-by-step instructions for installing, configuring, and deploying Acive Directory in a Windows enviorment.*

## Environments and Technologies Used:

- Microsoft Azure (Virtual Machines/Cloud Compute)
- Remote Desktop Protocol
- Windows Server
- Windows 10
- Active Directory 

## Lab Prerequisites:
- PC or Laptop
- Connection to the Internet
- Microsoft Azure Subscription
- [Lab: Preparing Active Directory Infrastructure in Azure](https://github.com/EddieJIV/Lab-Architecture-Preparing-Active-Directory-Infrastructure-in-Azure)

# Installation Steps:

- First things first, make sure both DC-1 and Client-1 are spun up and you are logged into both, ready to go!
  - Remember to be aware of what VM you are on while doing the work; if you need to, check the system settings.
- We are going to be working in DC-1 for this first part of the lab, where we will officially install Active Directory Domain Services, promote it as an official domain controller, and set up a new forest.
  
<table>
  <tr>
    <td>
      <img width="700" height="700" alt="Open Server Manager" src="https://github.com/user-attachments/assets/5ee1951d-c7cf-4d4b-80e6-34e3657d468b" />
    </td>
    <td>
      <img width="900" height="900" alt="image" src="https://github.com/user-attachments/assets/89fb3083-d0ae-4aba-876d-b7be15ee1ec6" />
    </td>
  </tr>
</table>

- Open up the start menu and navigate to Server Manager.
- Click on "Add Roles and Features"


<table>
  <tr>
    <td>
      <img width="1000" height="1000" alt="image" src="https://github.com/user-attachments/assets/f971fc98-81f7-4f40-9bdb-519945b63e95" />
    </td>
    <td>
      <img width="1000" height="1000" alt="image" src="https://github.com/user-attachments/assets/cdcbb539-cbe0-4a82-a3b4-94af397323f8" />
    </td>
  </tr>
</table>

- Click Next > on the "Before you Begin" page.
- Click Next > on the "Installation Type" page as long as Role-based or feature-based installation is checked, which it should be.
- For Server Selection, there should only be one (DC-1) so just click Next >.


<table>
  <tr>
    <td>
     <img width="auto" height="auto" alt="image" src="https://github.com/user-attachments/assets/128be849-38e9-405d-91ae-6a80f9ed7a1d" />
    </td>
    <td>
     <img width="auto" height="auto" alt="image" src="https://github.com/user-attachments/assets/ec11a38a-3440-46c5-be19-51516187dfb6" />
    </td>
  </tr>
</table>

- For the "Server Roles" page we are going to Select, "Active Directory Domain Services".
- Once you've clicked the box for Active Directory Domain Services you can simply check the box that says, "Add Features".
- Once you've done so, you can click on Next >
- Click Next > again on Features
- Click Next > once more on AD DS

<table>
  <tr>
    <td>
      <img width="1063" height="659" alt="image" src="https://github.com/user-attachments/assets/77715306-41dd-4df8-a3dc-c9eb84f93d34" />
    </td>
    <td>
      <img width="946" height="659" alt="image" src="https://github.com/user-attachments/assets/39d1fc3c-7786-48d9-86fc-70a6b29c6584" />
    </td>
  </tr>
</table>


- On the Confirmation page, we have to check the box to restart the destination server automatically and click yes when prompted 
- Once we've said yes to the restart we can go ahead and click on install!
- Once installed, click Close.

---
Now that Active Directory Domain Services installed, we're going to promote DC-1 to an actual Domain Controller.

<img width="900" height="900" alt="image" src="https://github.com/user-attachments/assets/424dff1b-653a-435b-862e-0c499d6a1ac0" />

- Click on the flag icon in the top right coner of the server manager, and click on, "Promote this server to a domain controller."

<img width="900" height="900" alt="image" src="https://github.com/user-attachments/assets/0673f421-9c60-4d7c-a364-918e63219b16" />

- On the Deployment Configuration page, check the box labeled as "Add a new forest".
- For purposes of the lab, we are simply going to name our domain mydomain.com when we specify the root domain name.
- Once you've named the root domain mydomain.com just click on next.


<table>
  <tr>
    <td>
      <img width="1000" height="1000" alt="image" src="https://github.com/user-attachments/assets/3ac59118-606a-4269-aced-7f180cc7c16a" />
    </td>
    <td>
      <img width="1000" height="1000" alt="image" src="https://github.com/user-attachments/assets/962ba0ca-f11f-426f-b473-e7d54a0c3cc0" />
    </td>
  </tr>
</table>

- Leave everything alone on the Domain Controller Options page.
- The only thing we will need to do is set a password for the Directory Services Restore Mode (DSRM)
  - We are likely never going to need it for this labn, so just make the Password, "Password1".
  - Once you've set the password, click Next >.
- For DNS Options make sure that "Create DNS delegation" is unchecked and click next.
- For Additional Options, Paths, and Review Options we can just click on Next >.

<img width="800" height="800" alt="Install" src="https://github.com/user-attachments/assets/b878d61e-f9de-4fc0-b5cf-ccd4f740df3b" />

- Once you've hit Next > on Additional Options, Paths, and Review Options and land on the Prerequisite Check page you can hit install!

## ⚠ Be advised, once the installation is complete, DC-1 is going to restart, and now that we've promoted it into an actual Domain Controller, we'll have to specify the context to which we want to log into it as going foward. ⚠


<p align="center">
<img width="526" height="160" alt="mydomain.com" src="https://github.com/user-attachments/assets/9890558f-9db2-4912-8d18-b547f1633cb4" />
</p>

- So, in order for us to log into the domain going fowards, for the username we have to use mydomain.com, followed by a \ (yes, it MUST be a backslash) then our username.
  - What this effectively will look like when logging back into DC-1 for the first time following the promotion to DC, is:
  - username: mydomain.com\(account name)
  - password: Cyberlab123!
---
- Once you've logged back into DC-1 in with your new credentials as lab user we are now going to create a Domain Admin user within the domain.

<img width="700" height="700" alt="AD UnC" src="https://github.com/user-attachments/assets/e0105cb2-f4b3-49bf-9772-67e967abe93d" />

- In order to do so, navigate to Active Directory Users and Computers within the Windows start menu by either typing it into the search bar or clicking on the Windows Administration Tools dropdown and locating Active Directory Users and Computers. Be careful not to open the wrong thing :) 


<img width="700" height="700" alt="NEW OU" src="https://github.com/user-attachments/assets/b6636f81-cf04-4019-93f0-e46d40b829ea" />

- Locate mydomain.com and right click on the icon indicated above, click on new, then click on Organizational Unit.

<table>
  <tr>
    <td>
      <img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/73b6cf6d-88b6-437f-ac6a-9f550c87f5f8" />
    </td>
    <td>
      <img width="700" height="700" alt="3 new OUs" src="https://github.com/user-attachments/assets/7e05fcf3-8704-44fa-8441-40fc05ad7585" />
    </td>
  </tr>
</table>

- We are going to name our first organizational unit, _EMPLOYEES
- Click Ok.
- Repeat the process for another Organizational Unit called, _ADMINS
- Finally, make one more OU called _CLIENTS

---
- We are now going to create a new employee named “Jane Doe” with the username of “jane_admin” / Cyberlab123! and add jane_admin to the “Domain Admins” Security Group.

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/d7b7adcf-8483-49e2-a114-607b7e5bab2e" />

- Left click on mydomain.com
- Right click on _ADMINS, click New, then Click User.

<table>
  <tr>
    <td>
      <img width="700" height="700" alt="Jane create 1" src="https://github.com/user-attachments/assets/1dd8bebd-8e09-4ba2-bddb-2870477dcfde" />
    </td>
    <td>
      <img width="700" height="700" alt="Jane create 2" src="https://github.com/user-attachments/assets/cd7d34a0-d837-45b1-824c-9906ef254c81" />
    </td>
  </tr>
</table>

- Make our new Admins name Jane Doe, with a username of Jane_admin
- Click Next >
- For our password, we will use Cyberlab123!
- Uncheck the box that says "User must change password at next logon
- Although it is not safe or smart to do in real life, for this lab, we are going to check the box that says "Password never expires"
- Click Next >
- Then click Finish!
---
This account is not an Admin yet just because we named it Jane_admin and put it in the admin OU. What makes this account a domain admin is by adding the newly created account to the built in Domain Admin Security Group. 

<img width="auto" height="auto" alt="Janes acct properties" src="https://github.com/user-attachments/assets/f0960b97-3ed3-4df6-aa08-f8e5e49cd50c" />


- Left click on the _ADMINS folder, locate our new user Jane Doe.
- Right click on her account.
- Navigate to and left click on properties.
- Within Jane Doe Properties, click on "Member Of"
- Then, once inside "Member of" click on Add.

<table>
  <tr>
    <td>
      <img width="700" height="700" alt="precheck" src="https://github.com/user-attachments/assets/321c05fd-2b5f-4d09-94fc-e9bd6e9dea9c" />
    </td>
    <td>
      <img width="700" height="700" alt="Post check name" src="https://github.com/user-attachments/assets/af3c7dee-59d8-467c-a6b5-6888db00020a" />
    </td>
  </tr>
</table>

- Once you've clicked add, type, "Domain Admins" into the Object names text box and click on Check Names
- If you've done this correctly it should "find" the name and underline it, like so.
- Click OK.

<img width="460" height="539" alt="image" src="https://github.com/user-attachments/assets/e73cf0d1-c505-415c-8b64-165c763176fa" />

- Click Apply.
- Then click OK.
And NOW, this account is a Domain Admin!
- Lets log out of DC-1, and log back in as our newly created user Jane Doe (Jane_admin)

## ⚠ From now on, we are going to be logging into DC-1 as our newly created Admin, so keep her login credentials handy for this lab ⚠ 

*and the following several labs as well!*

- Domain Admin Account:
  - user: mydomain.com\jane_admin
  - password: Cyberlab123!

<img width="auto" height="auto" alt="Janes first admin login" src="https://github.com/user-attachments/assets/0c618510-35d3-45ea-b3ef-4968ff1c2d5f" />

- Reconnect to DC-1 with Jane_admins login information.

---

- The next thing we're going to do is join Client-1 to the domain.
- In order to do so, log into Client-1 as the original local admin, labuser, if you havent already done so at the start of this lab.
- So you will have both VM's open. The DC-1 will be logged into with Jane_admin, and Client-1 will be logged into as labuser.

<img width="700" height="700" alt="Client-1 System" src="https://github.com/user-attachments/assets/03c2aeaf-c364-4fc2-95ff-158dbbf6512f" />

- In Client-1, type about in the search bar.
- Verify it is in-fact Client-1 youre operating on by double checking the Windows specifications
- Then click on Rename this PC (advanced) on the right-hand side of the page.

<table>
  <tr>
    <td>
     <img width="700" height="700" alt="Change" src="https://github.com/user-attachments/assets/94d08ce1-a087-4af6-8bea-9e751618f9fe" />
    </td>
    <td>
      <img width="700" height="700" alt="Member of" src="https://github.com/user-attachments/assets/706fc5dc-0cc2-4481-aefa-d400ae58c51c" />
    </td>
  </tr>
</table>

- Under the Computer Name tab, click on Change...
- Under Member of, click on the Domain bullet, and this is where we join it to the domain, so put mydomain.com
- Click OK

<img width="700" height="700" alt="Join!" src="https://github.com/user-attachments/assets/ea352842-d514-4877-ac7c-6288fc4870d2" />



- Because we set the DNS settings on this to use DC-1's private IP address, its able to locate the Domain Controller for the mydomain.com domain
- Additionally, since we gave Jane-admin the correct permissions and privlidges, we can enter her account information here to join our domain.

<img width="296" height="147" alt="image" src="https://github.com/user-attachments/assets/50e3457f-dd9d-476f-8fa0-5618c9508060" />

- If you minimize the settings window we've been working in you should see the pop-up welcoming Client-1 to your domain!
- At this point you will be prompted to restart, so click OK, then click close on System properties if you need to still, and you'll be able to restart Client-1.
  
---
- For the final step of this lab, we are going to go back into DC-1, verify that Client-1 shows up under Active Directory Users and Computers, and move it into the _CLIENTS Organizational Unit we created earlier!

<img width="507" height="357" alt="image" src="https://github.com/user-attachments/assets/ef6b7814-931b-4a28-bf31-b5b4b1e6c80f" />

- So, back in DC-1, search Active Directory Users and Computers in the search bar or you can find it under Windows Administrative Tools in the Start menu.

- Expand mydomain.com and click on Computers, and you should now see Client-1.

<table>
  <tr>
    <td>
      <img width="700" height="700" alt="Move warning" src="https://github.com/user-attachments/assets/90837e12-9081-45c7-9964-86b80109ec08" />
    </td>
    <td>
      <img width="700" height="700" alt="Moved to _CLIENTS" src="https://github.com/user-attachments/assets/e7bcbe7c-80cd-4eee-aa52-67fbc9f641a2" />
    </td>
  </tr>
</table>


- Left click and drag Client-1 into the _CLIENTS Organizational Unit.
  - Once you do so, you will be prompted with a warning, say Yes.
---

## Conclusion

In this lab, we successfully installed and configured Active Directory Domain Services on DC-1, promoted it to a domain controller with a new forest, mydomain.com, and set up organizational units (_EMPLOYEES, _ADMINS, _CLIENTS) to organize resources effectively. We created a Domain Admin account and used it to manage user privileges, then joined a client machine (Client-1) to the domain and verified its placement in ADUC.

While this lab focused on the core steps for deploying Active Directory and connecting clients, Active Directory offers a wide array of administrative capabilities, including group policy management, advanced security configuration, and automation via PowerShell.

I hope you'll join me in the next lab where we further our intuition and understanding of these enviorments, skills, and topics!

**Reminder:** When you are finished with this lab, be sure to pause your virtual machines in Azure to avoid unnecessary costs. We will continue to use DC-1 and Client-1 in the next lab, so do not delete them. Just stop them until you’re ready to continue on to the next lab! You only pay for compute while VMs are running. Storage (the OS disks) remains, but the cost is minimal compared to leaving VMs powered on. You can safely resume your VMs when you’re ready to continue.


