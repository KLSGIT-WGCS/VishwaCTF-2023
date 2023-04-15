# **Writeup - VishwaCTF**

* Category **web** 
* Name **aLive** 
* Difficulty **Medium**


## Description

In my college level project I created this website that tells us if any domain/ip is active or not. But there is a catch.

<img width="1324" alt="image" src="https://user-images.githubusercontent.com/121932742/232243936-dce05fad-bcf9-43a6-a545-90b24288aacb.png">



## **Solution**

The proper method to solve this challenge was doing a **Blind Command Injection**.

Try to put ;id and see what happens. You have to use **netcat** and send the ;ls command. You'll see that there's a file called "flag.txt". 

To print the flag, we can use the **cat** command or we can access to the directory (add /flag.txt to the URL). 

<img width="1030" alt="image" src="https://user-images.githubusercontent.com/121932742/232244112-9db4bf0c-79b4-4651-b9cd-5c950a6da4b2.png">


flag: **VishwaCTF{b1inD_cmd-i}**
