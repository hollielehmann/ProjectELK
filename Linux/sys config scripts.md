## Week 4 Homework Submission File: Linux Systems Administration

### Step 1: Ensure/Double Check Permissions on Sensitive Files

1. Permissions on `/etc/shadow` should allow only `root` read and write access.

    - Command to inspect permissions: ls -l /etc/shadow

    - Command to set permissions (if needed):  sudo chmod 600 /etc/shadow


2. Permissions on `/etc/gshadow` should allow only `root` read and write access.

    - Command to inspect permissions: ls -l /etc/gshadow

    - Command to set permissions (if needed): sudo chmod 600 /etc/gshadow

3. Permissions on `/etc/group` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions: ls -l /etc/group

    - Command to set permissions (if needed): sudo chmod 644 /etc/group

4. Permissions on `/etc/passwd` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions: ls -l /etc/passwd

    - Command to set permissions (if needed): sudo chmod 644 /etc/psswd

### Step 2: Create User Accounts

1. Add user accounts for `sam`, `joe`, `amy`, `sara`, and `admin`.

    - Command to add each user account (include all five users): 
    - sudo adduser sam
    - sudo adduser joe
    - sudo adduser amy
    - sudo adduser sara
    - sudo adduser admin

2. Ensure that only the `admin` has general sudo access.

    - Command to add `admin` to the `sudo` group: sudo usermod -aG sudo admin

### Step 3: Create User Group and Collaborative Folder

1. Add an `engineers` group to the system.

    - Command to add group: sudo addgroup engineers


2. Add users `sam`, `joe`, `amy`, and `sara` to the managed group.

    - Command to add users to `engineers` group (include all four users): 
    - sudo usermod -a -G engineers sam
    - sudo usermod -a -G engineers joe
    - sudo usermod -a -G engineers amy
    - sudo usermod -a -G engineers sara





3. Create a shared folder for this group at `/home/engineers`.

    - Command to create the shared folder:  sudo mkdir -p /home/engineers


4. Change ownership on the new engineers' shared folder to the `engineers` group.

    - Command to change ownership of engineer's shared folder to engineer group:  
    - sudo chown -R :engineers /home/engineers


### Step 4: Lynis Auditing

1. Command to install Lynis: sudo apt-get install lynis

2. Command to see documentation and instructions: man lynis

3. Command to run an audit: sudo lynis audit system

4. Provide a report from the Lynis output on what can be done to harden the system.

    - After Testing, it is suggested that a malware scanner, such as chkrotkit or OSSEC should be installed. 

    - Screenshot of report output: https://drive.google.com/file/d/1PFWTOq46-KYhEFdpj3jt-F22PAafvFwG/view?usp=sharing 


### Bonus
1. Command to install chkrootkit:  sudo apt-get install chkrootkit

2. Command to see documentation and instructions: man chkrootkit

3. Command to run expert mode: sudo chkrootkit -x

4. Provide a report from the chkrootkit output on what can be done to harden the system.
    - Screenshot of end of sample output https://docs.google.com/document/d/19ipxkddNwmigB2ansnjarWUQmBdU8i2CZ3jruThmWZI/edit?usp=sharing 

    - After running chkrootkit in expert mode, information was discovered in the utmp file about non registered user processes. Further testing on each non registered user process is neede to make sure that they are not malicious. 

    - It was also discovered that the utmp file is set to writable. it must be changed to read only, as it risks faked system logfiles or modifications of system files.

    

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
