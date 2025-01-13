# My WSL note

To list the installed `wsl` distros.

```powershell
wsl -l -v
```

To shutdown the `wsl` instance.

```
wsl --shutdown
```

Access the web server in `wsl2` from another PC on the same network (Wi-Fi/LAN)<sup>[\[1\]](https://www.nextofwindows.com/allow-server-running-inside-wsl-to-be-accessible-outside-windows-10-host)</sup>:

```
netsh interface portproxy add v4tov4 listenport=3000 listenaddress=0.0.0.0 connectport=3000 connectaddress=172.x.x.x
```

Change the `connectaddress` to your `wsl2`'s IP address, which you can find using `ifconfig` or `ip -s address`.
