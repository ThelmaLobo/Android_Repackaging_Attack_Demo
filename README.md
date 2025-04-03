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
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
