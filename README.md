
<h1>Cisco Packet Tracer - Basic Device Security</h1>
.<br />


<h2>Introduction</h2>

- Objective: To configure basic network settings on a switch, including hostname and password encryption, using Cisco IOS CLI.

- Tools Used: Cisco Packet Tracer, Switch, Router, PCs

- Skills Highlighted: Basic network device configuration, password security, troubleshooting in Cisco IOS CLI


<h2>Project Overview</h2>

- Lab Setup: A small network consisting of a switch, router, and a few PCs connected in Cisco Packet Tracer.

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)


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
We'll start this exercise by accessing the switch's command-line interface (CLI). To do this, click on the switch's image and then select the 'CLI' tab.
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
After entering privileged EXEC mode, we'll want to further augment our level of authority by entering global configuration mode using the 'config t' command. Although privileged EXEC mode grants more access than user EXEC mode, it's important to understand that these modes aren't simply steps in a linear progression of access levels. User EXEC mode is designed for basic monitoring and troubleshooting, while global configuration mode, though separate, is intended for comprehensive system-wide changes. This separation helps compartmentalize responsibilities, ensuring that different functions, such as monitoring versus configuring, are handled distinctly to maintain system integrity and security.
</p>
<p align = "center">

<img src = "https://github.com/user-attachments/assets/a718388c-2a72-4037-a2b1-5795ca217ae4">

</p>

<p>Now that we've activated global configuration mode we can change the name of our switch. We'll do this by typing 'hostname SW1' into the command line.In this scenario 'hostname' is the command telling the terminal to change the name of our device, and 'SW1' is the name we're changing it to. If you've executed these steps correctly you'll notice that the text in front of the command line that once said 'Switch (config)#' now says 'SW1(config)#'.</p>

<p align = "center">
<img src = "https://github.com/user-attachments/assets/535f0e9a-8b0c-4d03-ba0a-f62dc88a8842">
</p>

<p>While we're still in global configuration mode, we'll want to strengthen the security of our device by assigning it an encrypted password. While assigning unencrypted passwords using the 'password' command is possible, doing so is a poor security practice and should never be done in a scenario where security is critical. 
  
In this exercise, we will be using Type 5 encryption by using the 'enable secret < password >' command. In our case, the password is 'Poneglyph,' so we'll type 'enable secret Poneglyph.' While Type 8 encryption is more secure and is becoming the new security standard, Type 5 may still be used in situations where compatibility with older devices is necessary, or when organizational policies have not yet been updated to require Type 8. However, it's important to consider that as security requirements evolve, transitioning to Type 8 encryption should be a priority to ensure the highest level of protection. To assign type 8 encryption you'd type 'enable algorithm-type sha256 secret < password >'. </p>
