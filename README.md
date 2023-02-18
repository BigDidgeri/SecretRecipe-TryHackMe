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

