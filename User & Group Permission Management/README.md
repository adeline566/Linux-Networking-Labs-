                                        User & Group Permission Management LAB

This lab demonstrates hands-on experience with Linux user and group management, directory permissions, umask configuration, SGID, and sticky bit behavior. The tasks were completed in a CCIA environment and reflect practical system administration. 



# Task A: Account and Group Setup


### Step 1: Create Groups
Three groups were created:

employee

payroll

admin

<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/f80a955f-13be-4a83-baa3-afcc43c29523" />




# Step 2: Create User Accounts
Three user accounts were created with specified home directories:

Sophia – primary group: employee

Olivia – primary group: payroll

Emma – primary group: admin

All users were assigned /bin/bash as their login shell and passwords were configured.


<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/ea457134-4737-45fd-9588-7470873a3de7" />

<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/b6acfaa3-6467-4a30-afd7-4cdd5838f85c" />



# Step 3: Create Shared Group
A shared group named your_midas (MIDAS ID placeholder) was created and added as a secondary group for Sophia, Olivia, and Emma. Group memberships were verified for each user.

<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/eabd740c-44c4-4c70-96b9-6f058ee1e9b6" />



# Step 4: Create Shared Directory
A shared directory /home/cyse_project was created and assigned ownership to the your_midas group. Directory ownership and permissions were verified.


<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/7ebeb90c-fb45-477e-8a73-8d8c4d82ba68" />


# Step 5: Set Directory Permissions
Permissions for /home/cyse_project were set to rwxrwx--- using the octal method, ensuring that only members of the shared group could access the directory.


<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/be27018f-b6d9-4ec3-8434-2fa8cd44ad52" />


# Step 6: Configure Default Permissions (umask)
The system switched to Sophia’s account. The default permissions were modified using the umask command so that newly created files had permissions of rw-r-----. The umask value and file permissions were verified.


<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/72703fb6-d1c3-41f7-b70f-72d824992d50" />



# Step 7: Create File
A file named Sophia_homework was created in Sophia’s home directory with the student’s name as content. File contents and permissions were verified using ls -l.


<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/182e5d61-b5d4-4db4-8c32-ed8a07056676" />


# Step 8: Copy File to Shared Directory
The file Sophia_homework was copied to /home/cyse_project, and file permissions in the shared directory were verified.


<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/be0e2956-e8bc-46bd-91c8-1883ceafc0ca" />



# Step 9: Access Test (Emma)
The system switched to Emma’s account to test read access to Sophia_homework in the shared directory.

<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/a21f360f-a866-4508-9c0d-9a1c250785ab" />



# Step 10: Exit User Accounts
Exited Emma’s and Sophia’s accounts.


<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/7020846a-8e22-47a0-98c2-0b341858eea1" />



# Task B: SGID Permission Configuration

# Step 1: Set SGID on Shared Directory
The SGID permission was set on /home/cyse_project to ensure that files created within the directory inherit the group ownership.


<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/f92952c3-c445-4b7e-aed1-edf7ae04010c" />


# Step 2: Copy File with SGID Enabled
Under Sophia’s account, Sophia_homework was copied to the shared directory as Sophia_homework2.

<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/a743276d-c56b-4de0-96ac-c6d83b6c82ad" />

# Step 3: Access Test (Emma)
Emma’s account was used to test read access to Sophia_homework2, confirming correct SGID behavior.


<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/91cda201-9737-45e5-ad32-515d87e583f0" />


# Task C: Remove SGID Permissions

# Step 1: Unset SGID and Restrict Group Access
SGID permissions were removed from /home/cyse_project, and group read access was restricted.

<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/024ed471-b340-47dd-8708-3e6d29cc2f8c" />


# Step 2: Copy File After SGID Removal
Sophia copied Sophia_homework to the shared directory as Sophia_homework3.


<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/cb54b368-1200-4b6f-8d33-4d6e68a4b466" />


# Step 3: Access Test (Olivia)
Olivia attempted to read Sophia_homework3 and access was denied, confirming correct permission enforcement.

<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/33924c4b-0f8d-4749-ba9a-38dda5ef0430" />

# Extra Credit: Sticky Bit Configuration

# Step 1: File Deletion Attempt (Olivia)
Olivia attempted to delete Sophia_homework from /home/cyse_project.

<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/755b2bd9-2c90-4cc0-8f75-66ce76589166" />

<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/66cf971e-4b1f-494e-8166-f17075d5b02d" />



# Step 2: Set Sticky Bit
The sticky bit permission was enabled on /home/cyse_project to restrict file deletion to file owners or the root user.


<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/58738768-ba00-4a5e-9807-80728a691661" />



# Step 3: Deletion Test with Sticky Bit
Olivia attempted to delete Sophia_homework3 but was unsuccessful.

The sticky bit (t) ensures that only the file owner or root user can delete or rename files within a directory. Since Sophia_homework and Sophia_homework3 are owned by Sophia, Olivia was unable to delete them despite having write permissions on the directory.


<img width="1042" height="588" alt="image" src="https://github.com/user-attachments/assets/17093c11-a422-4a16-a8e8-6a2ed7b201d5" />

