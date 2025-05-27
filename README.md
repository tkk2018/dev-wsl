#### To list the installed `wsl` distros.

```powershell
wsl -l -v
```

#### To shutdown the `wsl` instance.

```
wsl --shutdown
```

#### Access the web server in `wsl2` from another PC on the same network (Wi-Fi/LAN)<sup>[\[1\]](https://www.nextofwindows.com/allow-server-running-inside-wsl-to-be-accessible-outside-windows-10-host)</sup>

Set up port proxy to redirect the request from the windows to the wsl2.

```powershell
netsh interface portproxy add v4tov4 listenport=3000 listenaddress=0.0.0.0 connectport=3000 connectaddress=172.x.x.x
```

| Option           | Description                                                    |
| ---------------- | -------------------------------------------------------------- |
| `listenport`     | The port on the Windows machine that accepts requests.         |
| `listenaddress`  | Set to `0.0.0.0`, which represents the Windows machine itself. |
| `connectport`    | The port on the target machine (in this case, `wsl2`).         |
| `connectaddress` | The IP address of the target machine (in this case, `wsl2`).   |

Change the `listenport`, `connectport` and `connectaddress` to your `wsl2`'s IP address, which you can find using `ifconfig` or `ip -s address`.

Next, restart the wsl by using `wsl --shutdown`.

Last, set up the inbound firewall rule for the port in Windows Defender Firewall with Advanced Security _if neccessary_.

To reset the `portproxy`
```powershell
netsh interface portproxy reset
```
