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

'-D' allows for a display of a list all current active and inactive network interfaces running on your workstation. sudo is used to give the user root permissions which will be needed for full functionality of tcpdump. Example below: 

<img src="https://i.imgur.com/cqn5cai.png" height="80%" width="80%" alt="Analyzing Network Traffic with tcpdump and Wireshark"/>


ctrl+c stops traffic capture in terminal.

<h2 align="center">Using filters within tcpdump to received network traffic:</h2>

Once you have the interface list, you can investigate specified interfaces by adding -i + the network interface you wish to look into.

For example: sudo tcpdump -i en0 -v host 192.168.1.1

In this case the interface specified is 'en0'.

The -v will add verbosity to the data capture and provide and screen counter so you see if packets are being caught, how many, and how fast.

This command is also asking for network traffic from the specified host '192.168.1.1'. The host filter can be an ip or even a domain

<img src="https://i.imgur.com/HHFGlBg.png" height="80%" width="80%" alt="Analyzing Network Traffic with tcpdump and Wireshark"/>


<h2 align="center">Destination and source IP addresses:</h2>

You can further filter the network traffic captured by specifying the destination and source IP addresses.

For example: 'sudo tcpdump -i en0 -v dst 192.168.1.255'

In this command the specifed destination IP is shown by 'dst' and is '192.168.1.255'. 

<img src="https://i.imgur.com/aBhUjnQ.png" height="80%" width="80%" alt="Analyzing Network Traffic with tcpdump and Wireshark"/>

Source and destination IP addresses can be combined to show network traffic from one source IP to another destination IP.

Shown below by the use of "and':

<img src="https://i.imgur.com/YI0174v.png" height="80%" width="80%" alt="Analyzing Network Traffic with tcpdump and Wireshark"/>


<h2 align="center">Capturing network traffic within a specified range:</h2>

Network traffic can also be captured from a specified range. This can be done by the use of 'net' shown below:

'sudo tcpdump -i en0 -v net 192.168.1.0/24'. 

This will capture all data from the network range specified - in this case 192.168.1.0-24

<img src="https://i.imgur.com/va9KElM.png" height="80%" width="80%" alt="Analyzing Network Traffic with tcpdump and Wireshark"/>

Network traffic can also be captured from specified protocols i.e: tcp or udp and also ports i.e: 443 or 80 etc.

Example: 'sudo tcpdump -i en0 -v tcp and net 192.168.1.0/24'

This is an exampled of a protocol specific filter. This will capture all tcp data from the network range specified - in this case 192.168.1.0-24.

'sudo tcpdump -i en0 -v port 80'

This will capture any data coming and going from port 80

<img src="https://i.imgur.com/e6vm9zy.png" height="80%" width="80%" alt="Analyzing Network Traffic with tcpdump and Wireshark"/>

'sudo tcpdump -i en0 -v src port 443 and dst 192.168.1.146'

This is a combination of the two. The source port is 443 and destination is ip 192.168.1.146. Data will be captured using these specified filters.

<h2 align="center">Saving network traffic from tcpdump into a pcap file for Wireshark:</h2>

'sudo tcpdump -w /Users/who_else/Desktop/traffic.pcap -i en0 -v tcp and net 192.168.1.0/24’

The -w specifies you wish to write a file. This then needs to be followed by the path and file name you wish to write the pcap file to. This command is capturing all tcp traffic on the network range of 192.168.1.0-24.

The pcap file can be opened within Wireshark and analysed further as shown below:

<img src="" height="80%" width="80%" alt="Editing Linux Permissions steps"/>

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
