### Sharing Files on a Network: Shared VS NTSF

### Objective
  
Setting up network sharing on Windows Servers allows users and devices to securely access and share files, folders, and resources over a network. It helps streamline collaboration, improve accessibility, and enforce permissions for controlled data access.

### Skills Learned

- Set up a file sharing: create shared folders with appropriate permissions and set NTFS and share permissions to allow domain users access
- Set up client machines: map network drives to access shared folders
- GPO Configuration: configure GPOs to automatically map network drives for users
- Implement quotas and file screening using File Server Resource Manager (FSRM): configure FRSM to create Quota Template and File Screen Template to effectively manage File Storage in your organization
- Understanding the different types of file sharing (local, network, and domain-based)
- Learning how to assign permissions for specific user scenarios, such as restricting access for temporary staff.
- Understanding explicit and inherited permissions and how they affect access.

### Tools Used

- VMware Workstation Pro
- Windows Server 2022
- File Server Resource Manager

### Content
- [Sharing files on a network with SHARED Permission](#Sharing-files-on-a-network-with-SHARED-Permission)
- [Sharing files on a network with NTSF Permission](#Sharing-files-on-a-network-with-NTSF-Permission)

### Sharing files on a network with SHARED Permission 

*Ref 1: Setting up File Services*

![image](https://github.com/user-attachments/assets/63225de4-6851-4bf2-9799-aef6fcb31ad6)

*Ref 2: Creating a new folder under local disk (C:) on our server and labeling it "SHARED".*

![image](https://github.com/user-attachments/assets/5eab0fe2-c06a-4d83-911e-63a5468c83b7)

*Ref 3: Right click SHARED folder, go to "sharing" tab, click the box for "share this folder", then click "add" and type in domain in the field. From there "check name" then look for "domain users" and click on it. From there you should see Domain Users under share permissions. Click apply and okay on all the open tabs to apply the settings.*

![image](https://github.com/user-attachments/assets/29408179-c644-4bcd-922b-f6939f01756b)

*Ref 4: Under the "security" tab you can give permissions to a single user or a group depending on the needs of the company or job role.*

![image](https://github.com/user-attachments/assets/69b0626e-85fc-48f2-b2ca-9a85db9ae0ca)

*Ref 5: Set up Client Machines.*

![image](https://github.com/user-attachments/assets/0a9dc45c-ba97-4fdf-93b6-686067dd0e90)

*Ref 6: On client's machine we set up map network drive by right clicking on "this pc" then going to map network drive. From there select a drive you'll want but in this case I selected "S:" for our drive. Under folder, type in your server name and the shared folder. i.e. \\WIN-0G53M1M70MV\SHARED. Don't forget to uncheck "reconnect at sign-in".*

![image](https://github.com/user-attachments/assets/9c22a900-833c-4c54-89a6-49ddba178203)

*Ref 7: Once the task is completed you should see your SHARED file under "network locations".*

![image](https://github.com/user-attachments/assets/1b7cf044-51e3-4ce7-a01f-3c88e0c99f00)

*Ref 8*: Configure GPOs to automatically map network drives for users* 

This process is better if the user needs constant access to the network shared folder. The pervious implemenation is suitable if the user needs to access the folder on one specific day.

![image](https://github.com/user-attachments/assets/5ae2f48d-39dc-484a-8b95-eb46bc052f5b)

*Ref 9: Back on our server, we open up the GPO task window and from there right click on "Group Policy Objects" folderr to create a new GPO folder and naming it "Mapped Drives".*

![image](https://github.com/user-attachments/assets/3027f689-9ed7-4fe5-9fc9-896dacc52725)

*Ref 10: Right click on the "Mapped Drives" folder and click edit. Then User Configuration->Windows Settings->Drive Map->New->Mapped Drive.*

![image](https://github.com/user-attachments/assets/73a1e0a0-7a43-4679-9599-ef1757491ad5)

*Ref 11: For location, you'll want to enter your \\server\share i.e. \\WIN-0G53M1M70MV\SHARED. Label as "SHARED" and change the drive to S:, for simplicity. CLick apply and okay.*

![image](https://github.com/user-attachments/assets/ce030be0-f95c-44dd-b261-4e0955785e2f)

*Ref 12: Click and drag your new Mapped Drives GPO into the user folder to apply it.*

![image](https://github.com/user-attachments/assets/a9869242-eeb0-4278-8bac-7f082a11c948)

*Ref 13: Going back to the the client machhine to test if the map drive GPO is applied correctly. Since it didn't show up we need to force the update from the command prompt*

![image](https://github.com/user-attachments/assets/79d50060-39f5-4e7a-b597-f6cea64f8ce7)

*Ref 14: Using the command "gpupdate /force" in the command prompt to force the update*

![image](https://github.com/user-attachments/assets/1c61f371-cc16-48e7-9565-3fa4345c7f6e)

*Ref 15: Once the update is complete, go ahead and restart the computer to see if the update has been applied and we can see the map drive under shared network*

![image](https://github.com/user-attachments/assets/5b26cfaf-4f83-4bd4-830d-dbdf2552df62)

*Ref 16: Map drive GPO was successfully implemented on client's machine and it'll remain there even after rebooting*

![image](https://github.com/user-attachments/assets/60b9f382-899f-461c-995d-ebb24343f996)

*Ref 17: Activity 4: Implementing quotas and file screening using File Server Resource Manager (FSRM)* 

![image](https://github.com/user-attachments/assets/46918186-9b6e-48c6-b552-850ea9b75c69)

*Ref 18: Go to server manager to add the new role "File Server Resource Manager Tools"*

![image](https://github.com/user-attachments/assets/62fe2d15-e195-435a-8fc7-ab482f39dab4)

*Ref 19: File Server Resource Mananger Tool installed*

![image](https://github.com/user-attachments/assets/91c2463c-0ae8-48a4-bc59-38e5ef5687c1)

*Ref 20: Applying a quota on the SHARED folder. Best practice to set a quota on the file storage so users do not go over it. Buying extra storage gets expensive if its done every year.*

![image](https://github.com/user-attachments/assets/db428948-ff09-4e35-8cd3-6924e092c3ba)

*Ref 21: Setting up an alert on storage usage at 80%. Once it gets close to it, an email will be sent out to the admin let them know that a specific user just past the threshold and needs to remove files before hitting their storage limit*

![image](https://github.com/user-attachments/assets/c45b22f3-cd56-40ee-a8ca-182038960799)

*Ref 22: Creating File Screen for SHARED folder so that users cannot store any files types that could fill up their folders quickly, i.e. pictures, audio, or video files. Click on custom properties and from there you can choose what files to block*

![image](https://github.com/user-attachments/assets/11913177-0b30-42b6-9470-9dd1a66ceef2)

*Ref 23: Can also create a templete of the file screen for the folder*

![image](https://github.com/user-attachments/assets/066e0de7-44ed-4b5a-9d62-c26b237d8872)

### Sharing Files with NTFS Permission

## Hands-on activity 1

*Ref 24-27: Setting up the NTFS Permissions*

If we go back to the Marketing "properties" tab and go to "security" tab to find the NTFS permissions. As you can see there's more permissions in here compared to sharing earlier. There's full control, modify, read & execute, list folder content, read, write and special permissions. There are also different groups that you can add for this permission. Since the marketing interns are not added into the NTFS permissions yet, we are going to edit that. Click "edit" then we can add the marketing interns group because we want to set particular permissions for only view and not modify or delete files for the marketing intern. So if we go down the list of permissions, by default, read & execute, list folder contents nad read permissions are allowed. We only want to allow read permissions so we deselect the other two permissions click apply > OK. Afterwards if you click on the "Marketing Intern" group and look at their permissions, "read-only" should be only permission available. That's how you change the NTSF for a specific shared folder.

![image](https://github.com/user-attachments/assets/38acde8c-9809-4d5b-8630-23cbe9509a50)

![image](https://github.com/user-attachments/assets/53702051-e556-493c-bac9-d6cd6234a130)

![image](https://github.com/user-attachments/assets/1f29726e-25df-47bf-99a7-61c9d8968b4c)

![image](https://github.com/user-attachments/assets/9281c08d-c456-445f-bcc9-aa1032948a07)

## Hands-on activty 2

*Ref 28-33: Setting up SHARE and NTFS for group*

The HR Department needs a secure folder HRGroup that only HR staff can access. Other employees should not see the folder at all. *Go to your windows server > right click the HRGroup folder > properties > advanced sharing > "click on share this folder"*. From here we notice that anyone has permission to view and edit the folders in the HRGroup. We only want HR employees to see it, not everyone, *so we click on "everyone" > remove > add > add HRGroup > OK > give them "full control" under permission > apply*. So now only HR has permission to see their folders. Once we get out of the "sharing" tab and go to "security" we notice that the NTFS permission has not been set up for the HR Group. If we click on user we can see that they only have read and execute and read list folder contents permissions in here so we also want to adjust the NTFS permissions for HR even if we already gave them full control in here and the shared permissions once they get into the sub folders and files under the HR Group they wont be able to do much but to just view the files because they don't have enough permissions in this NTFS level. So let's add them, *click "users" > edit > add HR Group > Apply > OK*. Afterwards we click on "full control" under permission to give them full control in the NTFS level.

![image](https://github.com/user-attachments/assets/3c16d841-db4e-40c0-954d-6e013a8b23b4)

![image](https://github.com/user-attachments/assets/9939243a-584c-47af-95bc-5535bdd97c6d)

![image](https://github.com/user-attachments/assets/e1fefa34-8432-4196-8ca0-6d3ebfc55b8f)

![image](https://github.com/user-attachments/assets/6dc05233-668d-4a2b-af13-a19cdadd1a47)

![image](https://github.com/user-attachments/assets/7b00558e-a991-48d1-8f18-ddfaccc103ce)

![image](https://github.com/user-attachments/assets/27918c62-a9a8-4f23-983d-addcc2ce9d41)

## Hands-on activity 3

*Ref 34-37: Setting up SHARE and NTFS for Third Party Vendor*

A third-party vendor needs access to a temporary folder VendorFiles to upload reports but should not see other files. *Click on VendorFiles > Sharing > "Share this folder" > Permissions > Add > Type in their name > Full Control*. Third party vendor needs access to the folder vendor files to upload reports but should not see other files so this is the only folder that vendor need to see. Next we allow full control for the vendors on this shared permissions because they want to be able to upload and get to the other files under this shared folder. Now we go to the NTFS permission. Like before *Security > Edit > Add the vendor > Unclick all permissions except for write*. Going back to the activity, we're only allowing the vendors to upload reports. That's why we removed all the other permissions except for write so they can only upload files and not see the others. 

![image](https://github.com/user-attachments/assets/5309c2db-5e15-4aed-b547-e5c273fd231d)

![image](https://github.com/user-attachments/assets/5746bc8e-43ac-4ed3-abc2-8b63ed215420)

![image](https://github.com/user-attachments/assets/fb5f8a75-50da-4248-a648-4af6e64b7fc5)

![image](https://github.com/user-attachments/assets/164c8eaa-a32d-4b5b-897a-810394485867)

## Hands-on activity 4

*Ref 38: Setting up SHARE and NTFS for IT and Senior IT*

In the IT Department, all techs need accesss to the Softare Repoository Software but only senior IT staff should be able to access the "Licenses" subfolder. *Software > Sharing > Permissions > Add > IT > Apply > give them Full control permission*. Similar steps as we've done in the previous activities to give SHARED permissions to a specific role to get access. The second part to the activity is to only allow access to the "Licenses" subfolder to senior IT. Adjust the subfolders permissions in here to only allwo the senior IT to access this so we have to change the NTFS permissions on this because it's a sub folder and we are only applying a certain permission on just this subfolder. This is were we can add the senior IT access in here, first we need to disable inheritance from this folder and set explict permissions to explicitly give the senior IT permissions to access this sub folder. *Right click on License > properties > security > advanced > disable inheritance > remove all inheritance > apply*. After this step you can see in here that it's denying all the users access to the licenses here. Next we're going to add the senior IT so they have explicit permission to aaccess this folder so no one can access this folder but the owner. *Security > Permissions > Edit > Add > Senior IT*. 

![image](https://github.com/user-attachments/assets/686c0a95-2194-4746-9ea6-e1cbe0a20d9c)

![image](https://github.com/user-attachments/assets/3bb03feb-157b-41cb-9f4f-0cf1d57c5a3a)

![image](https://github.com/user-attachments/assets/545e77cd-7130-4fda-8dbf-6a8953b570a1)

![image](https://github.com/user-attachments/assets/ee73e895-7bb1-4069-87cf-b16332c5aba9)
