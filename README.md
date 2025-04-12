# Using FTP to Manage Saves on PS3
* The Apollo Save Tool FTP Server feature allows you to download and upload saves from an FTP server. 
* Currently only on PS3 but will come to PSP,PS Vita and PS4.
## You must be connected to the same network on both devices and set up the necessary permissions. 
## Newer versions of the FileZilla client enforce a more secure but unnecessary connection. As such only older versions can be used or alternative apps.

# On Windows
* For Windows one of the best options is the FTP server that comes with it. Here is how to enable it.
1. In the search bar type in "Turn Windows features on or off" and open it.
2. Under "Internet Information Services" enable "FTP Server" and "Web Management Tools". Restart the PC to enable the features. 
3. If you do not want to use the credentials of your main user account create a new one.
4. Right click the Windows icon and choose "Computer Management" or search it in the search bar. 
5. Go to "Local Users and Groups" then go to "Users".
6. Create a new user name it and set the password, and remember them. (Set the password to never expire.)
7. Go back to the search bar and type in "Internet Information Services (IIS)" and open it. 
8. Open the dropdown on the left with the name of your device.
9. Click on the device name and under "IIS" find "Server Certificates" and go into it. 
10. Right click in empty space and choose "Create Self-Signed Certificate" give it a name and press "OK".
11. Right click on "Sites" and choose "Add FTP Site". 
12. Name it anything you want and set the path to where you want your saves to be uploaded to then click on "Next".
13. In "Binding" set the "IP Address" from "All Unassigned" to your current IP from the dropdown.(Open CMD and type in "ipconfig" if needed)
14. Leave the "Start FTP site automatically" enabled. 
15. Under "SSL" set it to "No SSL" or "Allow SSL".
16. Set "Authentication to "Basic". Set "Authorization" to "All users". Tick both "Read" and "Write" for permissions and click "Finish"
17. In "FTP SSL Settings" set the "SSL Policy" to "Allow SSL Connections".
18. Set the SSL certificate to the one you created previously you can select it from the dropdown then press "Apply" on the right side of the window.
19. Go to the FTP server you created and go to "FTP Firewall Support".
20. Under Data "Channel Range:" set it to 5000-51000.
21. Under "External IP Address of Firewall" set it to your current IP then press "Apply" on the right side of the window. (Open CMD and type in "ipconfig" if needed)
22. Open the search bar and type in "Windows Defender Firewall with Advanced Security" go to both Inbound and Outbound Rules and enable the FTP rules as seen in the pictures below.   
![-](imgs/1.PNG) 
![-](imgs/2.PNG) 
23. Back in "Internet Information Services (IIS)" right click on the FTP Site you created and go to "Manage FTP Site" and choose to restart it.
24. Restart the PC if you cannot connect from Apollo.
 
# Old FileZilla
* Newer versions of the FileZilla client enforce a more secure but unnecessary connection. As such only older versions can be used or alternative apps.
You can download this [Old version](https://www.mediafire.com/file/5fehy6soc48djps/FileZilla_Server-0_9_60_2.exe/file).
1. Install the server from the link above. 
2. Open it and create a host user and password. 
3. Go to "Edit" and add a user, and set a password for it.
4. Go to "Shared folders" and set the folder where you want the saves to be stored.
5. Under "Files" which is between the user and shared folder tick "Read" "Write" and "Delete" and under "Directories" tick "Create" and "Delete" then press "OK" at the bottom left.
6. Go to "Edit" and select "FTP over TLS Settings" then untick "Enable FTP over TLS support" and press "OK" at the bottom left.
7. Open the search bar and type in "Windows Defender Firewall with Advanced Security" go to Inbound Rules.
8. Choose "New Rule", set it to "Port" then press "Next". Set it to "TCP" and set the port to 21, then press "Next".
9. Leave "Action" at "Allow the Connection" and press "Next".
10. Tick all the boxes for "Where does this rule apply?" and press "Next" 
11. Finally name the rule and press "Finish"

# Alternative FTP server
*WIP

# On Android
1. On Android download any app that will allow you to be the HOST FTP server. The app "WiFi FTP Server" was tested and works for this. 
2. You have to set a username and password for the server WiFi FTP Server comes with the defaults of "android" for both but you can change them. 
3. Connect your phone to the same network as the PS4 and open Apollo. 

# On a NAS
* TrueNAS Scale will be used as an example. 
1. Add a new Dataset and name it whatever you want. For example: PS3saves
2. Go to "Credentials and make a new User and set a password and set the user directory as the Dataset you just created. 
3. Go to "System Settings" then "Services" and enable the FTP service, setting its path to the Dataset. 

# Connecting to the Server from Apollo
* The previously created FTP server credentials and IP are required. 
1. Download and install the latest version of [Apollo](https://github.com/bucanero/apollo-ps3/latest).
2. Open Apollo and go to Settings.
3. Select "Set User FTP Server URL" and enter in your FTP server IP along with the username and password then press the start button.
4. The following structure is a template: ftp://username:password@192.168.0.1/
5. An example: ftp://peaches:mono58672@192.168.1.9
6. You can now upload saves to your FTP server by going into the save and choosing "Upload save backup to FTP". 
7. To download saves you have uploaded go to Settings and set the "Online Saves Server" to "FTP Server" as the source.
8. Return to the Apollo home screen , navigate to FTP Server, and download the desired saves.  