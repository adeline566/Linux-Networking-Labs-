#User & Group Permission Management LAB

This lab demonstrates hands-on experience with Linux user and group management, directory permissions, umask configuration, SGID, and sticky bit behavior. The tasks were completed in a CCIA environment and reflect practical system administration. 


Task A: Account and Group Setup

Step 1: Create Groups
Three groups were created:

employee

payroll

admin



Step 2: Create User Accounts
Three user accounts were created with specified home directories:

Sophia – primary group: employee

Olivia – primary group: payroll

Emma – primary group: admin

All users were assigned /bin/bash as their login shell and passwords were configured.

![image alt](https://github.com/adeline566/Linux-Networking-Labs-/blob/83b4b26c40fc9d14396b674f5bdb12d8386eba05/Picture%202.png)
![image alt](https://github.com/adeline566/Linux-Networking-Labs-/blob/7a25cddac7bcb7565b5c21ee4524d470f946380a/Picture%203.png)


Step 3: Create Shared Group
A shared group named your_midas (MIDAS ID placeholder) was created and added as a secondary group for Sophia, Olivia, and Emma. Group memberships were verified for each user.

![image alt]


Step 4: Create Shared Directory
A shared directory /home/cyse_project was created and assigned ownership to the your_midas group. Directory ownership and permissions were verified.

![image alt]

Step 5: Set Directory Permissions
Permissions for /home/cyse_project were set to rwxrwx--- using the octal method, ensuring that only members of the shared group could access the directory.

![image alt]

Step 6: Configure Default Permissions (umask)
The system switched to Sophia’s account. The default permissions were modified using the umask command so that newly created files had permissions of rw-r-----. The umask value and file permissions were verified.

![image alt]


Step 7: Create File
A file named Sophia_homework was created in Sophia’s home directory with the student’s name as content. File contents and permissions were verified using ls -l.

![image alt]


Step 8: Copy File to Shared Directory
The file Sophia_homework was copied to /home/cyse_project, and file permissions in the shared directory were verified.

![image alt]


Step 9: Access Test (Emma)
The system switched to Emma’s account to test read access to Sophia_homework in the shared directory.

![image alt]


Step 10: Exit User Accounts
Exited Emma’s and Sophia’s accounts.

![image alt]

