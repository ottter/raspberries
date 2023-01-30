# [raspberries](https://github.com/ottter/raspberries/wiki)

Repo to contain all the scripts, configs, and instructions I use to build out my RPi cluster. I've built one several \
times before without documentation and it's always a mess to bring it back online if anything goes wrong. Hopefully \
this will resolve that issue for future screwups.

My goals with this project are *Agile* and subject to change. I aim to write this so that anyone reading it may understand.

Check out the [wiki](https://github.com/ottter/raspberries/wiki) for the full writeup!

## Goals

✔️: Free space\
✔️: Ansible playbook to configure Pis\
❌: K3s running\
❌: PiHole running

## Server List

| Hostname   |  Hardware  |  IP  |  Status   |
|------------|------------|------|-----------|
| localhost  | WSL        | .200 | online    |
| hades      | RPi 3b     | .201 | online    |
| persephone | RPi 3b     | .202 | online    |
| nyx        | RPi Zero W | .203 | online    |
| charon     | TBD        | .204 | TBD       |

## Quickstart

Process is better outlined in the wiki. This just for basic server setup before any K3s tomfoolery. This *won't* work \
without SSH keys set up as outlined [HERE](https://github.com/ottter/raspberries/wiki#configuring-ssh-for-ansible).

> clone the repo into your home directory and then `cd` into the new directory

```console
git -C $HOME clone -b main https://github.com/ottter/raspberries.git && cd "$HOME/$(basename "$_" .git)"
```

Make sure `hosts.txt` is using the desired IPs and hostname, and update `inventory.yml` to match. There are better ways \
to do this, especially at scale, but this works for me for now. I will improve it later.

> `setup-manager` only need to be ran first time, when a new server is added, or when SSH keys need to be recreated.

```console
ansible-playbook playbooks/setup-manager.yml -kK
```

> After initialization, `config-clients` will be the primary playbook that should be ran.

```console
ansible-playbook playbooks/config-clients.yml
```

## Important Links

[Raspberry Pi Imager](https://www.raspberrypi.com/software/) makes everything easier compared to back in the day.
 Make sure to install the Lite OS version. Also configure settings to set up user and WiFi before writing to SD card.

[Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) is going to be used to
 configure each of the Pi nodes. I am going to be using my personal computer as the control node using WSL, which means
 Ansible does not need to be installed on the managed (pi) nodes.

[Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install) to harness the power of Linux
 in Windows.

 [Pi-hole](https://pi-hole.net/) for a network-side ad blocker

 [K3s](https://k3s.io/) is a lightweight kubernetes tool to help manage the entire cluster
