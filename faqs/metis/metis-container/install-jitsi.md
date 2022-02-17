---
description: Install Jitsi on your Metis Container
---

# Install Jitsi

### Connecting to Metis Container

1. Open your SSH terminal and connect to your Metis Container's IP address
2.  Copy and paste&#x20;

    `sudo apt install gnupg2 nginx-full curl apt-transport-https -y`
3.  Copy and paste

    `sudo apt-add-repository universe; sudo apt update` and press `[ENTER]`

### **Domain of your server and set up DNS**

Decide what domain your server will use. For example, meet.example.org.

Set a DNS A record for that domain, using:

* your server's public IP address, if it has its own public IP; or
* the public IP address of your router, if your server has a private (RFC1918) IP address (e.g. 192.168.1.2) and connects through your router via Network Address Translation (NAT).

If your computer/server or router has a dynamic IP address (the IP address changes constantly), you can use a dynamic dns-service instead.

### Set up the Fully Qualified Domain Name (FQDN) (optional)

![FQDN setup](<../../../.gitbook/assets/Screen Shot 2022-02-16 at 9.25.21 PM.png>)

If the machine used to host the Jitsi Meet instance has a FQDN (for example meet.example.org) already set up in DNS, you can set it with the following command:

`sudo hostnamectl set-hostname meet.example.org`

Then add the same FQDN in the `/etc/hosts` file:

`127.0.0.1 localhost`

`x.x.x.x meet.example.org`

_Note: x.x.x.x is your server's public IP address_.

Finally on the same machine test that you can ping the FQDN with:

`ping "$(hostname)"`

If all worked as expected, you should see: meet.example.org

### Add the Jitsi package repository

This will add the jitsi repository to your package sources to make the Jitsi Meet packages available. Copy the commands and paste them into your SSH terminal.

`curl https://download.jitsi.org/jitsi-key.gpg.key | sudo sh -c 'gpg --dearmor > /usr/share/keyrings/jitsi-keyring.gpg'`

`echo 'deb [signed-by=/usr/share/keyrings/jitsi-keyring.gpg] https://download.jitsi.org stable/' | sudo tee /etc/apt/sources.list.d/jitsi-stable.list > /dev/null`

`sudo apt update`

### **Setup and configure your firewall**

The following ports need to be open in your firewall, to allow traffic to the Jitsi Meet server:

* 80 TCP - for SSL certificate verification / renewal with Let's Encrypt
* 443 TCP - for general access to Jitsi Meet
* 10000 UDP - for general network video/audio communications
* 22 TCP - if you access you server using SSH (change the port accordingly if it's not 22)
* 3478 UDP - for quering the stun server (coturn, optional, needs config.js change to enable it)
* 5349 TCP - for fallback network video/audio communications over TCP (when UDP is blocked for example), served by coturn

If you are using ufw, you can use the following commands:

`sudo ufw allow 80/tcp`

`sudo ufw allow 443/tcp`

`sudo ufw allow 10000/udp`

`sudo ufw allow 22/tcp`

`sudo ufw allow 3478/udp`

`sudo ufw allow 5349/tcp`

`sudo ufw enable`

Check the firewall status with:

`sudo ufw status verbose`

### **Forward ports via your router**

If you are running Jitsi Meet on a server [behind NAT](https://jitsi.github.io/handbook/docs/faq#how-to-tell-if-my-server-instance-is-behind-nat), forward the ports on your router to your server's IP address.

_Note_: _if participants cannot see or hear each other, double check your firewall / NAT rules._

### TLS Certificate

In order to have encrypted communications, you need a [TLS certificate](https://en.wikipedia.org/wiki/Transport\_Layer\_Security).

During installation of Jitsi Meet you can choose between different options:

1\.     The recommended option is to choose _**Generate a new self-signed certificate**_ and create a Lets-Encrypt Certificate later (see [below](https://jitsi.github.io/handbook/docs/devops-guide/devops-guide-quickstart#generate-a-lets-encrypt-certificate-optional-recommended)) (this will replace the self-signed certificate).

2\.     But if you want to use a different certificate or you want to choose a different challenge type of Let's Encrypt (see [below](https://jitsi.github.io/handbook/docs/devops-guide/devops-guide-quickstart#generate-a-lets-encrypt-certificate-optional-recommended) for details), you should create that certificate first and then install jitsi-meet and choose _**I want to use my own certificate**_.

3\.     You could also use the self-signed certificate but this is not recommended for the following reasons:

o   Using a self-signed certificate will result in warnings being shown in your users browsers, because they cannot verify your server's identity.

o   Jitsi Meet mobile apps _require_ a valid certificate signed by a trusted [Certificate Authority](https://en.wikipedia.org/wiki/Certificate\_authority) and will not be able to connect to your server if you choose a self-signed certificate.

### Install Jitsi Meet

_Note_: The installer will check if [Nginx](https://nginx.org) or [Apache](https://httpd.apache.org) are present (in that order) and configure a virtual host within the web server it finds to serve Jitsi Meet.

If you are already running Nginx on port 443 on the same machine, turnserver configuration will be skipped as it will conflict with your current port 443.

`sudo apt install jitsi-meet`

**SSL/TLS certificate generation:** You will be asked about SSL/TLS certificate generation. See [above](https://jitsi.github.io/handbook/docs/devops-guide/devops-guide-quickstart#tls-certificate) for details.

**Hostname:** You will also be asked to enter the hostname of the Jitsi Meet instance. If you have a domain, use the specific domain name, for example: `meet.example.org`. Alternatively you can enter the IP address of the machine (if it is static or doesn't change).

This hostname will be used for virtualhost configuration inside Jitsi Meet and also, you and your correspondents will be using it to access the web conferences.

### Access Control

**Jitsi Meet server:** _Note_: By default, anyone who has access to your Jitsi Meet server will be able to start a conference: if your server is open to the world, anyone can have a chat with anyone else. If you want to limit the ability to start a conference to registered users, follow the instructions to set up a [secure domain](https://jitsi.github.io/handbook/docs/devops-guide/secure-domain).

**Conferences/Rooms:** The access control for conferences/rooms is managed in the rooms, you can set a password on the webpage of the specific room after creation. See the User Guide for details: [https://jitsi.github.io/handbook/docs/user-guide/user-guide-start-a-jitsi-meeting](https://jitsi.github.io/handbook/docs/user-guide/user-guide-start-a-jitsi-meeting)

### Generate a Let's Encrypt certificate (optional, recommended)

In order to have encrypted communications, you need a [TLS certificate](https://en.wikipedia.org/wiki/Transport\_Layer\_Security).

![](<../../../.gitbook/assets/Screen Shot 2022-02-16 at 9.25.29 PM.png>)

The best method is to create a certificate that is signed by a [Certificate Authority](https://en.wikipedia.org/wiki/Certificate\_authority). This way you can avoid problems with a self-signed certificate (see [above](https://jitsi.github.io/handbook/docs/devops-guide/devops-guide-quickstart#tls-certificate) for details). The easiest way is to use [Let's Encrypt](https://letsencrypt.org). This certificate will also help you setup your Jupiter node for access outside, if you choose.

Simply run the following in your shell:

`sudo /usr/share/jitsi-meet/scripts/install-lets-encrypt-cert.sh`

Note that this script uses the [HTTP-01 challenge type](https://letsencrypt.org/docs/challenge-types/) and thus your instance needs to be accessible from the public internet on both ports 80 and 443. If you want to use a different challenge type, don't use this script and instead choose _**I want to use my own certificate**_ during `jitsi-meet` installation.



Jitsi's [Official Guide](https://jitsi.github.io/handbook/docs/devops-guide/devops-guide-quickstart)
