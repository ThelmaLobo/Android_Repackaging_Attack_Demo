<h1>Demonstration of Android Repackaging Attack </h1>

<h2>Description</h2>
An Android repackaging attack is a type of cyberattack where a malicious actor takes a legitimate Android application (APK file), modifies it to include malicious code, and then redistributes it as if it were the original app. This process typically involves reverse-engineering the app, altering its code or resources, and repackaging it into a new APK file that looks and behaves similarly to the original but contains hidden malicious functionality.
<br />


<h2>Environments Used </h2>

- <b> Seed Ubuntu 16.4 </b>
- <b> Android 7.1 VM </b> 

<h2>Program walk-through:</h2>

<p align="center">
I have downloaded the seed VM machine from https://seedsecuritylabs.org/Labs_16.04/Mobile/Android_Repackaging/ and Android VM. Once these are downlaoded, we need to also download the smali code from this website. I have dowloaded MaliciousCode_Location.zip file for this exercise. Below screenshot shows the smali codes. We have also downloaded an Android application called Minimal To Do which is a simple tool for creating To-do lists.  : <br/>
<img src="https://i.imgur.com/oB5f5sj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once we have downloaded the apk file. We need to decompile the file as shown below. Once the de-compilation is completed, we will be injecting the Malicious code into the decompiled file and choose the location where we need to inject the malicious code.:  <br/>
<img src="https://i.imgur.com/w0GLBwt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://i.imgur.com/hLJBvQA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Below file "toodle" contains mutliple smali files. We will be copy the smali files like MaliciousCode.smali, SendData.smali and SendData$1.smali to the toodle directory containing multiple smali code as shown in the below screesnhot : <br/>
<img src="https://i.imgur.com/L5kB3vR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Here we have copied the smali files like MaliciousCode.smali, SendData.smali and SendData$1.smali : <br/>
 <img src="https://i.imgur.com/CX2fkfd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now let's make some changes to the MaliciousCode.smali file. I have added the path as ".class public Lcom/avjindersekhon/toodle/MaliciousCode;"
Also we will be making changes:  <br/>
<img src="https://i.imgur.com/1djAGUd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/mkmobFz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once we have made these changes, we move on to configuring the DNS onto the Android VM because smali code is going to collect the information of the victim and we will be demonstrating that on the Android VM. As shown below, this is our Android VM:  <br/>
<img src="https://i.imgur.com/cgODKHz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We will be making changes to the sysem/etc/hosts file as shown below. We will be adding the IP address of the Seed Ubuntu machine which is 10.0.2.15. It will be sending the location information from Android VM to Seed Ubuntu machine:  <br/>
<img src="https://i.imgur.com/8HVeynE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Iaq2mwK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once we have done that, we are now back to our Seed VM machine where we will be setting permissions in the AndroidManifest file. Here I have added the user permission which help the attacker to get the victim machine's real time location access (ACCESS_FINE_LOCATION, ACCESS_MOCK_LOCATION, INTERNET) :  <br/>
<img src="https://i.imgur.com/xYbO6Aa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/OsqEmCz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 Under the intent filter, we also have to set a particular time to track the details of when the victim was present at that location which we would be accessing :  <br/>
<img src="https://i.imgur.com/U59SBwn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once we have made the changes in the AndroidManifest file, we will re-compiling the file as below :  <br/>
<img src="https://i.imgur.com/eAkUJdH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We need to generate keys and provide the signature after re-compilation as shown below :  <br/>
<img src="https://i.imgur.com/ke3VM3m.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/nLHdtzy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 Now we will be connecting to the Android machine:  <br/>
<img src="https://i.imgur.com/9RBwfdf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 We will also have to download the Minimal To Do app on Android VM which is already done as shown below:  <br/>
<img src="https://i.imgur.com/dqxDywQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 We need to go to Setting > Search for that application (Minimal To Do) and enable the Permissions for that app :  <br/>
<img src="https://i.imgur.com/dqxDywQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/CNbKZDw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/RmEiv59.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 We need to go onto Mock Location. Remember, we had already added this location and provided access to our AndroidManifest File in the seed VM :  <br/>
<img src="https://i.imgur.com/MSf0Xy6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/I9bSyjl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/GyupMUe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Also, let's go to the Settings > Change the time as we had made changes in the AndroidManifest file as below :  <br/>
<img src="https://i.imgur.com/TxfiZy2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 We will be going back to the Seed VM and check if the attack was successful of the victim. We need to open the browser and logon to www.repackagingattacklab.com. This is where, we be tracking the victim's live location. As per the below screenshot, the live location of the victim is New York. This is because we had changed the mock location as New York on the Android VM  :  <br/>
<img src="https://i.imgur.com/PJxLzy8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 We again change the location to Paris on Android VM.  :  <br/>
<img src="https://i.imgur.com/Di74kte.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 On the Seed VM, we see that the location is changed. Hence, we can see that real-time location of the victim can be tracked by the attacker as shown below.
 We also changed the location to Agra. Hence, we can see that the real time locations are all tracked by the attacker:  <br/>
<img src="https://i.imgur.com/S9hwwax.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://i.imgur.com/I8GuHwy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://i.imgur.com/dSmHncb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 From this demonstration, we understand how the Android Repackaging Attack is being performed by the attacker. 
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
