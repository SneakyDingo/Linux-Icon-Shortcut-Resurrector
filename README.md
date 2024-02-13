# Linux-Icon-Shortcut-Resurrector
Linux-Icon-Shortcut-Resurrector is a band aid solution to stop Linux from resetting your custom shortcut icons to default settings. Setting it up will take a few minutes, but it's not difficult.

# Overview
I'll have you create a master file of the .desktop file with the custom icon image included. Then, we'll execute a shell script to replace the original .desktop file with the master file. Lastly, we'll create a new .desktop file for the shell script, allowing Linux to run it automatically on startup. This ensures that the correct icon path is maintained without manual intervention.

# Instructions

### I. Creating the "Master" .desktop File

1. Go to ```/usr/share/applications``` and find the problematic .desktop file that's reverting to default. Copy the .desktop file (I will use Brave Web Browser as the example).
   
2. Paste the .desktop file to a folder location of your choosing. For this tutorial, everything I will use will be found in the Desktop folder.

3. Open the recently pasted .desktop file with a text editor. Look for the line that reads "Icon=". Put in the path of your desired icon after it. If it doesn't exist, write it in.
Ex: ```"Icon=/home/sneakydingo/Desktop/brave_icon.png"```

4. Save the file and exit.
   

### II. Creating the Shell Script

1. Create an empty text file, open it.
   
2. Copy and paste the following code into the text file:
```
#!/bin/bash
    # Copying the master file to the applications folder with Root permission"
    echo "Copying the .desktop files to /usr/share/applications..."
    sudo cp /home/sneakydingo/Desktop/brave-browser.desktop /usr/share/applications/brave-browser.desktop

    # Refresh the icon cache
    echo "Refreshing the icon cache..."
    sudo update-desktop-database /usr/share/applications
fi
```
*PLEASE NOTE: This shell script is a template—you'll have to modify the file path information, specifically the username (/sneakydingo) and folder location (Desktop/)*  

3. Save the file as ```iconfix.sh```, then exit.

4. You will have to make the .sh file executable. You can do this by running the following command in the terminal:
```
chmod +x iconfix.sh
```


### III. Shell Script into an Application

1. Create an empty text file. Open the file.
   
2. Copy & paste this template into the file:
```
   [Desktop Entry]
Type=Application
Name=Icon Fix
Exec=/home/sneakydingo/Desktop/iconfix.sh
Icon=/home/sneakydingo/Desktop/iconfix_icon.png
Terminal=true
Name[en_US]=Icon
```
*PLEASE NOTE: The Icon path for this file IS NOT for the Brave Browser Icon, but for the iconfix shell script that we will use to run on start-up. You will have to find your own icon.*

3. Save file as ```iconfix.desktop```, then exit.

4. Open a terminal, you will be copying the .desktop file to the applications folder:
```
sudo cp /home/sneakydingo/Desktop/iconfixer.desktop /usr/share/applications/
```
5. Enter your user password if permission is required.
   

### IV. Start-up Application

Now that the script has been turned into a .desktop file AND it's in the applications folder, you should be able to find the iconfix program in the Startup Applications. Select it and enjoy!

# To Do
Create a nifty icon for the iconfix application.


