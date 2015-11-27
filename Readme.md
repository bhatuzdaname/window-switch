#Dropdown Terminator (like guake)
Terminator is awesome but it lacks the ease of access that guake provides with it's dropdown feature. Our aim is to have this for terminator too.

First you need to install the following apps:
`sudo apt-get install wmctrl xdotool xwit`

Next move __wswitch__ (bash script) to __/usr/local/bin__ and grant executable permission with:
`sudo chmod +x wswitch`

Next make your preferred terminator layout and name it as 'guake-style'.

The final step is to execute this script on a keystrike. Go to Keyboard shortcuts and set up a new one. In the command area simply write __wswitch__ and for keystroke choose a preferred one (I like F11).

And voilà! We are done.

#Add entry to nautilus right-click menu#
First install __nautilus-actions__
`sudo apt-get install nautilus-actions`

Next move __launch_term__ to __/usr/local/bin__ and grant executable permission with:
`sudo chmod +x launch_term`

In nautilus actions simply add a new entry with the command __launch_term__ and the parameter __%d__ i.e. current directory.
Preferably you can also simply choose import profile and choose __terminator_nautilus.desktop__.
