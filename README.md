Commands:

`vagrant up` start virtual machine(s) and run ansible playbook if running for the first time
`vagrant provision` run ansible playbook on a machine that has already been created

On Fedora - if ansible throws errors related to hostname resolution, run `hostnamectl set-hostname hostname.newdomain.local`

Virtualbox takes some special configuration to run on Fedora:

First install dependencies:
```
sudo dnf -y install @development-tools
sudo dnf -y install kernel-headers kernel-devel dkms elfutils-libelf-devel qt5-qtx11extras
```

Next, add the RPM repository provided by Virtualbox development:

```cat <<EOF | sudo tee /etc/yum.repos.d/virtualbox.repo 
[virtualbox]
name=Fedora $releasever - $basearch - VirtualBox
baseurl=http://download.virtualbox.org/virtualbox/rpm/fedora/36/\$basearch
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://www.virtualbox.org/download/oracle_vbox.asc
EOF
```

Add the GPG key:

`sudo dnf search virtualbox`

Install:

`sudo dnf install VirtualBox-6.1` or latest version if different.

Add your user to the virtualbox user group:

```
sudo usermod -a -G vboxusers $USER
newgrp vboxusers
id $USER
```
