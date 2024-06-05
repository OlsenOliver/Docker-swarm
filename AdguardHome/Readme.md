You may experience an error saying that port 53 is already in use, which is due DNSStubListener.

Deactivate DNSStubListener and update DNS server address. Create a new file: /etc/systemd/resolved.conf.d/adguardhome.conf (create a /etc/systemd/resolved.conf.d directory if necessary) with the following content:
´´´
sudo mkdir /etc/systemd/resolved.conf.d
sudo nano /etc/systemd/resolved.conf.d/adguardhome.conf
´´´
Add the following
´´´
[Resolve]
DNS=127.0.0.1
DNSStubListener=no
´´´
Specifying 127.0.0.1 as DNS server address is necessary because otherwise the nameserver will be 127.0.0.53 which doesn't work without DNSStubListener.

Activate another resolv.conf file:
´´´
sudo mv /etc/resolv.conf /etc/resolv.conf.backup
sudo ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf
´´´
Restart DNSStubListener:
´´´
sudo systemctl restart systemd-resolved
´´´