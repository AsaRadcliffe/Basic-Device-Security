
<h1>Cisco Packet Tracer - Basic Device Security</h1>
.<br />


<h2>Introduction</h2>

- Objective: To configure basic network settings on a switch, including hostname and password encryption, using Cisco IOS CLI.

- Tools Used: Cisco Packet Tracer, Switch, Router, PCs

- Skills Highlighted: Basic network device configuration, password security, troubleshooting in Cisco IOS CLI


<h2>Project Overview</h2>

- Lab Setup: A small network consisting of a switch, router, and a few PCs connected in Cisco Packet Tracer.


<h2>Step-by-Step Implementation</h2>
<p align = "center">
<img src= "https://github.com/user-attachments/assets/140e114b-1521-46af-8c3e-fb6a57beebb7">
</p>
<p>
In this simple excercise we will be using Cisco Packet Tracer to practice configuring the settings of a switch using basic commands in Cisco's proprietary IOS command line interface.
</p>
<br />

<p align = "center">
<img src="https://github.com/user-attachments/assets/8ca1adb9-0c9d-439b-94a1-d7de571984a2">
</p>
<p>
We'll start this exercise by accessing the switch's command-line interface (CLI). To do this, click on the switch's image and then select the 'CLI' tab. On a real network device you'd do this by connecting your computer to the device using a console cable via the console port, or connecting remotely using SSH or Telnet if you're configuring a router that has an IP address. You would then open a terminal emulator like PuTTY or Tera Term; for console access, select the serial connection and configure the appropriate settings (9600 baud rate, 8 data bits, no parity, 1 stop bit, no flow control). For SSH/Telnet access, enter the router's IP address and choose the connection type (preferably SSH).
</p>
<br />

<p align = "center">
<img src= "https://github.com/user-attachments/assets/86aedc88-3607-426a-a512-cb2edfac89a2">

</p>
<p>
Now that we've reached the CLI our first objective will be to change the name of the switch from 'Switch' to 'SW1'. You may have noticed that next to the word Switch (the device's current name) is a ">". This indicates that our device is currently in user EXEC mode, which means that the authority we have to make changes and view information is very limited. To change this we must enter privleged EXEC mode by executing the 'Enable' command. You'll know the command worked when the '>' symbol next to our device's name becomes a '#', as it has in the image above.
</p>
<br />

<p align = "center">

<img src = "https://github.com/user-attachments/assets/5832a8a5-512c-421f-b638-a9bdf1a3c532">

</p>

<p>
After entering privileged EXEC mode, we'll want to further augment our level of authority by entering global configuration mode by using the 'config t' command. Although global configuration mode grants users more authority than privileged EXEC mode, it's important to understand that these modes aren't simply steps in a linear progression of access levels. Privileged EXEC mode is designed primarily for monitoring and executing higher-level commands, allowing limited configuration changes. However, it doesn't grant unrestricted control over the device's settings. Global configuration mode, on the other hand, is used for making system-wide changes that impact the overall operation of the device. This compartmentalization ensures that different responsibilities are managed separately, maintaining the integrity and security of the device's configuration.
</p>
<p align = "center">

<img src = "https://github.com/user-attachments/assets/a718388c-2a72-4037-a2b1-5795ca217ae4">

</p>

<p>Now that we've enabled global configuration mode we can change the name of our switch. We'll do this by typing 'hostname SW1' into the command line. In this scenario 'hostname' is the command telling the terminal to change the name of our device, and 'SW1' is the name we're changing it to. If you've executed these steps correctly you'll notice that the text in front of the command line that once said 'Switch (config)#' now says 'SW1(config)#'.</p>

<p align = "center">
<img src = "https://github.com/user-attachments/assets/535f0e9a-8b0c-4d03-ba0a-f62dc88a8842">
</p>

<p>While we're still in global configuration mode, we'll also want to strengthen the security of our device by assigning it an encrypted password. Assigning unencrypted passwords using the 'enable password' command is possible, but doing so is a poor security practice and should never be done in a scenario where security is critical. 
  
In this exercise, we will be using Type 5 encryption by using the 'enable secret < password >' command. While Type 8 encryption is more secure and is becoming the new security standard, Type 5 may still be used in situations where compatibility with older devices is necessary, or when organizational policies have not yet been updated to require Type 8. However, it's important to consider that as security requirements evolve, transitioning to Type 8 encryption should be a priority to ensure the highest level of protection. To assign type 8 encryption you'd type 'enable algorithm-type sha256 secret < password >'. </p>

<p align = "center">

<img src = "https://github.com/user-attachments/assets/c4843a4d-bcea-4103-89be-279126fbe4fd">

</p>

<p>Having assigned a password with type 5 encryption, we'll now want to return to privileged EXEC mode to ensure that the password is properly configured and to observe how it appears in its encrypted from within the running configuration. We'll do this by executing the 'exit' command from global configuration mode, then executing the 'show running-config' commmand from privileged EXEC mode. Although global configuration mode grants a higher level of authority for making changes to the router's configuration, we still need to return to privileged EXEC mode to view the running configuration because, once again, the purpose of global configuration mode is to make comprehensive 'global' changes to the system, whereas privileged EXEC mode is for accessing 'privileged' information and troubleshooting. It is essential to remember this compartmentalization of responsibilities between privileged EXEC mode and global configuration mode to maintain security, prevent errors, and ensure efficient troubleshooting by clearly separating the tasks of viewing configurations from making system-wide changes.
  
The running configuration contains all the current settings and configurations that are actively in use by the router. This mode is essential for verifying changes and troubleshooting because it allows us to access real-time information such as interface statuses, routing tables, and security settings. By viewing the running configuration, we can confirm that our password has been assigned and see its encrypted form. As we can see, the highlighted series of letters, numbers, and symbols does not resemble the password we assigned to the switch. This alteration in the running configuration not only protects the integrity of our system from potential onlookers in the same physical space but also provides stronger security against remote infiltrators compared to an unencrypted password or one using a weaker encryption algorithm, such as type 7.  </p>
