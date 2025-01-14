# Network File Share And Permissions

# Description
In this project we will learn how to share out resources over a network and also how to create file shares that allow Read, Write or Deny access to individual users or groups.
# Enviorments and Utilities Used
 - Active Directory
 - Virtual Machines
 - Microsoft Azure
# Operating Systems Used
 - Windows 10
# Project Walk-through
This project is another minior continuation of Active Directory that we setup in the AD project.

Our First step is to longin to dc-1 as jane_admin password Cyberlab123!. In dc-1 pull up your Active Directory Users and Computers and pick a random name to use to log into client-1 with and the password will be Password1.
![image](https://github.com/user-attachments/assets/9135886f-9f20-4072-a745-434b7d7c8723)

On dc-1 search in the bar at the bottom left File Exploer then go to This PC and select C drive. On here we will make 4 new folders. right clcik and go to "new" then "folder. We will name them "read-access", "write-access", "no-access" and "accounting".
![image](https://github.com/user-attachments/assets/33ce858b-ad06-4024-af74-6f020ed040bc)

Next we will set the permissions. Right clcik read-access folder go to Properties, Sharring tab, Hit the sahre button type in "domain users" Add then make sure permission levle is set to Read, then hit share.
![image](https://github.com/user-attachments/assets/26dc6c0d-994f-482c-a9ff-8356d716536b)

Write access folder we will add domain users again and change the permission to Read/Write.
![image](https://github.com/user-attachments/assets/9908eb45-554c-41e7-9205-8152bc39ac19)

We will do the same for no-access. Add domain admins, and Read/Write Permissions. We will leave accounting alone for now.
![image](https://github.com/user-attachments/assets/cd50fe94-5691-4145-b48e-ec12c1e35db4)

Now lets go over to client-1. Lets try and look at the folders we just created on dc-1. On client-1 go to start type in "run" then enter "\\dc-1" to get to get to the new folders.
![image](https://github.com/user-attachments/assets/ef71924b-75c3-4730-a4d9-1ee84e7cdca2)

If we go into the read-access folder and try and create a New folder we are not able to. The permission for our normal user is only set to Read here.
![image](https://github.com/user-attachments/assets/35c7f34f-3b0e-4a0b-bb6b-192860ddb066)

In the write-access folderif we try and make a new text document you can see we have the permissions to read and write in this folder.
![image](https://github.com/user-attachments/assets/2df68639-ba49-4a78-aa7b-f74c2ef2e325)

Now in the no-access folder we cant even open it. This is because only Admins can read and write here.
![image](https://github.com/user-attachments/assets/cef071d6-fea5-461d-8489-24a738dca5aa)

Now lets try group permissions. Back over on dc-1 pull up Active Directory Users And Computers, right click mydomain.com, go down to New> Organizational Unit and select it. We will name it "_GROUPS".
![image](https://github.com/user-attachments/assets/bb0f3334-8be1-4f21-a41d-197d8a9c3c8b)

In _GROUPS right click and go to New> Group. Name the group "ACCOUNTANTS" and select OK.
![image](https://github.com/user-attachments/assets/dc39fc4d-99a3-45fa-ae70-fdf6dab22e61)

Now lets go to the accounting folder we made. We will right clcik and go to Properties> Sharing> Share, Type ACCOUNTANTS and Add then give the Read/Write Permission level.
![image](https://github.com/user-attachments/assets/043f7203-ad35-44e6-9b1e-aff79405d3df)

Back on client-1 as our normal user in the same place where we looked at the other folders hit the refresh button at the top and you can now see the accounting folder. Try and open it. Due to the permissions our normal user can not open this. Lets log out of our user on client-1 for a moment. In dc-1 lets move our  user to the accounting group so he has access. Double clcik the ACCOUNTANTS security group> Members> Add, Then add your user, hit ok and apply
![image](https://github.com/user-attachments/assets/73c90d69-63b5-4be8-99d6-a9bb8bb7383c)
![image](https://github.com/user-attachments/assets/80caad74-1c45-4ce0-a6ec-148ce55597f6)

Lets see if we did all this correctly. Log back into client-1 as your user. Search "run" in the bottom left> enter  \\dc-1 and we are back to the folders. Lets try opening the accounting folder. As you can see we can open and write documents.
![image](https://github.com/user-attachments/assets/eb60722f-343d-4d79-aa7a-8e062581f43f)


Congratulations we have successfully set up Permissions and File Shares.

































