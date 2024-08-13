
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







<p>
After entering privileged EXEC mode, we'll want to further augment our level of authority by entering global configuration mode using the 'config t' command. Although privileged EXEC mode grants more access than user EXEC mode, it's important to understand that these modes aren't simply steps in a linear progression of access levels. User EXEC mode is designed for basic monitoring and troubleshooting, while global configuration mode, though separate, is intended for comprehensive system-wide changes. This separation helps compartmentalize responsibilities, ensuring that different functions, such as monitoring versus configuring, are handled distinctly to maintain system integrity and security.
</p>
