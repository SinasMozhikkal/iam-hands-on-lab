\# Lab Steps – Sinas AD-IAM Lab Research



---



\## ✅ Activity 1 – Configure Static IP on DC1



(No screenshot – task already completed earlier)



IP Address : 192.168.247.10

Subnet Mask : 255.255.255.0

Preferred DNS : 192.168.247.10



---



\## ✅ Activity 2 – Promote DC1 to Domain Controller (shin.lab)



(No screenshot – task already completed earlier)



Domain FQDN : shin.lab

NetBIOS Name : SHIN

---



\## ✅ Activity 3 – Configure Static IP on Server2



IP Address : 192.168.247.20

Subnet Mask : 255.255.255.0

Preferred DNS : 192.168.247.10



---



\## ✅ Activity 4 – Join Server2 to SHIN.LAB Domain



System Properties → Change → Domain: shin.lab

Credentials used : SHIN\\administrator



✅ Activity 5 – Create Organizational Units (OUs)



Objective: Organize users into logical groups for easier management.



Steps:



Open Active Directory Users and Computers on DC1.



Right-click your domain (shin.lab) → New → Organizational Unit.



Create the following OUs:



* HR
* IT
* Finance



Created OUs:

HR

IT

Finance



✅ Activity 6 – Create Users for Each OU



Objective: Add users to their respective OUs.



Steps:



Navigate to each OU in Active Directory Users and Computers.



Right-click the OU → New → User.



Enter the following details:

| OU      | Username | Login Name  |

| ------- | -------- | ----------- |

| HR      | Alice    | alice.hr    |

| IT      | Bob      | bob.it      |

| Finance | Charlie  | charlie.fin |





Set passwords and configure “User must change password at next logon” as needed.



✅ Activity 7 – Create Security Groups and Add Users



Objective: Group users for permissions management.



Steps:



1. Open Active Directory Users and Computers.
2. Navigate to the domain or relevant OU.
3. Right-click → New → Group.
4. Configure groups as follows:

| OU      | Group Name    | Members |

| ------- | ------------- | ------- |

| HR      | HR\\\_Team      | Alice   |

| IT      | IT\\\_Team      | Bob     |

| Finance | Finance\\\_Team | Charlie |

5.Add users to the groups: Right-click the group → Properties → Members → Add → Enter usernames → OK.



✅ Activity 8 – Configure Group Policies (GPOs)



Objective: Apply policies to control settings for users in each OU.



Steps:

1. Open Group Policy Management (gpmc.msc).
2. Right-click Group Policy Objects → New → Name the GPO (e.g., HR\_Policy).
3. Right-click the GPO → Edit → Configure policies as needed:

* Password policies: Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Password Policy
* Logon scripts: User Configuration → Windows Settings → Scripts (Logon/Logoff)
* Desktop restrictions: User Configuration → Administrative Templates → Desktop



1. Link the GPO to the corresponding OU: Right-click OU → Link an Existing GPO → Select the GPO → OK.
2. Verify: Log in as a user from that OU, run gpupdate /force and check that the policy applies.
