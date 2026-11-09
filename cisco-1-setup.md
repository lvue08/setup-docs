# My First Git Lab

This is my first document stored in Git.

## Things I Learned

- Git tracks changes to files.
- GitHub stores my repository online.
- **SSH keys** keep my account secure.

<h1>Command notes 2.2. IOS Navigation</h1>


2.2.2 Configuration Mode and Subconfiguration Modes
analyst@secOps ~]$ 1s
Desktop Downloads lab.support.files second_drive
[analyst@secOps ~]$

User EXEC Mode: Switch>
                Router>

Privileged EXEC Mode: Switch#
                      Router#

To configure the device, the user must enter global configuration mode, which is commonly called global config mode.
From global config mode, CLI configuration changes are made that affect the operation of the device as a whole. Global configuration mode is identified by a prompt that ends with (config)# after the device name, such as Switch(config)#.

Defult prompt for line configuration mode is Switch(config-line)#
Defult prompt for interface configuration mode is Switch(config-if)#





Config commands 2.2.4 Navigate Between IOS Modes
To enter line subconfiguration mode use the line command below, followed by the management line type and number you wish to access.

Use the exit command to exit a subuconfiguration mode and return to global configuration mode.
Switch(config)# line console 0
Switch(config-line)# exit
Switch(config)#

To move from any subconfiguration mode of the global configuration mode to the mode one step above it in the hierachy modes, enter the exit command.

To move from any subconfiguration mode to the privileged EXEC mode, enter the end command or enter the key combination Ctrl+Z
Switch(config-line)# end
Switch#

You can also move directly from one subconfiguration mode to another. The command prompt changes from (config-line)# to (config-if)#
Switch(config-line)# interface FastEthernet 0/1
Switch(config-if)#


The Command Structure 2.3

<b>Ping<b> Ip-address - The command <b>Ping<b> and the user-defined argument is the ip-address of the destination device. For example, ping 10.10.10.5 (IP address of another computer or PC)

<b>Traceroute<b>ip-address - The command is<b>Traceroute<b>and the user-defined argument is the ip-address of the destination device. For examples, traceroute 192.168.254.254.


<b>End of 2.3 The Command Structure<b>


Basic Device Configuration 2.4

1.Start with a letter
2.Contain no spaces use dashes -
3.End with a letter or digit
4.Use only letters, digits and dashes
5.Be less than 64 characters in length

When naming convention has been identified, the next step is to use the CLI to apply the names to the devices. From privileged EXEC mode, access the global configuration mode by entering the<b>configure terminal<b>command.

Command hostname: 
Switch# configure terminal
Switch(config)# hostname (Name of your device)
Device name(config)#

<h1>2.4.3 Configure Passwords</h1>

To secure user EXEC mode access, enter line console configuration mode using the<b>line console 0<b>global configuration command. The zero is used to represent the first console interface. Next, specify the user EXEC mode password using the<b>password<b>password command. Finall, enable user EXEC access using the<b>login<b>in command.

Command Password:
Switch# configure terminal
Switch# line console 0
Switch# password (Your password)
Switch# login
Switch# end
Switch#

Console access will now require a password before allowing access to the user EXEC mode.

To have administrator access to all IOS commands including configuring a device, you must gain privileged EXEC mode access. It is important access method because it provides complete access to the device. 

To secure privileged EXEC access, use the<b>enable secret<b> password global config command, as shown.

Switch# configure terminal
Switch# enable secret class
Switch# exit
Switch#

Virual terminal (VTY) lines enable remote access using Telnet or SSH to the device. Many cisco switches support up to 16 VTY lines that are numbered 0 to 15.

To secure VTY lines, enter line VTY mode using the<b>ling vty 0 15<b> global config command. Next, specify the VTY password using the password password command. Lastly, enable VTY access using the login command.

Switch# configre terminal
Switch# line vty 0 15
Switch# password cisco
Switch# login
Switch# exit
Switch#

2.4.4 Encrypt Passwords

The startup-config and running-config files display most passwaords in plaintext. 
To encrypt all plaintext passwords, use the<b>service password-encryption<b>global config command.

Switch# configure terminal
Switch(config)# service password-encryption
Swtich(config)#

Use the show running-config command to verify that passwords are now encrypted.

Switch# end
Switch# show running-config

<h1>2.4.5 Banner messages</h1>

To creat a banner message of the day on a network device, use the<b>banner motd #<b>the message of the day # global config command. The "#" in the command syntax is called the demlimiting character can be any charcter as long as it does not occur in the message. For thos reason, symbols such as the "#" are often used. After the command is executer, the banner will be displayed on all subsequent attempts to access the device until the banner is removed.

Configure the banner
Switch# configure terminal
Switch# banner motd #Authorized Access Only#

End of Basic device Configuration 2.4


<h1>Save Configurations 2.5</h1>

Configuration files 2.5.1
There are two system files that store the device configuration.

1.startup-config - This si the saved configuration file that is stored in NVRAM. It contains all the commands that will be used by the device upon startup or reboot. Flash does not lose its contents when device is powered off.

2.running-config - This is stored in Random Access Memory (RAM). It reflects the current configuration. Modifying a running configuration affects the operation of a cisco device immediately. RAM is volatile memory. It loses all of its content when the device is powered off or restarted.

The show running-config privileged EXEC mode command is used to view the running config. 

Switch# show running-config

To view starup configuration file, use the show startup-config privileged EXEC command. 

If power to the device is lost, or the device is restarted, all configuration changes will be lost unless they have been saved. To save changes made to the running configuration to the startup configuration file, use the<b>copy running-config startup-config<b>Privileged EXEC mode command.

2.5.2 Alter the Running Configuration

If changes are made to the running config do not have the desired effect and the running-config has not yet been saved, you can restore the device to its previous configuration. Remove the changed commands individuall, or reload the device using the<b>reload<b>privileged EXEC mode command to retore the startup-config.


2.5.4 Capture Configuration to a Text File

Configuration files can also be saved and archived to a text document. This sequence of steps ensures that a working copy of the configuration file is available for editing or reuse later.

Example assume that a switch has been configured, and the running config has been saved on the device.

Step 1. Open terminal emulation software, such as PuTTY or Tera Term, that is already conencted to a switch.

Step 2. Enable logging in the terminal software and assign a name and file loaction to save log file. The figure displays that All session output will be captured to the file specified.

Step 3. Execute the show running-config or show startup-config command at the privileged EXEC prompt. Text displayed in the termianl window will be placed into the chosen file. 

Switch# show running-config
building configuration. . .
(output omitted)

Step 4. Disable logging in the terminal software. The figure shows how to disable logging by choosing the None session logging option.

Restoring a configuration file to a device

Step 1. Enter global configuration mode on the device.

Step 2. Copy and pasta the text file into the terminal window connected to the switch.

The text in the file will be applied as commands in the CLI and become the running configuration on the device.

End of 2.5 Save Configurations


2.6 Ports and Adresses

The use of IP addresses is the primary means of enabling devices to locate one another and establish end-to-end communication on the internet. Each end device on a network must be configured with an IP address. 
Examples below this text.

<ul>
    <li>Computers (work stations, laptops, file servers, web servers)<li>
    <li>Network printers<li>
    <li>VoIP phones<li>
    <li>Security cameras<li>
    <li>Smart phones<li>
    <li>Mobile handheld<li>
<ul>


2.6.2 Interfaces and ports

Network communications depend on end user device interfaces, networking device interfaces, and the cables that connect them. Each physical interface has specifications, or standards, that define it. A cable connectiong to the interface must be designed to match the physical standards of the interface. Types of network media include twisted-pair copper cables, fiber-optic cables, coaxial cables, or wireless.

Different types of network media have different features and benefits. Not all network media have the same characteristics. Not all media are appropriate for the same purpose. These are some of the differences between various types of media.

<ul>
    <li>Distance the media cna successfully carry a signal<li>
    <li>Environment in which the media is to be installed<li>
    <li>Amount of data and the speed at which it must be transmitted<li>
    <li>Cost of the media and installation<li>
<ul>

A layer 2 switch does not need an IP address. The IP address assigned to the SVI is used to remotely access the switch. An IP address is not necessary for the switch to perform its operations.

End of Ports and Addresses 2.6


