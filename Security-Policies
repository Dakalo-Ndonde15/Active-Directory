# Security Policies

## Objective
  
Understand and implement essential security measures in our work place.

### Skills Learned

- Password Policy: Configure and enforce a strong password policy for AD users
- Account Lockout Policy: Configure an account lockout policy to protect against brute-force attacks
- User Rights Assignment: Assign and restrict user rights to enhance security (i.e. job roles)
- Implementing Fine-Grained Password Policies: Apply different password policies to different groups of users (Active Directory Administrative Center)

### Tools Used

- VMware Workstation Pro 17
- Windows Server 2022
- Windows 10 Enterprise

## Steps

*Ref 1: Configure and enforce a strong password policy for AD users with the criteria: Minimum password length, password complexity, and password age. Previously, Windows Server minimum password length is 8 characters but a new password policy was implemented in Aug 2021. After the policy change, the required minimum password length is 12 characters or more. Open Group Policy Management Console (GPMC) on our VM server*

![image](https://github.com/user-attachments/assets/97120575-c162-40cb-8c2b-8df144978072)

*Ref 2: Right click on "Default Domain Policy" to apply the policy to all AD users in the domain*

![image](https://github.com/user-attachments/assets/67750ccc-cdfb-4e80-8f88-5b202dbb34c1)

*Ref 3: Computer Config > Policies > Windows Settings > Security Settings > Account Policies > Password Policy to change the minimum password length, password complexity, and password age*

![image](https://github.com/user-attachments/assets/712de7f8-23ce-426b-bc64-55e9bac055af)

*Ref 4: Update the password policy to reflect the requirements but this could vary between company to company so always comply to the company policy*

![image](https://github.com/user-attachments/assets/d58be859-4866-4456-8493-6f986668c01b)

*Ref 5: Testing to see if the policy has been apply correctly to the new user 'Kim Chi' on Asia's User GPO. It shows that it works when we try to use 123456 as a password*

![image](https://github.com/user-attachments/assets/6605840b-a673-486c-b0e9-6b049ca0ab5b)

*Ref 6: Configuring an account lockout policy to protect against brute-force attacks by including password threshold and password lockout duration. Default Domain Policy > Computer Config > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy*

![image](https://github.com/user-attachments/assets/23db3b91-9e98-426a-9b6e-8338d31614d5)

*Ref 7: Updating the Account lockout duration to 30 minutes, threshold to 3 and reset account lockout counter after to 30 minutes. The account lockout threshold is set to 3 for this example but once again follow your company policy for their recommended lockout threshold*

![image](https://github.com/user-attachments/assets/a60d1add-3aa5-4bf2-885d-8b028feed9c8)

*Ref 8: Account lockout policy was successfuly implemented on the users*

![image](https://github.com/user-attachments/assets/67a4b92c-2e40-4130-ba36-8471a2e00102)

*Ref 9: Create a new GPO and name it "User Rights"*

![image](https://github.com/user-attachments/assets/eafb68df-7936-424f-93c6-db3d9e413da0)

*Ref 10: Users Rights > Computer Config > Windows Settings > Security Settings > Local Policies > User Rights Assignment

![image](https://github.com/user-attachments/assets/bc7dadc6-46ba-45c9-8fa6-c6e67ec42ee5)

*Ref 11: Applying "deny log on locally" to users in HR as an example*

![image](https://github.com/user-attachments/assets/6797d175-d259-4fdc-8948-2a23b96df807)

*Ref 12: Applying "allow log on through remote desktop services" to users in IT as an example*

![image](https://github.com/user-attachments/assets/6fe93856-47ad-406d-96c2-81688d6362be)

*Ref 13: Attempting to log in on the server with an non-admin user account and it fails meaning the policy is implemented correctly*

![image](https://github.com/user-attachments/assets/3882c005-e376-4555-8667-d722d704851f)

*Ref 14: Applying different password pollices to different groups of users. i.e. the organization wants to apply sricter password policies to administrative accounts while allowing standard users to have less stringent requirements. Under Active Directory Administrative 
Center, click on the server name > system > password settings container*

![image](https://github.com/user-attachments/assets/3bb0e470-e75d-452d-a972-de1e4a5857b8)

*Ref 15: Under password settings container, go to new > password settings

![image](https://github.com/user-attachments/assets/8e49f599-4dc9-4677-a237-16ee726ea8a7)

*Ref 16: Setting up Admin password policy first. Naming the setting "AdminPasswordPolicy" and giving it a Precedence of 1 (the lower the number the higher the priorty it will be applied). Adding group "IT" to get implemented*

![image](https://github.com/user-attachments/assets/2d60aa79-0458-4bbf-9088-655a81ea7e53)

*Ref 17: Do the same for user passwords but set their precedence with a number higher than 1, apply it to standard users in your organization*

![image](https://github.com/user-attachments/assets/07116dcf-484b-4dbf-be90-38b17faa0780)
