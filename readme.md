## Contents

* [SSH](#ssh)
  * [socks](#ssh-socks)
* [Books](#books)
* [Awesome Lists](#awsome-lists)
* [Other Lists](#other-lists)






## SSH

### Socks
Setup socks proxy through `<proxy>`
```bash
ssh -D9090 <proxy-user-account>@<proxy>
```
[https://anapnea.net/tut_unix_ssh.php](https://anapnea.net/tut_unix_ssh.php)
[http://linux.byexamples.com/archives/115/ssh-dynamic-tunneling/](http://linux.byexamples.com/archives/115/ssh-dynamic-tunneling/)

### Tunnel
To forward (or tunnel) from one machine to another, you need to use the -L argument.  
`localhost` is the optional default `hostname`
```bash
ssh -L [hostname:]<localport>:<hostname>:<remoteport> <proxy-user-account>@<proxy>
# Example:
# Bind default proxy port (9090) to Tor port (9050) on proxy.net
ssh -L 127.0.0.1:9090:127.0.0.1:9050 kim@myproxy.net
```
From there, if Tor is listening on port `9050` of `proxy.net` and you set the browsers proxy to `localhost:9090` all browsing traffic will go through Tor, except DNS.

## Books


## Awesome Lists


## Other Lists

* []() - .

### License

[![Creative Commons License](http://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/)

This work is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/)
