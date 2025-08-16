\# Lab Steps – Sinas AD-IAM Lab Research



---



\## ✅ Activity 1 – Configure Static IP on DC1



| Parameter     | Value          |

| ------------- | -------------- |

| IP Address    | 192.168.247.10 |

| Subnet Mask   | 255.255.255.0  |

| Preferred DNS | 192.168.247.10 |



\*Note: Task already completed earlier\*



---



\## ✅ Activity 2 – Promote DC1 to Domain Controller (shin.lab)



| Parameter    | Value    |

| ------------ | -------- |

| Domain FQDN  | shin.lab |

| NetBIOS Name | SHIN     |



\*Note: Task already completed earlier\*



---



\## ✅ Activity 3 – Configure Static IP on Server2



| Parameter     | Value          |

| ------------- | -------------- |

| IP Address    | 192.168.247.20 |

| Subnet Mask   | 255.255.255.0  |

| Preferred DNS | 192.168.247.10 |



---



\## ✅ Activity 4 – Join Server2 to SHIN.LAB Domain



| Action        | Details            |

| ------------- | ------------------ |

| Change Domain | shin.lab           |

| Credentials   | SHIN\\administrator |



---



\## ✅ Activity 5 – Create Organizational Units (OUs)



\*\*Objective:\*\* Organize users into logical groups.



| OU Name |

| ------- |

| HR      |

| IT      |

| Finance |



\*\*Steps:\*\*



1\. Open Active Directory Users and Computers on DC1.

2\. Right-click the domain → New → Organizational Unit → Enter OU name.



---



\## ✅ Activity 6 – Create Users for Each OU



\*\*Objective:\*\* Add users to their respective OUs.



| OU      | Username | Login Name  |

| ------- | -------- | ----------- |

| HR      | Alice    | alice.hr    |

| IT      | Bob      | bob.it      |

| Finance | Charlie  | charlie.fin |



\*\*Steps:\*\*



1\. Navigate to the OU.

2\. Right-click → New → User → Enter user details.

3\. Set password and configure “User must change password at next logon”.



---



\## ✅ Activity 7 – Create Security Groups and Add Users



\*\*Objective:\*\* Group users for permission management.



| OU      | Group Name    | Members |

| ------- | ------------- | ------- |

| HR      | HR\\\_Team      | Alice   |

| IT      | IT\\\_Team      | Bob     |

| Finance | Finance\\\_Team | Charlie |



\*\*Steps:\*\*



1\. Navigate to the domain or OU.

2\. Right-click → New → Group → Enter group details.

3\. Add users: Right-click group → Properties → Members → Add → Enter usernames → OK.



---



\## ✅ Activity 8 – Configure Group Policies (GPOs)



\*\*Objective:\*\* Apply policies for users in each OU.



\*\*Steps:\*\*



1\. Open Group Policy Management (gpmc.msc).

2\. Create new GPO → Name it (e.g., HR\\\_Policy).

3\. Edit GPO to configure policies:



&nbsp;  \* Password policies: Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Password Policy

&nbsp;  \* Logon scripts: User Configuration → Windows Settings → Scripts (Logon/Logoff)

&nbsp;  \* Desktop restrictions: User Configuration → Administrative Templates → Desktop

4\. Link GPO to OU: Right-click OU → Link an Existing GPO → Select GPO → OK.

5\. Verify: Log in as a user from the OU → `gpupdate /force` → Confirm policy applied.



---



\## ✅ Activity 9 – Delegate OU Permissions



\*\*Objective:\*\* Delegate specific administrative tasks without giving full domain privileges.



| Step | Action                                                                                                             |

| ---- | ------------------------------------------------------------------------------------------------------------------ |

| 1    | Open Active Directory Users and Computers                                                                          |

| 2    | Navigate to the OU (e.g., HR)                                                                                      |

| 3    | Right-click OU → Delegate Control…                                                                                 |

| 4    | Click Next on Welcome screen                                                                                       |

| 5    | Click Add → Enter user/group (e.g., Alice or HR\\\_Team) → OK → Next                                                 |

| 6    | Select common tasks → Create, delete, and manage user accounts → Next → Finish                                     |

| 7    | Verify: Log in as delegated user → Open ADUC → Try creating user in delegated OU → Confirm cannot modify other OUs |



\*\*Summary:\*\*



\* OU permissions allow fine-grained control over administrative tasks.

\* Delegation enforces least privilege in Active Directory.



