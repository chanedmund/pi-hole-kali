# pi-hole-kali
Altered basic-install.sh specifically for Kali Linux

Things you need to consider before running this file:
- I did not create this installer
- I simply edited it so that it would work with "unsuported" Kali Linux
- You MUST ALREADY have a static IP or static DHCP reservation for your pi-hole server
- You can only use the pi-hole as a DNS server instead of DHCP server, which is how it works best anyway.

I would advise that you read over all of the files before you install them.

```
git clone https://github.com/oldjamey/pi-hole-kali.git
cd pi-hole-kali && sudo bash basic-install.sh
```

**Edit:**

The basic-install.sh is for an older version, and the upgrade didn't work, so I added additional files in order to complete a working upgrade.
If you have any trouble after running the install and the upgrade, just submit an issue, and I will look into it.

To run/upgrade to the latest version after running the install script with the commands above, run the following commands:

```
sudo cp update.sh /opt/pihole/ && chmod +x /opt/pihole/update.sh
sed 's/dhcpcd5 //' '/etc/.pihole/automated install/basic-install.sh'
pihole -up
sed 's/dhcpcd5 //' '/etc/.pihole/automated install/basic-install.sh'
```

^ Running the last `sed` command should allow you to run `pihole -up` in the future without the script crapping out.

(Just remember to run it again after running `pihole -up` the next time as well.)

