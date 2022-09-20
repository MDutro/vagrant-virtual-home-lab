Commands:

`vagrant up` start virtual machine(s) and run ansible playbook if running for the first time
`vagrant provision` run ansible playbook on a machine that has already been created

On Fedora - if ansible throws errors related to hostname resolution, run `hostnamectl set-hostname hostname.newdomain.local`

