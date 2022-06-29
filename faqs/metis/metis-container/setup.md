---
description: How to setup your Metis Container
---

# Setup

### Connecting

1\.     Connect power and network cable to ‘top’ Raspberry Pi, power on with the push button switch

2\.     Find the container's IP address by looking at your router’s information page or by using a network scanner

3\.     SSH to the device by using Putty (Windows) or Terminal (MacOS/Linux) by using the username \``ubuntu`\` and the password \``ubuntu`\`

4\.     If you want Jupiter and Metis installed via script, copy and paste this into your terminal window:

`wget -O - https://gist.githubusercontent.com/sigwo/85809f9170de9876fbf279d910d791cd/raw/042820f52b252c2981274c5c9fbac5d5a1fbddb4/buildMetis.sh | bash`

_Note: If you want to manually install the applications and setups, please proceed with the next section. If you use the script above, skip to 'Configure Metis'_

## Let’s update and install, the manual way

1\.     After connecting, type `sudo apt update; sudo apt upgrade -y` to pull new updates to the underlying Linux operating system on the Raspberry Pi

2\.     After this process completes (you may have to answer a couple questions), type in `sudo reboot`

3\.     Now you are ready to install the Jupiter software!

### Install Jupiter

1\.     The Jupiter install guide is located here:  [install-jupiter](../../../documentation/install-jupiter/ "mention")

### Configure Metis

2\.     Follow the install guide located here: [configuration.md](../configuration.md "mention")

### Swap size (4GB version)

1\.     Edit the file `/etc/dphys-swapfile` and modify the variable `CONF_SWAPSIZE`:

a.     Make the size `4096`

b.     Save the file

![Change 2048 to 4096](<../../../.gitbook/assets/Screen Shot 2022-02-16 at 11.00.44 PM.png>)

Reboot the Raspberry Pi and your Jupiter node and Metis node will be up and running! If this is as far as you go, you have the most private messaging system available! Get your family and friends on Metis today!

_Note: If you would like to install your own Jitsi instance instead of using the public version located at meet.jit.si, follow this guide. There are some advanced techniques below so grab a drink and lots of patience. Send us an email at_ [_support@sigwo.com_](mailto:support@sigwo.com) _if you need assistance or have any questions. We recommend other apps such as Jitsi, iO, or a Home Assistant install to be installed on the 2nd Raspberry Pi._
