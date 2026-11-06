# My First Git Lab

This is my first document stored in Git.

## Things I Learned

- Git tracks changes to files.
- GitHub stores my repository online.
- **SSH keys** keep my account secure.

Command notes 2.2. IOS Navigation


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

Use the exit command to exit a subuconfiguration mdoe and return to global configuration mode.
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
