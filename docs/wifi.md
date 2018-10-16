# WiFi

Students have an open access to WiFi connection at school. EPITA provides two
differents networks with various specifications detailled below.

```nohighlight
Your Bocal logins are required to connect to the WiFi network.
```

## IONIS

The IONIS WiFi hotspot **requires a 5 Ghz WiFi card**. The IONIS WiFi is
recommended as it provides a faster and more stable connection.

To connect on IONIS, follow these steps:

1. Connect to the IONIS WiFi hotspot
2. You will be asked for your logins. You need to log with your epita's email address and *Bocal*'s password.

## Ionis Portal

Ionis Portal is an open WiFi access handled by the Bocal.

**Unlike IONIS, you will have to enter your credentials each time you want to
use the WiFi network.**

To connect on Ionis Portal, follow these steps:

1. Connect to the Ionis Portal WiFi hotspot
2. Open your web browser, a connection page should open-up (if not, open a website using **http**).
3. Login with your *Bocal* logins
4. Wait a few seconds before the connection is verified and established.

## Archlinux configuration

This section assumes you want to connect to the IONIS WiFi on an Archlinux
distribution, and have an activated WiFi interface.
To get the name of your WiFi interface you can type: `$ iw dev`.

This configuration is using _netctl_, a profile-based network manager
for archlinux.
Thus, you will have to configure a network _profile_. A simple profile is
presented below. For more information, please visit the
[archlinux wiki on netctl](wiki.archlinux.org/index.php/netctl).

1. Create a file in `/etc/netctl/`. Its name should be self-explanatory. A good
   name would be \<interface\>-IONIS.
2. Fill it with the following configuration:
```sh
Description='EPITA IONIS profile'
Interface=<interface>
Connection=wireless
Security=wpa-configsection
IP=dhcp
WPAConfigSection=(
    'ssid="IONIS"'
    'key_mgmt=WPA-EAP'
    'eap=PEAP'
    'identity="<epita_email_address>"'
    'password="<bocal_password>"'
)
```
3. Start the profile.
`$ netctl start <profile_name>`
You can also enable it to make it start at boot.
`$ netctl enable <profile_name>`

If you wish to avoid having a password stored in plain text, you may want to
try _wpa\_passphrase_ to make a pre-shared key instead, calculated from the
passphrase and the SSID. Please refer to this
[netctl section](https://wiki.archlinux.org/index.php/netctl#Obfuscate_wireless_passphrase).

You can find configuration examples in `/etc/netctl/examples/`.
