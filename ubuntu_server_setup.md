# Setting up k3s on Ubuntu

## Allow SSH connection
1. `sudo ufw default deny incoming`
2. `sudo ufw default allow outgoing`
3. `sudo ufw allow OpenSSH`
4. `sudo ufw enable`

## Adding sudoer
1. `adduser tddninja`
2. `usermod -aG sudo tddninja`

## Disable ssh root login
1. `sudo vim /etc/ssh/sshd_config`
2. update ~~`PermitRootLogin yes`~~ to `PermitRootLogin no`
3. `sudo systemctl restart ssh`

## [Install RKE2](https://docs.rke2.io/install/quickstart)
1. `curl -sfL https://get.rke2.io | sudo sh -`
2. `sudo systemctl enable rke2-server.service`
3. `sudo systemctl start rke2-server.service`
4. Optionally follow logs to see the status: `sudo journalctl -u rke2-server -f`
