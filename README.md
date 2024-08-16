
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
In this simple exercise, we will use Cisco Packet Tracer to practice configuring the settings of a switch using basic commands in Cisco's proprietary IOS command-line interface.
</p>
<br />

<p align = "center">
<img src="https://github.com/user-attachments/assets/8ca1adb9-0c9d-439b-94a1-d7de571984a2">
</p>
<p>
We will start by accessing the switch's command-line interface (CLI). To do this, click on the switch's image and then select the 'CLI' tab. On a real network device, you would connect your computer to the device using a console cable via the console port or connect remotely using SSH or Telnet if the device has an IP address. Then, you would open a terminal emulator like PuTTY or Tera Term. For console access, select the serial connection and configure the appropriate settings (9600 baud rate, 8 data bits, no parity, 1 stop bit, no flow control). For SSH/Telnet access, enter the device's IP address and choose the connection type (preferably SSH).
</p>
<br />

<p align = "center">
<img src= "https://github.com/user-attachments/assets/86aedc88-3607-426a-a512-cb2edfac89a2">

</p>
<p>
Now that we have reached the CLI our first objective will be to change the name of the switch from 'Switch' to 'SW1'. You may have noticed that next to the word Switch (the device's current name) is a ">". This indicates that our device is currently in user EXEC mode, which means that the authority we have to make changes and view information is very limited. To gain additional authority, we must enter privileged EXEC mode by executing the 'enable' command. You will know the command was successful when the '>' symbol changes to a '#' in the prompt, as shown in the image above.
</p>
<br />

<p align = "center">

<img src = "https://github.com/user-attachments/assets/5832a8a5-512c-421f-b638-a9bdf1a3c532">

</p>

<p>
After entering privileged EXEC mode, we will further augment our level of authority by entering global configuration mode by using the 'config t' command. Although global configuration mode grants users more authority than privileged EXEC mode, it is important to understand that these modes are not simply steps in a linear progression of access levels. Privileged EXEC mode is designed primarily for monitoring and executing higher-level commands, allowing limited configuration changes. However, it does not grant unrestricted control over the device's settings. Global configuration mode, on the other hand, is used for making system-wide changes that impact the overall operation of the device. This compartmentalization ensures that different responsibilities are managed separately, maintaining the integrity and security of the device's configuration.
</p>
<p align = "center">

<img src = "https://github.com/user-attachments/assets/a718388c-2a72-4037-a2b1-5795ca217ae4">

</p>

<p>In global configuration mode, we will change the switch's name by typing 'hostname SW1' into the command line. In this context, 'hostname' is the command used to change the device's name, and 'SW1' is the new name. If executed correctly, you will see that the prompt changes from 'Switch(config)#' to 'SW1(config)#'.</p>

<p align = "center">
<img src = "https://github.com/user-attachments/assets/535f0e9a-8b0c-4d03-ba0a-f62dc88a8842">
</p>

<p>While still in global configuration mode, we will also enhance the security of our device by assigning an encrypted password. Assigning unencrypted passwords using the 'enable password' command is poor security practice and should be avoided in scenarios where security is critical. 
  
In this exercise, we will be using Type 5 encryption by using the 'enable secret < password >' command. While Type 8 encryption is more secure and is becoming the new security standard, Type 5 may still be used in situations where compatibility with older devices is necessary, or when organizational policies have not yet been updated to require Type 8. However, it's important to consider that as security requirements evolve, transitioning to Type 8 encryption should be a priority to ensure the highest level of protection. To assign type 8 encryption you would type 'enable algorithm-type sha256 secret < password >'. </p>

<p align = "center">

<img src = "https://github.com/user-attachments/assets/c4843a4d-bcea-4103-89be-279126fbe4fd">

</p>

<p>Having assigned a type 5 encrypted password, we will return to privileged EXEC mode to ensure that the password is properly configured and observe its encrypted form within the running configuration. To do this, execute the 'exit' command from global configuration mode, then use the 'show running-config' command from privileged EXEC mode. Although global configuration mode grants a higher level of authority for making changes to the device's configuration, we still need to return to privileged EXEC mode to view the running configuration because, once again, the purpose of global configuration mode is to make comprehensive 'global' changes to the system, whereas privileged EXEC mode is for accessing 'privileged' information and troubleshooting. It is essential to remember this compartmentalization of responsibilities between privileged EXEC mode and global configuration mode to maintain security, prevent errors, and ensure efficient troubleshooting by clearly separating the tasks of viewing configurations from making system-wide changes.
  
The running configuration contains all the current settings and configurations that are actively in use by the router. This mode is essential for verifying changes and troubleshooting because it allows us to access real-time information such as interface statuses, routing tables, and security settings. By viewing the running configuration, we can confirm that our password has been assigned and see its encrypted form. As we can see, the highlighted series of letters, numbers, and symbols does not resemble the password we assigned to the switch. This change in the running configuration not only protects the integrity of our system from potential onlookers in the same physical space, but also provides stronger security against remote infiltrators compared to an unencrypted password or one using a weaker encryption algorithm, such as type 7.</p>

<p align = "center">

<img src = "https://github.com/user-attachments/assets/c6284ee8-3255-4a4f-9df0-da84c22a919d">

</p>

<p>Now that we've taken measures to ensure our device's security, we need to make sure the changes are saved to the device's startup configuration. We can do this by simply typing 'write' into the command line from privileged EXEC mode. This step is as critical as it is simple, because the device's running configuration is only stored in its RAM. If we make important changes that should become the new defaults but do not save them and the device is powered off or restarted, those changes will be lost, leaving the device in a vulnerable state. For more complex or critical changes, this oversight could require significant time, effort, and monetary cost to rectify, especially if the device supports essential services.</p>

<p align = "center">
<img src = "https://github.com/user-attachments/assets/73ab6893-4796-4b1a-a4c0-32a68ba5675a">
</p>


<p>Finally, now that we have made and verified the necessary changes to our device, we'll exit privileged EXEC mode and test our password. To do this, type 'exit' into the command line. When you type the 'enable' command to re-enter privileged EXEC mode, you will be prompted to enter your password. For security reasons, the password will not be visible as you type it, so be mindful of your input. Remember that passwords are case-sensitive, so if you have issues accessing the device, make sure that your case entries are correct and that Caps Lock is turned off. If you've entered the password correctly and pressed 'Enter,' you should be back in privileged EXEC mode. With this, our network device configuration exercise is complete! </p>


<h2>Conclusion</h2>

<p>In this exercise, we utilized Cisco Packet Tracer to practice configuring a switch using Cisco’s IOS command-line interface. We began by accessing the switch’s CLI, where we demonstrated how to enter privileged EXEC mode and global configuration mode. This process allowed us to change the switch’s name and configure an encrypted password to enhance security.

We also discussed how to view the chagnes we made in the running configuration, and the importance of saving changes to the device’s startup configuration to ensure that updates are preserved even if the device is powered off or restarted. By executing the necessary commands, we verified that the password encryption and configuration changes were applied correctly and saved.</p>

<h3>Key Takeaways</h3>

<h4>Accessing CLI:</h4>
We accessed the swtich's CLI using Cisco Packet Tracer and briefly detailed how to access the CLI while using a real, physical network device.

<h4>Configuration Modes:</h4>
We explored privileged EXEC and global configuration modes, emphasizing their distinct functions and non-linear relationship.

<h4>Security Enhancement:</h4>
We changed the switch’s hostname and applied Type 5 encryption to strengthen security. We also briefly explained why it is important to encrypt passwords, in which scenarios one may use different encryption algorithms, and how to apply type 8 encryption algorithm to a password.

<h4>Saving Changes</h4>
We confirmed the importance of saving changes to the startup configuration to prevent loss of critical updates, as well as the potential consequences of failing to do so.
</br>
</br>
</br>
<p>This exercise highlights the critical importance of proper configuration and security practices in network management. It reinforces the need to understand different modes of access and their specific purposes to maintain device integrity and security. Ensuring that configurations are saved and correctly implemented is vital for effective network administration and protection against potential vulnerabilities.</p>
