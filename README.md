# pythonforandroid
  This text file dilineates the steps needed to setup the android platform and write android apps using python on a PC.
  
1)	Downlaod and install Java SE 6 or 7. I installed Java SE 7. Java SE 8 was found to be incomptabile and the emulator will show an error message instructing you to install a JDK.

2)	In Windows 8.1, right click on 'This PC' and click on 'Properties'. In the following window, click on 'Advanced System Settings' and then hit the Environment Variables button.

3)	Under System Variables, click on New. Specify the variable name as JAVA_HOME and set its value as the path-  C:\Program Files\Java\jdk1.7.0_79. I downloaded the android emulator from the link: https://developer.android.com/sdk/index.html
From this page download the file: android-sdk_r24.2-windows.zip

4)	Now extract it into C drive.

5) 	Find android.bat file in the folder of the extracted parent folder and execute it.

6)	From the list that pops up, select the packages you want to install and install them.

7)	In the android-sdk-windows folder, execute the AVD manager.exe file.

8)	In the AVD manager window, select the virtual device configurations., I used Google Nexus 4, Skin Type: HVGA, Internal Memeory 1024 Mib and SDCard: 512 Mib

9)  With the configurations set, click Ok.

10)	Now the Android Virtual Device is created.

11)	In the AVD Manager window, select the device you just created and select 'Start'.

12)	Now the AVD starts. Wait for some time as the AVD is slower than the actual smartphone.

13)	Next we need to add a scripting layer. Return to the Google page in AVD's browser and type'sl4a_r6.apk'. sl4a is the scripting layer for android.

14)	Download the apk file and click on it to install it.	

15)	Click on the AVD's web browser and type the term 'python-for-android_r1.apk' in the google search bar.

16) 	Click on the first link and download the apk file. This step is to add scripting function to android using python. 

17)	In the browser window, click on the Menu button and select Downloads. Click on the apk file to install it. (Before, you do this, ensure you have enabled 'Unknown Sources' in the device's Settings--> Applications.

18)	The installer will download and extract different files and install it.

19)	Just to ensure we have installed everything correctly, go to the apps screen of the android virtual device. 

20) In that, click on an app named Sl4a and see if the various .py files have been installed.

21) Now we need to setup the AVD so that it can execute any python program we write.

22)	Before we proceed with the configuration, ensure that you don't have any emulator programs such as Bluestacks running in the background. If so, please close any such applications.

23) Now write a sample program that may contain the following lines or its variants but with the same functionality:
		  
		  import android
		  test=android.Android()
		  test.makeToast("Hello from Android on PC")
	   
Save this program (I named it android_test.py) in the platform-tools folder of the C:\Program Files\Android\android-sdk_r24.2-windows\android-sdk-windows\platform-tools

24)	In Windows 8.1, right click on 'This PC' and click on 'Properties'. In the following window, click on 'Advanced System Settings' and then hit the Environment Variables.

25)	Under System Variables, click on New. Specify the variable name as AP_PORT and set its value as 9999.

26)	In your PC, open your web browser and download the script android.py from the link: https://code.google.com/p/android-python-market/downloads/detail?name=android.py

27)	Copy the android.py file in to the folder Python34/Tools/Scripts. Now we need to convert android.py to be compatible with Python 3. Launch a command promprt window and navigate to the same folder. Now execute the follwoing command:
	2to3 android.py

28)	Then copy the android.py file to C:\Python3x folder (x is for the version. I am using Python 3.4 hence the folder Python34). If you are using Python2.x, copy the android.py file to C:\Python2x.

29)	In the Android Virtual Device, you must have seen a list of python scripts inside the app Sl4a. In this screen, hit the Menu button and then Hit View-->Interpreters.

30)	In this screen, hit on Menu again and select Start Server, then click Private. Now we have started a private server. We need this step in order to know the listening TCP port number.

31)	In the top left corner, there is an icon for the Sl4a that shows that a server is running. Click on this icon and hold your click. Drag down while holding the click to see the server running. Click on the server. In the ensuing screen, the last 5 digits show the TCP port used for listening(let us assume that it is 12345).

32)	Now, launch command prompt. Navgiate to folder C:\Program Files\Android\android-sdk_r24.2-windows\android-sdk-windows\platform-tools.

33)	To check which emulators are running, run the command: 
	  adb devices
	If you see any extra devices, stop them using Task Manager.

34)	We need to forward the network connection to the android device. For that, issue the following command:
	    adb forward tcp:9999 tcp:12345 
	    set AP_PORT=9999

35)	Now run the program android_test.py.

36)	We need to transfer the program to the sdcard of the Android Virtual Device to see if it runs on the Android platform. For this issue the following command in the command prompt:
	    adb push android_test.py /sdcard/sl4a/scripts

37) 	Now open the Sl4a app in the Android Virtual Device. Along with the pre-installed scripts, the program android_test.py should now be listed. Click on that and select the wheel button to see if it displays the message.

Now you can get out and get going with Android programming using Python. Happy coding :-)
