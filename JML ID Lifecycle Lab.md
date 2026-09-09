
## Overview + Objectives

In this lab I will be demonstrating the entire Joiner, Mover, and Leaver identity lifecycle process using Microsoft Entra ID. 

The lab follows an employee through three stages:

Joiner: New employee is onboarded and receives appropriate access.
Mover: Employee changes roles and their access is automatically adjusted.
Leaver: Employee leaves the organization and their access is revoked.


#### Environment 

Identity Platform: Microsoft Entra ID
Organization: Test Server Industries
User: John Carter
Initial Role: IT Help Desk Technician
New Role: Junior Systems Administrator


#### Scenario

Test Server Industries hires **John Carter** as an IT Help Desk Technician.

As part of the onboarding process, John requires:

- A Microsoft Entra ID account
- IT access
- VPN access

Several months later, John is promoted to **Junior Systems Administrator**. His access must be updated to reflect his new responsibilities.

Later, John leaves the company. His account must be disabled and his organizational access revoked.

The goal is to manage John's identity throughout the complete employee lifecycle.


### JOINER - Employee Onboarding

We are going to create John's company identiy and provide the right access that is required for his initial Help Desk position.

#### Step 1 - Creating the User

1. I Navigated to Microsoft Entra admin center → Identity → Users → All users → New user then created the following account with these attributes: 

Display Name: John Carter 
User Principal Name: john.carter@testserverindustries.onmicrosoft.com
Job Title: IT Help Desk Technician 
Department: IT

![1]

#### Step 2 - Verify Dynamic IT Membership

The IT security group already has the group rule: 
user.department -eq "IT"

1. Navigated to Groups > IT > Members > Verified that John Carter appears as a member.

[2]


#### Step 3 - Assign VPN Access 

We are now going to give John VPN access by adding him to the security group that grants it which would be "VPN-Access"

1. Navigated to Users > John Carter > Groups > Add memberships > Select: VPN-Access which adds John to the group. 

![3]


### MOVER - Employee Role Change 

John is now promoted Junior System Administrator and needs his role changed. Make sure that the Junior System Admin role actually exists as a Security Group first. 

#### Step 4 - Changing Roles

1. I navigated to Users > John Carter > Properties. 

Updated to: 

Job Title: Junior System Administrator
Department: Jr. System Administrator

2. Save the changes and review.

![4]


#### Step 5 - Verify Updated Access 

If the dynamic group was setup correctly then John's access should be updated to reflect teh IT-SysAdmins due to the Jr. Sys admin attribute in the department section of his identity profile. 

![5]

John's access now reflect his new job responsibilities. This is also demonstrating least privilege by not giving him more access than his role requires which is very important. 



### LEAVER - Employee Offboarding

John's time with the company has now officially ended and its time to offboard him, terminate his access and disable his accounts. 

#### Step 6 - Block Sign-ins 

1. Navigated to Users > John Carter > Properties
2. Uncheck Account enabled to prevent from signing in altogether. 

![6]


#### Step 7 - Revoke Active Sessions

1. Navigated to Johns account and selected "Revoke Sessions"

![7]

#### Step 8 - Verify Offboarding

Double checked and confirmed that John Carter's access is stripped and not assigned to any security groups and contain no other attributes related to his previous roles.

![8]

## Summary

This lab demonstrated the complete Joiner, Mover and Leaver identity lifecycle using Entra ID. 

We showed the process when he was provisioned access upon his employment, had his access updated, then ultimately removed once he was no longer a part of the company. 

This is a very simplified version of the ID lifecycle process in a potential enterprise environment. 

[1]:https://github.com/DON-CYR/JML-Identity-Lifecycle-Lab/blob/main/images/sc_1.png
[2]:https://github.com/DON-CYR/JML-Identity-Lifecycle-Lab/blob/main/images/sc_2.png
[3]:https://github.com/DON-CYR/JML-Identity-Lifecycle-Lab/blob/main/images/sc_3.png
[4]:https://github.com/DON-CYR/JML-Identity-Lifecycle-Lab/blob/main/images/sc_4.png
[5]:https://github.com/DON-CYR/JML-Identity-Lifecycle-Lab/blob/main/images/sc_5.png
[6]:https://github.com/DON-CYR/JML-Identity-Lifecycle-Lab/blob/main/images/sc_6.png
[7]:https://github.com/DON-CYR/JML-Identity-Lifecycle-Lab/blob/main/images/sc_7.png
[8]:https://github.com/DON-CYR/JML-Identity-Lifecycle-Lab/blob/main/images/sc_8.png
