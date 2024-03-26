<h1>Analyzing Network Traffic with tcpdump and Wireshark</h1>


<h2>Description</h2>
This will be a demonstration of how to capture network traffic inside of terminal using tcpdump and saving the packet data to a .pcap file to be analyzed within Wireshark
<br />


<h2>Languages and Utilities Used</h2>

- <b>Terminal</b> 
- <b>tcpdump</b> 
- <b>Wireshark</b> 


<h1>Program walk-through:</h1>



<h2 align="center">Understanding terminal and basic tcpdump functions: </h2>
  
'tcpdump —help' specifies all the functionalities of tcpdump within the terminal with explanations of what they all do.

<img src="https://i.imgur.com/0QgKtMg.pngg" height="80%" width="80%" alt="Analyzing Network Traffic with tcpdump and Wireshark"/>

'-D' allows for a display of a list all current network interfaces running on your workstation. sudo is used to give the user root permissions which will be needed for full functionality of tcpdump. Example below: 

<img src="https://i.imgur.com/cqn5cai.png" height="80%" width="80%" alt="Analyzing Network Traffic with tcpdump and Wireshark"/>


<h2 align="center">Describe the permissions string:</h2>


<img src="https://i.imgur.com/SEdB1he.png" height="80%" width="80%" alt="Editing Linux Permissions steps"/>

The above screenshots shows the permissions for the file .project_x.txt. The permissions string -rw—w---- can be broken down into 10 separate strings or characters. The - at the beginning of the permissions string indicates these are permissions for a file and not a directory. A directory permissions string would begin with the letter d. Following this are the permissions for the three user types. The first 3 strings grouped together rw- show the permissions for the user. r referring to read, w referring to write and x finally referring to the ability to execute executable files. The - means the permission is missing for the file or directory. The second group of 3 strings show the permissions for the group. In this screenshot -w- shows that the group only has write permissions for this file. Finally, the last 3 strings — demonstrate that the other users have neither read, write or executable permissions.

<h2 align="center">Change file permissions:</h2>

The organization does not allow others to have write access to any files. Using Linux commands I will identify the files which need permissions modified and use linux commands to modify them.

The file project_k.txt has granted other users permission to write files. 

<img src="https://i.imgur.com/kShlx4m.png" height="80%" width="80%" alt="Editing Linux Permissions steps"/>

In the chmod command u sets the permissions for the user who owns the file, g sets the permissions for the group that owns the file, and o sets the permissions for others.

The following command will modify the other user permissions to remove the permission to write files: chmod o-w project_k.txt.

This is the outcome of the permissions successfully modified: 

<img src="https://i.imgur.com/k3uxC4M.png" height="80%" width="80%" alt="Editing Linux Permissions steps"/>


<h2 align="center">Change file permissions on a hidden file:</h2>

The research team has archived .project_x.txt, which is why it’s a hidden file. This file should not have write permissions for anyone, but the user and group should be able to read the file. I know .project_x.txt is a hidden file because it starts with a full stop (.).


<img src="https://i.imgur.com/QGaV7AQ.png" height="80%" width="80%" alt="Editing Linux Permissions steps"/>

Currently the user and group can both write to the hidden file and the user is the only user type who can read the file.

The following command ensures to remove the write permissions for both the user and group and add the read permissions for the group:

<img src="https://i.imgur.com/6lagvDp.png" height="80%" width="80%" alt="Editing Linux Permissions steps"/>

This is the successful outcome:

<img src="https://i.imgur.com/M2ZcWJ5.png" height="80%" width="80%" alt="Editing Linux Permissions steps"/>


<h2 align="center">Change directory permissions:</h2>

The files and directories in the projects directory belong to the researcher2 user. Only researcher2 should be allowed to access the drafts directory and its contents. Use a Linux command to modify the permissions accordingly.

Currently group users have permissions to execute files in the drafts directory.

<img src="https://i.imgur.com/hGOWugA.png" height="80%" width="80%" alt="Editing Linux Permissions steps"/>

To remove the group permissions to remove the executable permissions for the group user this command is used:

<img src="https://i.imgur.com/Hgaw7OI.png" height="80%" width="80%" alt="Editing Linux Permissions steps"/>

This is the outcome:

<img src="https://i.imgur.com/UINsdDD.png" height="80%" width="80%" alt="Editing Linux Permissions steps"/>


<h2 align="center">Summary:</h2>


Linux commands were used to modify, remove & add permissions for the three user types: user, group and other as per the organizations requirements. Removing unauthorized access and adding authorized access ensures that the system can stay secure.


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
