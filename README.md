# pagekite-config
This repository contains a sample pagekite config files for frontend and backend

If you want to run your own fronend service in some public cloud, you need to install pagekite following the below steps

https://pagekite.net/wiki/Howto/GNULinux/ConfigureYourSystem/

once you installed, you can find all the pagekite config files under the directory ( in Ubuntu machine ) 

```
/etc/pagekite.d
```

you can use the sample frontend in this repo to kick start your setup !!

# To use self signed certificate

Generate selsigned cert in your machine where you have installed pagekite using the below commands. Below command will generate three files under the directory /etc/pagekite.d, you can change the location if you want

```
openssl req -new -x509 -keyout /etc/pagekite.d/site-key.pem \
    -out /etc/pagekite.d/site-cert.pem -days 365 -nodes
  cat /etc/pagekite.d/site-key.pem /etc/pagekite.d/site-cert.pem \
    |tee /etc/pagekite.d/frontend.pem
```

Then, add the tls-endpoint in the 20_frontends.rc file including the path of your frontend.pem file for Pagekite

```
tls_endpoint=*.your-domain.com:/path/to/frontend.pem

```

# Running your backend 

You can run your backends in any machine like windows, linux or mac, before that download the pagekite.py file to run your backends from here https://pagekite.net/downloads

Your backend config file should be ~/.pagekite.rc under MacOS and linux, or C:\Users\your-username\pagekite.cfg under Windows

Then, you can run your backend by below command to access your site via http(s)://xyz.your-domain.com


```
python pagekite.py

```

If you use self-signed cert, your browser will warn you to accept the risk of the certificate. We suggest to use letsencrypt free SSL certificate to run your service.







