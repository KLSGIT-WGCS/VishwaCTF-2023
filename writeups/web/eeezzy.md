# eeezzy
- Challenge Name : eeezzy
- Difficulty :  Easy

## Challenge Description
I forgot my login details again!



## Methodology
A web instance was provided to us where we needed to get the flag. 

![image](https://user-images.githubusercontent.com/121932742/231846273-3ac014d2-50b9-4996-8bce-6185bd400f25.png)

Lets see what's given for us, like we do in our math and physics numericals.

We have two things one is login form and view source code option in the right bottom.

```
<?php  
  
    session_start();    $_SESSION['status']=null;    $flag="";  
    try {  
        if (isset($_GET['username']) && isset($_GET['password'])) {  
            if (strcmp($_GET['username'], $flag)==0 && strcmp($_GET['password'], $flag)==0)                $_SESSION['status']=$flag;  
            else                $_SESSION['status']="Invalid username or password";  
        }  
    } catch (Throwable $th) {        $_SESSION['status']=$flag;  
    }  
  
?>
```

So we have something fishy over here...

The code has stringcompare vulnerablity known as strcmp()

Find more about it here https://www.doyler.net/security-not-included/bypassing-php-strcmp-abctf2016

Now enter some random strings in User and Pwd form or can even submit [SPACE] to avoid confusions intercepting it in URL.

I intercepted the request in the login form and updated this
**GET /?username=admin&password=admin&submit=Login HTTP/2__**
To
**GET /?username=&password[]=&submit=Login HTTP/2**
for example if its challenge.com/?username=admin&password=admin&submit=Login
i changed it to challenge.com/?username=&password[]=&submit=Login

Here is the flag in the form of error

<img width="1436" alt="image" src="https://user-images.githubusercontent.com/121932742/231860272-a9c5e469-4bfa-4c24-a8d8-34b529592302.png">

**VishwaCTF{5t0p_c0mp4r1ng}**


