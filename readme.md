## Contents

* [SSH](#ssh)
  * [Sshuttle](#ssh-sshuttle)
  * [Socks](#ssh-socks)
  * [Tunnel](#ssh-tunnel)
* [Books](#books)
* [Awesome Lists](#awesome-lists)
* [Other Lists](#other-lists)






## SSH

### [Sshuttle](https://github.com/apenwarr/sshuttle/tree/master) <a id="ssh-sshuttle"/>

`sshuttle` combines an `ssh` tunnel with a system wide proxy, sometimes called a poor mans VPN.

On a debian based system, install `sshuttle` as root with:  
`apt-get install sshuttle`  
For a later version:  
`git clone git://github.com/apenwarr/sshuttle`  
After the server you intend to tunnel though has `sshd` running, from your local machine, run:  
```bash
# Syntax:
sshuttle --dns -vvr <proxy-user-account>@<proxy> 0/0
# Example:
sshuttle --dns -vvr kim@myproxy.net 0/0
```
Now all network traffic is `ssh` proxied through the `proxy` server, including DNS.

Test with: [http://ifconfig.me/](http://ifconfig.me/)  
Test if there is any leakage by visiting the DNS leak test [Web site](https://www.dnsleaktest.com/) and clicking on the Standard test button, you can also visit the IP/DNS Detect [site](http://ipleak.net/).

`-v` is just additional verbosity.  
`-r`, `--remote`_`=[username@]sshserver[:port]`_ _is the remote hostname and optional username and ssh port number to use for connecting to the remote server._ 
`0/0` is short for `0.0.0.0/0`, which represents the subnets to route over the `ssh` tunnel. The usage of `0/0` routes all the traffic except DNS requests to the remote server.  
`--dns` will also proxy your DNS queries through the server you are tunneled to.

### Socks <a id="ssh-socks"/>
Setup socks proxy through `<proxy>`
```bash
ssh -D9090 <proxy-user-account>@<proxy>
```
* [http://linux.byexamples.com/archives/115/ssh-dynamic-tunneling/](http://linux.byexamples.com/archives/115/ssh-dynamic-tunneling/)

### Tunnel <a id="ssh-tunnel"/>
To forward (or tunnel) from one machine to another, you need to use the -L argument for Local port forwarding.  
`localhost` is the optional default `hostname`.  

```bash
# Syntax:
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

You can also **combine tunnel with socks proxy**:
```bash
# Syntax:
ssh -D9090 -L 127.0.0.1:9090:127.0.0.1:9050 <proxy-user-account>@<proxy>
```

## Books


## Awesome Lists


## Other Lists

* []() - .

## License

[![Creative Commons License](http://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/)

This work is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/)
