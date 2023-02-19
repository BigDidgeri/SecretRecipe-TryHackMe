# SecretRecipe-TryHackMe # 
## Q1 - What is the Computer Name of the Machine found in the registry? ##
```JAMES``` SYSTEM\ControlSet001\Control\ComputerName

## Q2 - When was the Administrator account created on this machine? (Format: yyyy-mm-dd hh:mm:ss) ##
```2021-03-17 14:58:48``` Click on users and it will show you all the values of each user.
![image](https://user-images.githubusercontent.com/18509521/219844209-debf27d6-b491-45fb-8852-683c0b9adcb8.png)

## Q3 - What is the RID associated with the Administrator account? ##
```500``` We can I dentify the user RID by navigating to SAM\Domains\Account\Users\000001F4 the last 4 bits is the RID of the user in hex, put that into a calculator and you will retrieve the RID.
![image](https://user-images.githubusercontent.com/18509521/219843649-5c3fa295-7c9a-494e-a33f-969d3081afe8.png)

## Q4 - How many User accounts were observed on this machine? ##
```7``` Just count the users.
![image](https://user-images.githubusercontent.com/18509521/219843712-e293a0e8-32f3-4de6-b8ea-266c009cc463.png)

## Q5 - There seems to be a suspicious account created as a backdoor with RID 1013. What is the Account Name? ##
```bdoor```
![image](https://user-images.githubusercontent.com/18509521/219844278-6988c811-90c7-4137-b26c-685d7cbcdef6.png)

## Q6 - What is the VPN connection this host connected to? ##
I went to go check the network interfaces at ```SYSTEM\ControlSet001\Services\Tcpip``` and found ```tapprotonvpn``` just above it. This indicates ```ProtonVPN`` is the vpn being used. However it can also be found at ```SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList```
![image](https://user-images.githubusercontent.com/18509521/219844686-068a7fae-a72c-4a36-98b2-2306a21b795e.png)
![image](https://user-images.githubusercontent.com/18509521/219844765-d095c199-0a7f-4e03-9cd9-6c47578becdb.png)

## Q7 - When was the first VPN connection observed? (Format: YYYY-MM-DD HH:MM:SS) ##
```2022-10-12 19:52:36```
![image](https://user-images.githubusercontent.com/18509521/219844815-9127fa77-77d7-4ebd-90c7-31a99819648c.png)

## Q8 - There were three shared folders observed on his machine. What is the path of the third share? ##
```C:\RESTRICTED FILES``` This is located at SYSTEM\ControlSet001\Services\LanmanServer\Shares
![image](https://user-images.githubusercontent.com/18509521/219904942-c0f0cf40-1eba-4e6b-87f6-1d11a2266fda.png)

## Q9 - What is the Last DHCP IP assigned to this host? ##
```172.31.2.197``` This can be found at SYSTEM\ControlSet001\Services\\Tcpip\Parameters\Interfaces
![image](https://user-images.githubusercontent.com/18509521/219905038-d5a51dc5-6d8a-49c8-8c1f-15862457b3c5.png)

## Q10 - The suspect seems to have accessed a file containing the secret coffee recipe. What is the name of the file? ##
```secret-recipe.pdf``` This can be located at NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs
![image](https://user-images.githubusercontent.com/18509521/219905217-8c8f7483-0917-4ef9-ae68-fdc5a41167f3.png)

## Q11 - The suspect ran multiple commands in the run windows. What command was run to enumerate the network interfaces? ##
```pnputil /enum-interfaces``` This can be located at NTUSER.dat\Software\Microsoft\Windows\CurrentVersion\Explorer\RunMRU
![image](https://user-images.githubusercontent.com/18509521/219905292-c68f22e8-7227-4035-a530-fbc407fd8f46.png)


## Q12 - In the file explorer, the user searched for a network utility to transfer files. What is the name of that tool? ##
```netcat``` wordwheelquery saves all searches ran in explorer on the computer. This can be found at NTUSER.dat\Software\Microsoft\Windows\CurrentVerion\Explorer\WordWheelQuery
![image](https://user-images.githubusercontent.com/18509521/219905286-d66449fe-58e9-4447-8e02-6def89d10db3.png)

## Q13 - What is the recent text file opened by the suspect? ##
```secret-code.txt``` This can be found at NTUSER.dat\Software\Microsoft\CurrentVersion\Explorer\RecentDocs\.txt
![image](https://user-images.githubusercontent.com/18509521/219905335-447531b2-805a-4a8e-b4f3-762aa9e2a0c5.png)

## Q14 - How many times was Powershell executed on this host? ##
```3``` This can be found at SYSTEM\CurrentControlSet\Control\Session Manager\AppCompatCache and search for powershell among all the entries.
![image](https://user-images.githubusercontent.com/18509521/219905620-819adf3b-bce1-4f81-bbe6-ac4755b85ace.png)

## Q15 - The suspect also executed a network monitoring tool. What is the name of the tool? ##
```wireshark```This can be found at SYSTEM\ControlSet001\Services\BAM\State\UserSetting\{SID}

## Q16 - Registry Hives also notes the amount of time a process is in focus. Examine the Hives. For how many seconds was ProtonVPN executed? ##
```343``` This can be found in UserAssist located at NTUSER.DAT\Software\Microsoft\Windows\Currentversion\Explorer\UserAssist\{CEBFF5CD-ACE2-4F4F-9178-9926F41749EA}\Count
![image](https://user-images.githubusercontent.com/18509521/219906408-b9d8c980-0ac2-4271-9911-f416706725a0.png)


## Q17 - Everything.exe is a utility used to search for files in a Windows machine. What is the full path from which everything.exe was executed? ##
```C:\Users\Administrator\Donwloads\Tools\Everything\Everything.exe``` This can be found at SYSTEM\ControlSet001\Services\BAM\State\UserSetting\{SID}
![image](https://user-images.githubusercontent.com/18509521/219906015-b185c028-aa5b-4622-b226-05f33a92c441.png)



