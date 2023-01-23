# [raspberries](https://github.com/ottter/raspberries/wiki)

Repo to contain all the scripts, configs, and instructions I use to build out my RPi cluster. I've built one several \
times before without documentation and it's always a mess to bring it back online if anything goes wrong. Hopefully \
this will resolve that issue for future screwups.

My goals with this project are *Agile* and subject to change. I aim to write this so that anyone reading it may understand.

Check out the [wiki](https://github.com/ottter/raspberries/wiki) for the full writeup!

## Goals

✔️: Free space\
❌: Ansible playbook to configure Pis\
❌: PiHole running\
❌: K3s running

## Server List

| Hostname   | Hardware | Status |
|------------|----------|--------|
| hades      | RPi 3b   | TBD    |
| persephone | RPi 3b   | TBD    |
| nyx        | TBD      | TBD    |
| charon     | TBD      | TBD    |

## Important Links

[Raspberry Pi Imager](https://www.raspberrypi.com/software/) makes everything easier compared to back in the day.
 Make sure to install the Lite OS version. Also configure settings to set up user and WiFi before writing to SD card.

[Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) is going to be used to
 configure each of the Pi nodes. I am going to be using my personal computer as the control node using WSL, which means
 Ansible does not need to be installed on the managed (pi) nodes.

[Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install) to harness the power of Linux
 in Windows.
