title: Introduction to self-hosting with YunoHost
class: animation-fade
layout: true

---

class: impact

# Introduction to Self‑Hosting with YunoHost

---

# Disclaimer

- This workshop was designed for beginner with little technical knowledge!
- Purists: sorry about the few technical shortcuts!

---

# Contact

- **Mastodon**: cybre.space/aleks
- **GitHub**: github.com/alexAubin
- **Matrix**: @Alekswag:matrix.org
- **IRC**: Find me on #yunohost on irc.freenode.org
- I also spend a lot on time on forum.yunohost.org

---

# Plan

## Boring part (~ 30 min)

- Generalities about self-hosting and YunoHost
- Some technical notions

## Cool part (~ 1h30)

- Hands-on !
- Install YunoHost on a VPS
- Play with apps, email, and so on

---

# Self-Hosting

- Having **your very own server**
    - a computer connected 24/7 that manages services like email, websites, file sync, ...
- Being **autonomous with your own data and services**
    - kinda similar to growing your own vegetables

.center[
![](img/garden.jpg)
]

---

# Self-Hosting

## Hardware

- **At home** ("true" self-hosting)
    - ARM-board (Raspberry-Pi like)
    - Old computer / laptop

- **On a remote server**
    - VPS (virtual private server)

---

.center[
![](img/raspberrypi.jpg)
![](img/oldcomputer.jpg)
]

.center[
![](img/datacenter.jpg)
]

---

<br>
<br>
<br>

.center[
**But what can you hope to do**

**with a RaspberryPi ?**
]

---

# Self-Host: a blog

.center[
![](img/blog.png)
]

---

# Self-Host: file cloud, contacts/calendar

.center[
![](img/nextcloud.png)
]

---

# Self-Host: a task manager

.center[
![](img/wekan.png)
]

---

# Self-Host: emails

.center[
![](img/rainloop.png)
]

---

# Self-Host: mailing lists

.center[
![](img/mailman.jpg)
]

---

# Self-Host: social media

.center[
![](img/mastodon.png)
]

---

# Self-Host: your own website?

.center[
![](img/yoloswagteam.png)
]

---

# Self-Hosting

## Why not just use Google and Facebook?

- **Political**
    - fight the GAFAM hegemony, escape surveillance capitalism
    - reclaim control (and responsability!) over your data and services
    - contribute to build a free / open / decentralized internet and save the wurld from cyberdistopia

- But also: **fun**, **pedagogical**

---

# Self-Hosting

## Public

- Individuals
- Group of friends
- Small association / club
- Small enterprise / company
- Small/medium-scale CHATONS / librehosters (10-100 users)

---

.center[
![](img/rainbow.jpg)
]

---

<br>

.center[
![](img/ni.png)
]

---

<br>

.center[
![](img/toocomplicated.png)
]

---

<br>

# Server administration is madness

- Requires **lot of technical knowledge / skills**
- And takes **hell of a time anyway**
- Evebody **somewhat reinvents the wheel everyday**
    - read the same READMEs / tutorial and apply "by hand"
    - lack of standardized, accessible environnement

.center[
=> not accessible
]

---

<br>
<br>

.center[
![](img/nobodygottimeforthat.jpg)
]


---

<br>
<br>
<br>
<br>

.center[
**But one way or another, we should be able to**

**have simple, accessible interfaces for simple use cases**
]

---

<br>
<br>

.center[
![](img/yunohost.jpg)
]

---

# YunoHost

## "The Ubuntu of Self-Hosting"

Basically
- a standardized setup (Debian + Nginx + Postfix + ...)
- accessible abstractions and interfaces
- does what you would do by hand ... but automagically!

---

# YunoHost: naming

.center[
« Y U No Host »

![](img/dude_yunohost.jpg)
]

---

# YunoHost: naming

.center[
alternatively: « You (K)now Host »

<br>

![](img/iknowselfhosting.png)
]

---

# YunoHost: features

- ![](img/icon-debian.png) **Debian**-based (stable, robust, well-known)
- ![](img/icon-tools.png) Simple & clean **web administration interface**
- ![](img/icon-package.png) Install **apps** in just a few clicks & questions
- ![](img/icon-users.png) ![](img/icon-door.png) **Multi-users** with single sign-on (SSO) portal
- ![](img/icon-mail.png) ![](img/icon-messaging.png) **Email** and instant messaging (XMPP) out of the box
- ![](img/icon-medic.png) **Backups** (and restore!)
- Lots of other stuff for things to just works

---

# YunoHost

<br>

.center[
**Try it:**

**demo.yunohost.org**
]

---

# YunoHost: admin interface

.center[
![](img/admin.png)
]

---

# YunoHost: user portal

.center[
![](img/user_panel.png)
]

---

.center[
**YunoHost: ecosystem**
![](img/ecosystem.png)
]

---

class: impact

# Technical notions

---

# Technical notions

## Network

- basic understanding of the architecture
- global / local IP addresses
- domain name
- (ports, protocol)

## System

- what's a server
- SSH (remote control)
- basic command line usage

---

# Technical notions

## Disclaimer

- You don't need to master all of these
- It's mostly useful only during initial install

---

# Technical notions: network

## Internet architecture

.center[
![](img/internet.jpg)
]

---

# Technical notions: network

## Local network

.center[
![](img/localnetwork.png)
]

---

# Technical notions: network

## Global IP / Local IP

- IP adresses are used to identify *machines*
- **Global (or public) IP address** make sense on the "global" internet
    - typically given by your ISP to your router
    - ~shared by multiple devices
- **Local IP address** make sense only inside a local network (e.g. @ home)
    - typically looks like `192.168.x.y` or `10.0.x.y`
    - (related to the lack of IPv4 ?)

---

# Technical notions: network

## Domain name and DNS

.center[
![](img/dns.png)
]

---

# Technical notions: network

## Domain name and DNS

.center[
human-readable name <-> IP address
]

- As a **human, it's easier to remember** `wikipedia.org` rather than `91.198.174.192`
- **DNS resolvers** translate domain name to IP
- (Also stores some technical infos (ex: spam counter-measure stuff))
- You can:
   - **buy domain names on DNS *registrars* **(ex: Gandi.net)
   - or get some for free (ex: netlib.re, nohost.me)


---

# Technical notions: network

## (Ports)

- If IP adresses are like building adresses, **ports are like room numbers**
- Ports are used to specify **which program to talk to**
- ex:
   - `127.0.0.1 : 72839` talking to  `91.198.174.192 : 443`
   - your web browser <-----------------> wikipedia.org web server

---

# Technical notions: network

## (Protocols)

- Rules used by programs to talk to each other
    - *Hello, How are You?, Please, Thank you*
- Most known:
    - Web (HTTP, HTTPS): port 80 and 443
    - Email (SMTP, IMAP): port 25, 587, 993

---

# Technical notions: system

## Server (hardware)

- A machine dedicated to answering requests and serving stuff
   - web pages, mail inboxes, instant messaging, ...
- Typically on 24/7 and reachable on the internets

---

# Technical notions: system

## Command line interface

- Interacting with the system through "written orders" rather than clicks
- Happens in a terminal (or console)
- More technical, but also more efficient on various aspects...

```bash
# List files in the current folder
alex@shadow:~/dev/workshopYunohost$ ls -l
total 28
drwxr-xr-x 2 alex alex 4096 Dec 26 23:36 dist
-rw-r--r-- 1 alex alex 7391 Dec 28 03:32 fiche.md
drwxr-xr-x 2 alex alex 4096 Dec 28 11:53 img
-rw-r--r-- 1 alex alex 7977 Dec 28 11:53 slides.md
drwxr-xr-x 2 alex alex 4096 Dec 28 03:20 template
```

---

# Technical notions: system

## Command line interface

- Interacting with the system through "written orders" rather than clicks
- Happens in a terminal (or console)
- More technical, but also more efficient on various aspects...

```bash
# Convert a jpg image to png
alex@shadow:~$ convert logo.jpg logo.png
```

---

# Technical notions: system

## Remote control with SSH

- Servers typically don't have graphical interface nor keyboards
- and usually not in the same room anyway !

.center[
-> need a way to remote control
]

---

# Technical notions: system

## Remote control with SSH

- SSH stands for Secure SHell and is a protocol (default on port 22)
- Remote control with command line interface

```bash
$ ssh root@11.22.33.44
The authenticity of host '11.22.33.44' can't be established.
RSA key fingerprint is SHA256:CuPd7AtmqS0UE6DwDDG68hQ+qIT2tQqZqm8pfo2oBE8.
Are you sure you want to continue connecting (yes/no)? █ 
```

---

# Technical notions: system

## Remote control with SSH

- SSH stands for Secure SHell and is a protocol (default on port 22)
- Remote control with command line interface

```bash
$ ssh root@11.22.33.44
The authenticity of host '11.22.33.44' can't be established.
RSA key fingerprint is SHA256:CuPd7AtmqS0UE6DwDDG68hQ+qIT2tQqZqm8pfo2oBE8.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '11.22.33.44' (RSA) to the list of known hosts.
Debian GNU/Linux 9
root@11.22.33.44's password:
```

---

# Technical notions: system

## Remote control with SSH

- SSH stands for Secure SHell and is a protocol (default on port 22)
- Remote control with command line interface

```bash
$ ssh root@11.22.33.44
The authenticity of host '11.22.33.44' can't be established.
RSA key fingerprint is SHA256:CuPd7AtmqS0UE6DwDDG68hQ+qIT2tQqZqm8pfo2oBE8.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '11.22.33.44' (RSA) to the list of known hosts.
Debian GNU/Linux 9
root@11.22.33.44's password:

Last login: Thu Oct  4 08:52:07 2018 from 90.63.229.46
root@35c3-0:~$ █
```

---

class: impact

# Let's get to work !

## Installing your first YunoHost server

---

# Let's get to work !

- Each of you will have **a VPS** (already bought them)

---

# Let's get to work !

- Each of you will have **a VPS** (already bought them)
- With a terminal, **connect using SSH** to your server



---

# Let's get to work !

- Each of you will have **a VPS** (already bought them)
- With a terminal, **connect using SSH** to your server
- Launch **YunoHost's install script**

---

# Let's get to work !

- Each of you will have **a VPS** (already bought them)
- With a terminal, **connect using SSH** to your server
- Launch **YunoHost's install script**
- Access the **YunoHost admin interface** on your server

---

# Let's get to work !

- Each of you will have **a VPS** (already bought them)
- With a terminal, **connect using SSH** to your server
- Launch **YunoHost's install script**
- Access the **YunoHost admin interface** on your server
- Run the **postinstall**
   - at this point you'll have to choose a **domain name** (ex: `something.netlib.re`)

---

# Let's get to work !

- Each of you will have **a VPS** (already bought them)
- With a terminal, **connect using SSH** to your server
- Launch **YunoHost's install script**
- Access the **YunoHost admin interface** on your server
- Run the **postinstall**
   - at this point you'll have to choose a **domain name** (ex: `something.netlib.re`)
- **Configure DNS records**

---

# Let's get to work !

- Each of you will have **a VPS** (already bought them)
- With a terminal, **connect using SSH** to your server
- Launch **YunoHost's install script**
- Access the **YunoHost admin interface** on your server
- Run the **postinstall**
   - at this point you'll have to choose a **domain name** (ex: `something.netlib.re`)
- **Configure DNS records**
- Add a **first user**

---

# Let's get to work !

- Each of you will have **a VPS** (already bought them)
- With a terminal, **connect using SSH** to your server
- Launch **YunoHost's install script**
- Access the **YunoHost admin interface** on your server
- Run the **postinstall**
   - at this point you'll have to choose a **domain name** (ex: `something.netlib.re`)
- **Configure DNS records**
- Add a **first user**
- Play with some **apps and email**, get to know YunoHost

---

# Let's get to work !

- Each of you will have **a VPS** (already bought them)
- With a terminal, **connect using SSH** to your server
- Launch **YunoHost's install script**
- Access the **YunoHost admin interface** on your server
- Run the **postinstall**
   - at this point you'll have to choose a **domain name** (ex: `something.netlib.re`)
- **Configure DNS records**
- Add a **first user**
- Play with some **apps and email**, get to know YunoHost
- ???
- **Enjoy your server!**

---

# Let's get to work !

- Each of you will have **a VPS** (already bought them)
- With a terminal, **connect using SSH** to your server
- Launch **YunoHost's install script**
- Access the **YunoHost admin interface** on your server
- Run the **postinstall**
   - at this point you'll have to choose a **domain name** (ex: `something.netlib.re`)
- **Configure DNS records**
- Add a **first user**
- Play with some **apps and email**, get to know YunoHost
- ???
- **Enjoy your server!**

(All of this is also detailed on `yunohost.org/install`


