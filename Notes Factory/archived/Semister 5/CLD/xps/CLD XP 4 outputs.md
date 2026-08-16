> [!attention] incase httpd not found
>   `httpd` isn’t available until you install it.

Run this:

```bash
sudo dnf install -y httpd
sudo systemctl enable --now httpd
```

After that, you can check if it’s running:

```bash
systemctl status httpd
```

And if you haven’t already, make sure your EC2 security group allows **HTTP (port 80)** from your IP or `0.0.0.0/0`.

---


MOD INSTANCE
```bash

A newer release of "Amazon Linux" is available.
  Version 2023.8.20250707:
  Version 2023.8.20250715:
  Version 2023.8.20250721:
  Version 2023.8.20250804:
Run "/usr/bin/dnf check-release-update" for full release and version update info
   ,     #_
   ~\_  ####_        Amazon Linux 2023
  ~~  \_#####\
  ~~     \###|
  ~~       \#/ ___   https://aws.amazon.com/linux/amazon-linux-2023
   ~~       V~' '->
    ~~~         /
      ~~._.   _/
         _/ _/
       _/m/'
Last login: Fri Aug  1 03:20:36 2025 from 13.233.177.5
[ec2-user@ip-172-31-44-70 ~]$ echo hello
hello
[ec2-user@ip-172-31-44-70 ~]$ sudo yum update -y
Last metadata expiration check: 0:08:47 ago on Fri Aug  8 03:08:33 2025.
=======================================================================================================================================================================
installation process "done"
=======================================================================================================================================================================
Dependencies resolved.
Nothing to do.
Complete!
[ec2-user@ip-172-31-44-70 ~]$ sudo systemctl start httpd
[ec2-user@ip-172-31-44-70 ~]$ sudo systemctl enable httpd
[ec2-user@ip-172-31-44-70 ~]$ sudo systemctl status  httpd
● httpd.service - The Apache HTTP Server
     Loaded: loaded (/usr/lib/systemd/system/httpd.service; enabled; preset: disabled)
    Drop-In: /usr/lib/systemd/system/httpd.service.d
             └─php-fpm.conf
     Active: active (running) since Fri 2025-08-08 03:08:28 UTC; 9min ago
       Docs: man:httpd.service(8)
   Main PID: 2003 (httpd)
     Status: "Total requests: 0; Idle/Busy workers 100/0;Requests/sec: 0; Bytes served/sec:   0 B/sec"
      Tasks: 177 (limit: 507)
     Memory: 18.0M
        CPU: 356ms
     CGroup: /system.slice/httpd.service
             ├─2003 /usr/sbin/httpd -DFOREGROUND
             ├─2014 /usr/sbin/httpd -DFOREGROUND
             ├─2015 /usr/sbin/httpd -DFOREGROUND
             ├─2016 /usr/sbin/httpd -DFOREGROUND
             └─2017 /usr/sbin/httpd -DFOREGROUND

Aug 08 03:08:28 ip-172-31-44-70.ap-south-1.compute.internal systemd[1]: Starting httpd.service - The Apache HTTP Server...
Aug 08 03:08:28 ip-172-31-44-70.ap-south-1.compute.internal systemd[1]: Started httpd.service - The Apache HTTP Server.
Aug 08 03:08:28 ip-172-31-44-70.ap-south-1.compute.internal httpd[2003]: Server configured, listening on: port 80
[ec2-user@ip-172-31-44-70 ~]$ sudo nano /var/www/html/index.html
[ec2-user@ip-172-31-44-70 ~]$ sudo nano /var/www/html/index.html
[ec2-user@ip-172-31-44-70 ~]$ sudo systemctl restart httpd
[ec2-user@ip-172-31-44-70 ~]$ sudo nano /var/www/html/wow.html
[ec2-user@ip-172-31-44-70 ~]$ sudo nano /var/www/html/wow.html
[ec2-user@ip-172-31-44-70 ~]$ sudo systemctl restart httpd
[ec2-user@ip-172-31-44-70 ~]$ sudo systemctl restart httpd
[ec2-user@ip-172-31-44-70 ~]$ ^

```


***
  PROBZ INSTANCE
```bash
   ,     #_
   ~\_  ####_        Amazon Linux 2023
  ~~  \_#####\
  ~~     \###|
  ~~       \#/ ___   https://aws.amazon.com/linux/amazon-linux-2023
   ~~       V~' '->
    ~~~         /
      ~~._.   _/
         _/ _/
       _/m/'
Last login: Fri Aug  8 03:39:09 2025 from 13.233.177.4
[ec2-user@ip-172-31-46-104 ~]$ sudo yum update -y
Last metadata expiration check: 0:07:14 ago on Fri Aug  8 03:34:15 2025.
Dependencies resolved.
Nothing to do.
Complete!
[ec2-user@ip-172-31-46-104 ~]$ sudo systemctl start httpd
Failed to start httpd.service: Unit httpd.service not found.
[ec2-user@ip-172-31-46-104 ~]$ cat /etc/os-release
NAME="Amazon Linux"
VERSION="2023"
ID="amzn"
ID_LIKE="fedora"
VERSION_ID="2023"
PLATFORM_ID="platform:al2023"
PRETTY_NAME="Amazon Linux 2023.8.20250804"
ANSI_COLOR="0;33"
CPE_NAME="cpe:2.3:o:amazon:amazon_linux:2023"
HOME_URL="https://aws.amazon.com/linux/amazon-linux-2023/"
DOCUMENTATION_URL="https://docs.aws.amazon.com/linux/"
SUPPORT_URL="https://aws.amazon.com/premiumsupport/"
BUG_REPORT_URL="https://github.com/amazonlinux/amazon-linux-2023"
VENDOR_NAME="AWS"
VENDOR_URL="https://aws.amazon.com/"
SUPPORT_END="2029-06-30"
[ec2-user@ip-172-31-46-104 ~]$ sudo dnf install -y httpd
Last metadata expiration check: 0:08:03 ago on Fri Aug  8 03:34:15 2025.
Dependencies resolved.
======================================================================

...
Installed:
  apr-1.7.5-1.amzn2023.0.4.x86_64                                     
  apr-util-1.6.3-1.amzn2023.0.1.x86_64                                
  apr-util-openssl-1.6.3-1.amzn2023.0.1.x86_64                        
  generic-logos-httpd-18.0.0-12.amzn2023.0.3.noarch                   
  httpd-2.4.64-1.amzn2023.0.1.x86_64                                  
  httpd-core-2.4.64-1.amzn2023.0.1.x86_64                             
  httpd-filesystem-2.4.64-1.amzn2023.0.1.noarch                       
  httpd-tools-2.4.64-1.amzn2023.0.1.x86_64                            
  libbrotli-1.0.9-4.amzn2023.0.2.x86_64                               
  mailcap-2.1.49-3.amzn2023.0.3.noarch                                
  mod_http2-2.0.27-1.amzn2023.0.3.x86_64                              
  mod_lua-2.4.64-1.amzn2023.0.1.x86_64                                

Complete!
[ec2-user@ip-172-31-46-104 ~]$ sudo systemctl start httpd
[ec2-user@ip-172-31-46-104 ~]$ sudo systemctl enable httpd
Created symlink /etc/systemd/system/multi-user.target.wants/httpd.service → /usr/lib/systemd/system/httpd.service.
[ec2-user@ip-172-31-46-104 ~]$ sudo systemctl status httpd
● httpd.service - The Apache HTTP Server
     Loaded: loaded (/usr/lib/systemd/system/httpd.service; enabled; >
     Active: active (running) since Fri 2025-08-08 03:42:39 UTC; 26s >
       Docs: man:httpd.service(8)
   Main PID: 28455 (httpd)
     Status: "Total requests: 0; Idle/Busy workers 100/0;Requests/sec>
      Tasks: 177 (limit: 1111)
     Memory: 12.9M
        CPU: 70ms
     CGroup: /system.slice/httpd.service
             ├─28455 /usr/sbin/httpd -DFOREGROUND
             ├─28456 /usr/sbin/httpd -DFOREGROUND
             ├─28457 /usr/sbin/httpd -DFOREGROUND
             ├─28458 /usr/sbin/httpd -DFOREGROUND
             └─28459 /usr/sbin/httpd -DFOREGROUND

Aug 08 03:42:39 ip-172-31-46-104.ap-south-1.compute.internal systemd[>
Aug 08 03:42:39 ip-172-31-46-104.ap-south-1.compute.internal systemd[>
Aug 08 03:42:39 ip-172-31-46-104.ap-south-1.compute.internal httpd[28>
...skipping...
● httpd.service - The Apache HTTP Server
     Loaded: loaded (/usr/lib/systemd/system/httpd.service; enabled; >
     Active: active (running) since Fri 2025-08-08 03:42:39 UTC; 26s >
       Docs: man:httpd.service(8)
   Main PID: 28455 (httpd)
     Status: "Total requests: 0; Idle/Busy workers 100/0;Requests/sec>
      Tasks: 177 (limit: 1111)
     Memory: 12.9M
        CPU: 70ms
     CGroup: /system.slice/httpd.service
             ├─28455 /usr/sbin/httpd -DFOREGROUND
             ├─28456 /usr/sbin/httpd -DFOREGROUND
             ├─28457 /usr/sbin/httpd -DFOREGROUND
             ├─28458 /usr/sbin/httpd -DFOREGROUND
             └─28459 /usr/sbin/httpd -DFOREGROUND

Aug 08 03:42:39 ip-172-31-46-104.ap-south-1.compute.internal systemd[>
Aug 08 03:42:39 ip-172-31-46-104.ap-south-1.compute.internal systemd[>
Aug 08 03:42:39 ip-172-31-46-104.ap-south-1.compute.internal httpd[28>

lines 1-19/19 (END)
[ec2-user@ip-172-31-46-104 ~]$ 
/inde^Cer@ip-172-31-46-104 ~]$ suo nano /var/www/html 
[ec2-user@ip-172-31-46-104 ~]$ sudo nano /var/www/html/index.html
[ec2-user@ip-172-31-46-104 ~]$ sudo systemctl restart httpd
[ec2-user@ip-172-31-46-104 ~]$ sudo nano /var/www/html
[ec2-user@ip-172-31-46-104 ~]$ sudo nano /var
[ec2-user@ip-172-31-46-104 ~]$ sudo nano /var/www/html/mello.html
[ec2-user@ip-172-31-46-104 ~]$ sudo nano /var/www/html/mello.html
[ec2-user@ip-172-31-46-104 ~]$ 

```
***

### outputs below not sorted

## noname has it~~~~





