## Contents

* [SSH](#ssh)
  * [Socks](#ssh-socks)
  * [Tunnel](#ssh-tunnel)
* [Books](#books)
* [Awesome Lists](#awsome-lists)
* [Other Lists](#other-lists)






## SSH

### Socks {#ssh-socks}
Setup socks proxy through `<proxy>`
```bash
ssh -D9090 <proxy-user-account>@<proxy>
```
* [https://anapnea.net/tut_unix_ssh.php](https://anapnea.net/tut_unix_ssh.php)
* [http://linux.byexamples.com/archives/115/ssh-dynamic-tunneling/](http://linux.byexamples.com/archives/115/ssh-dynamic-tunneling/)

### Tunnel
To forward (or tunnel) from one machine to another, you need to use the -L argument for Local port forwarding.  
`localhost` is the optional default `hostname`.  

```bash
# Syntax
ssh -L [hostname:]<localport>:<localhost-name-on-remote-host>:<remoteport> <proxy-user-account>@<proxy>
# Example:
# Bind default proxy port (9090) to Tor port (9050) on proxy.net
# In this example, port 9050 is only accessible to the localhost interface of proxy.net
ssh -L 127.0.0.1:9090:127.0.0.1:9050 kim@myproxy.net
# If port 9050 was accessible to proxy.net interfaces other than localhost, then we could do the following:
ssh -L 127.0.0.1:9090:proxy.net:9050 kim@myproxy.net
```
From there, if Tor is listening on port `9050` of `proxy.net` and you set your browsers proxy to `localhost:9090` all browsing traffic will go through Tor, except DNS.

You can also do remote port forwarding by swapping the `-L` for `-R`, the rest of the command syntax stays the same. What this allows us to do is open a tunnel from a remote machine to our local machine. Further details can be seen [here](http://blog.trackets.com/2014/05/17/ssh-tunnel-local-and-remote-port-forwarding-explained-with-examples.html).

Details on tunneling RDP on my [blog post](https://blog.binarymist.net/2010/08/26/installation-of-ssh-on-64bit-windows-7-to-tunnel-rdp/).


## Books


## Awesome Lists


## Other Lists

* []() - .

### License

[![Creative Commons License](http://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/)

This work is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/)
