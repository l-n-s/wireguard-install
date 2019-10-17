# wireguard-install

[WireGuard](https://www.wireguard.com) [road warrior](http://en.wikipedia.org/wiki/Road_warrior_%28computing%29) installer for Ubuntu 18.04 LTS, Debian 9 and CentOS 7.

This script will let you setup your own VPN server in no more than a minute, even if you haven't used WireGuard before. It has been designed to be as unobtrusive and universal as possible.

## Usage

Run the script and follow the assistant:

```
wget https://raw.githubusercontent.com/l-n-s/wireguard-install/master/wireguard-install.sh -O wireguard-install.sh
bash wireguard-install.sh
```

Once it ends, you can run it again to add more users. Reboot your server to apply all settings.

## Options

The script can be configured by setting the following environment variables:

* INTERACTIVE - if set to "no", the script will not prompt for user input
* PRIVATE\_SUBNET - private subnet configuration, "10.9.0.0/24" by default
* SERVER\_HOST - public IP address, detected by default
* SERVER\_PORT - listening port, picked random by default
* CLIENT\_DNS - comma separated DNS servers to use by the client

## Setting up clients

### Ubuntu PC

Install WireGuard and reboot your computer:

    sudo add-apt-repository ppa:wireguard/wireguard -y && sudo apt update && sudo apt install wireguard resolvconf -y
    sudo reboot

Copy the file `/root/client-wg0.conf` from a remote server to your local PC path `/etc/wireguard/wg0.conf` and run 
`sudo systemctl start wg-quick@wg0.service`

To show VPN status, run `sudo wg show`.

## Credits

Inspired by [Nyr's openvpn-install](https://github.com/Nyr/openvpn-install).
