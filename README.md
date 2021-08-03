# cmddm
cmddm stands for command display manager.  
cmddm allows users to select available gui sessions like WM/DE directly through console environments without a graphical display manager

# The conventional approach
The conventional approach to load gui sessions from console environment is to crate a .xinirc file and put the binary executable of the particular gui session that needs to be run in the .xinitrc file. Then, we add startx to our .profile file or .bash\_profile. The problem with this approach is that you need to create separate xinitrc files for different window managers/ desktop environments that you use or manually use startx for each of them. This scripts solve this problem by offering display manager like session launching directly in the console environment. It displays a list of available xsessions and you can choose any of them to be launched.

# Requirements
- python3
- a posix system able to run xserver and a pure console environment
- xorg-xinit or xinit, whatever it is called in you distro's repos as the script uses startx at its back

# Installation
Just satisfy the requirements and put the cmddm somewhere in path. It would be generally executable. If it's not, make it executable by "chmod +x". Add cmddm in you .profile or .bash\_profile

# cmd mode
The script provides all the xsessions provided in /usr/share/xsessions. But, it also adds a special session called "cmd". If you don't want to go into a gui session and choose to be remain in console environment, then choosing this option would leave you back to a console environment

# xinitrc like startup features
We tend to add some startu programs in our xinitrc or some shutdown programs that should run after quitting the gui environment. The script also provides these features. These aren't available through the command line, but can be configured in the configuration file located in ~/.config/cmddm.toml The file uses toml configuration. To add startup or shutdown programs, lookup "startup" subcategory in the configuration and under it add your programs to respective lists (arrays) referencing to run\_after/before\_session\_initialisation.

# Some other configuration
If you don't like being asked each time you login which session you want to use, you can turn wait\_for\_selection to false and modify the default\_value to your desired session name. If default\_value is used without turning wait\_for\_selection to false, it means nothing, you would be asked about which session to use and would not use default session
