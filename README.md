# Window Switch

Window switch (**wswitch**) is a utility which enables you to bind a key to a particular application on Ubuntu.
When the key is pressed, one of these three things will happen based on the current state.

1. If the application is not running, **wswitch** will start the application.
2. If the application is running but its window is not in focus, **wswitch** will bring it to focus.
3. If the application is running and its window is in focus, **wswitch** will *iconify* (minimize) it.

## How to use **wswitch**?

### Install dependencies

As a first step, install the dependencies

```bash
sudo apt-get install wmctrl xwit
```

### Add **wswitch** to path

The best way to do this is to make a soft link of **wswitch** in **/usr/local/bin/**

1. Navigate to the directory containing **wswitch** on a terminal.
2. Run the following:
	```bash
	sudo ln -s $(pwd)/wswitch /usr/local/bin/wswitch
	```

### Identify `WM_CLASS` of your target application

Now let's configure **wswitch** for your favorite application.
Let's assume that your target application is [Terminator](https://launchpad.net/terminator).

First you need to find the `WM_CLASS` of your target application.
The following will help you do that.
1. Start your target application.
2. Fire up a terminal (If your target application is Terminator, you are in luck).
3. Run the following: `wmctrl -l -x | awk '{print $3}'`. This will print a list of `WM_CLASS` of all the windows currently open on your desktop.
4. Identify the `WM_CLASS` of your target application. For Terminator, this will be *terminator.Terminator*.

### Bind a key

The next step is to bind a key to **wswitch**.

1. Open the keyboard shortcuts settings. This is usually found in `System Settings > Keyboard > Shortcuts`.
2. Add a new shortcut and give it a name (like Terminator).
3. In the *command* section write the following:

	```bash
	wswitch <WM_CLASS> <launch_command>
	```
	Here `WM_CLASS` is what you found in the previous step.
	The `launch_command` is the command which can be used to launch a new instance of the application.

	For example, for Terminator, the following can be used:

	```bash
	wswitch terminator.Terminator terminator
	```

	You can also pass arguments in the `launch_command`. For example,

	```bash
	wswitch terminator.Terminator "terminator --layout=my-custom-layout"
	```

4. Bind your favorite key to this shortcut.
5. Hit the key and see the magic!

## Suggestions?
Create an issue or code it up and send a pull request.
