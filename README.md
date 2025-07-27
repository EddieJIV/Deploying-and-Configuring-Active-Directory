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

<img width="800" height="800" alt="image" src="https://github.com/user-attachments/assets/b878d61e-f9de-4fc0-b5cf-ccd4f740df3b" />

- Once you've hit Next > on Additional Options, Paths, and Review Options and land on the Prerequisite Check page you can hit install!
  - Be advised, the computer is going to restart at this point. Now that we have actually turned it into an actual Domain Controller, we have to specify the context to which we want to log into it as.



---
Rough Draft Conclusion:
In this lab, we effectively installed Active Directory Domain Services on the DC-1 server, promoted it to a domain controller with a new forest (mydomain.com), created organizational units and user accounts, and then joined a client machine (Client-1) to the domain. Finally, we organized the clients in Active Directory! 

---







<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>

<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>


<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>

<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>


<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>

<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>


<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>

<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>


<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>

<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>


<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>

<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>


<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>

<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>


<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>

<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>


<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>

<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>


<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>

<table>
  <tr>
    <td>
      <img width="1000" alt="Img1" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
    <td>
      <img width="1000" alt="Img2" src="https://i.imgur.com/DJmEXEB.png" />
    </td>
  </tr>
</table>
