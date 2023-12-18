<div align="center">

# Project Overview
In this guided project, the goal is to apply hands-on practice to accurately and confidently perform the tasks required to implement and maintain Entra ID. This project is meant to give an understanding of how to:
<li>Create users and groups</li>
<li>Assign users to groups</li>
<li>Configure Self-Service Password Reset (SSPR)</li>
<li>Configure and customize Conditional Access and Privilege Identity Management (PIM)</li>
<li>Monitor Identity Secure Score</li>

## Create users and groups
Go to the Microsoft Entra admin center (entra.microsoft.com). Navigate to the side menu, under Identity, select Users, then All users. Next, add a user by clicking New user and Create new user in the command bar.

![1](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/6f5d2744-26e4-4b8d-b262-f28f5eadb010)

In the following page, fill in the Principal name of the user (gpuser1) and (if needed) select the right domain name. Then fill in the Display name (GP User1), uncheck the Auto-generate password checkbox, and fill in the Password field. Continue by clicking Next: Properties.

![2](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/5304039a-e255-46fa-b74e-e71c913ce673)

On the properties page, information can be filled in, such as the department the new user belongs to. For this guided project, this step will be skipped. Continue by clicking Next: Assignments. Assignments can be used to add users to an already active group. A group will be created and added later. It is also possible to assign a role to the user on this page. Click Add role and select the Application Administrator role for this user.

![3](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/66bfa83a-a31f-4e8e-a4d0-39eed096dde6)

Click Next: Review + create, followed by Create. The new user might not automatically appear in the user list. Click Refresh in the command bar and monitor that the user is successfully added to the list.

![4](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/7947935c-cc16-4f17-af85-1450ef458788)

Follow the same steps to add another user (GP User2) with the role of Application Developer.

![5](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/c594c9a3-5b85-4fa6-86f8-006773d65d89)

Click on GP User1 and notice the full domain address for this user. This can be used to log in to the user account. Validate that you can log in with the user you’ve created.

![6](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/456dd1b3-2725-44ed-9577-6fde3240de53)

## Assign users to groups
Navigate to the side menu, under Identity, select Groups, then All groups. Click New group in the command bar. Select the Group type (Security), fill in the Group name (GPSecurityGroup), and leave roles assigned to the group on No. For the Membership type, select Assigned. Info: a Dynamic User can use user properties to decide which users are assigned to the group. Under Members, click No members selected. Search for GP User and select GP User1 and GP User2. Click Select and then Create.

![7](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/0ab1c1d3-c1f0-4cc7-bdc4-8d2ffef56350)

Click Refresh in the command bar if the newly created group is not automatically showing.

![8](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/cb3f4e38-ce37-44c1-a201-026f989e8e07)

Create another group by clicking New group in the command bar. This time, select the Group type Microsoft 365. Fill in the Group name (GPM365Group). By default, a Group email address is created. Leave all other options as default. Under Members, click No members selected.

![9](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/dd5598fd-bd18-44ed-8f69-8eb7f206c8ee)

Search for “gpuser” and select GP User1 and GP User2. Continue by clicking Select and Create. Click Refresh in the command bar to monitor that the group is created successfully.

## Configure Self-Service Password Reset (SSPR)
Navigate to the side menu, under Identity, select Groups, then All groups. Select New group from the command bar. For the Group type, select Security. Fill in the Group name (GPSSPR) and keep all other options as default. Click the No members selected link, search for “gpuser” and select the two users (GP User1 & GP User2). Click Select and Create.

![10](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/871e3817-8979-42a7-b7c1-6242afc21f83)

Click Refresh in the command bar if the group is not automatically loaded. Next, navigate to the side menu, under Identity, select Users, then User settings. Under Manage, select Password reset. In the Properties tab, set Self-service password reset enabled to Selected. Click the No groups selected link, select the GPSSPR group and click Save.

![11](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/044bb890-9a9e-42a8-af84-11de894d089b)

One final thing to check is under Manage, click Authentication methods. Here, you can select the Number of methods required to reset as well as the Methods available to the users.

![12](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/16734e8c-8896-4a06-ae53-a8d398e64dc0)

## Configure Conditional Access
Conditional access sets the requirements that need to be met before a user is granted access. To configure this, navigate to the side menu, under Protection, select Conditional Access, then select Create new policy in the command bar.

![13](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/23adfcc3-a424-4421-8f03-e5253f49d867)

If security defaults are enabled, a warning message will be shown at the bottom of the screen. These defaults are already set in place to provide a minimum of protection but are not sufficient. Click on the link in the error message.

![14](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/0c00585e-e8c9-4f9c-abde-aed92e4b4dbc)

In the Security defaults window, set the Security defaults to Disabled. As for the reason, check My organization is using Conditional Access. Click Save followed by the Disable button.

![15](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/d2dbabcc-bd3c-40c9-b9fe-d363e444341b)

Back in the Conditional Access policy page, fill in the name (GP CA Policy). Under Users, click on the link Specific users included. Under Include, check Select users and groups, then Users and groups. Search for “gpuser” if needed and select GP User2 followed by Select.

![16](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/90720aaf-43c7-4eb8-b263-0ef8d948dee4)

Under Target resources, click the link No target resources selected. If needed, Select what this policy applies to, to Cloud apps. Under Include, mark Select apps. Under Select, click the None link. Search for and Select “Microsoft Azure Management”.

![17](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/615576a7-fd63-4df1-b4f1-30bc280d69ae)

Under Conditions, click on the link 0 conditions selected. Monitor the available options / conditions that can be used. However, we will not use any of these for this project. Under Access controls and Grant, click on the 0 controls selected link. In the Grant window, select Block access.

![18](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/17744806-7d25-463f-bd9e-83756df9aea2)

Then, set Enable policy to On and click Create. GP User2 will now be denied access to the Azure portal.

## Configure Privileged Identity Management (PIM)
PIM allows users to request a role for a limited period of time. Each role can be configured for a specific period of time. In this task, we verify the settings for the Azure DevOps Administrator role and allow GP User1 to request access to this role. To be able to do this, the user will need to have a Microsoft Entra ID P2 license assigned.

Navigate to the side menu, under Identity Governance, select Privileged Identity Management. Then, under Manage, select Azure AD roles. In the Default Directory, under Manage, select Settings. Search for and select “Azure DevOps Administrator”.

![19](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/c2823198-edbe-4938-9f1d-f33d06aec86d)

Here, each role can be configured with specific activation, assignment, and notification requirements. We want our primary user account to approve any requests for this role assignment. Click Edit in the command bar to continue. Select the Require approval to activate checkbox. Click on the + next to No approver selected, select the primary or admin user and click the Update button.

![20](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/14497679-b6d2-426b-89b1-c89e6f2a4265)

Back in the Default Directory, under Manage, select Roles. In the command bar, select Add assignments. Click on Select role, search and select Azure DevOps Administrator. Under Select members, click on the No members selected link. Select the checkbox for GP User1 and click the Next button.

![21](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/1133e9b3-2616-4c5c-8a4d-5ecf401bfb47)

In the Settings tab, keep Assignment type on Eligible (default) and click the Assign button.

Test this by logging in with GP User1 to see if they can request this role. To do this, as user GP User1, navigate to the side menu, under Identity governance, select Privileged Identity Management. Then, under Tasks, select My roles. In the Active assignments tab, the user can see their current role.

![22](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/e956d2d0-b30c-46c5-8ee4-04289b40e9f3)

In the Eligible assignments tab, the user can request a different role assignment. 

![23](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/06f36af4-2e8c-40e2-af56-f19129a21162)

The user can specify the duration (default maximum of 8 hours) and provide a reason for requesting the access. As soon as the user clicks on the Activate button, the request is sent to the primary / admin user pending approval. Back in the primary user account, navigate to the side menu, under Identity governance, select Privileged Identity Management. Next, under Tasks, select Approve requests. The request from GP User1 will be awaiting approval.

![24](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/bb098ee1-7232-451d-b908-ab9b7e25f20d)

## Monitor Identity Secure Score
The identity secure score provides an overall score and improvement actions for the identity security posture. It is important to review and implement recommendations for your Azure environment. To do this, navigate to the side menu, under Protection, click Show more, then select Identity Secure Score.

![25](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/cd2b9197-ada2-41f2-ab44-64b4b76fb645)

Under Improvement actions, you can see, select and implement any Improvement action to continue improving the identity security posture.

![26](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/1d5c2b47-57df-4319-bffa-b29087ca4e9a)

## Remove created users
Navigate to the side menu, under Identity, click on Users and select All users. Select the checkbox of the users you want to delete. In the command bar, select Delete.

![27](https://github.com/GeoffreyMorren/Microsoft-Entra/assets/152500568/4e5c694c-6aa2-4685-b346-fbbcf59bf194)

</div>
