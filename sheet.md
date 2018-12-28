# Hands-on Introduction to Self-Hosting with YunoHost

## Setting up your first YunoHost server

This tutorial is somehow similar to what you would find in the official documentation on `https://yunohost.org/install`.

### Access your server

1. **Open a terminal**.
    - If you run Linux or MacOS, you should find this in the various accessories provided on your system.
    - If you are on Windows, you might want to download *MobaXterm* somewhere on the internet.

1. **SSH in your server**. Using the IP address provided to you, run the following command in your terminal : 
```
ssh root@11.22.33.44
```
(replacing the number with your IP address).

On Windows, create a new Session (type: SSH), input your IP in 'Hostname' and `root` as Username.
The system will ask you to check the server fingerprint to confirm its identity (usually people just type 'yes' though it's a bad security practice :/). Then you should enter the password `iloveyunohost`. Then you should see some ascii art popping up, as well as technical info, and a new command prompt like : `root@<some_name>:~# _`. You are now controlling your server through command line !

### Install yunohost 

- 2 - **Let's run YunoHost's installation script**. For various reasons (please trust the teacher ;)), we will setup a *testing* instance ! (Though this is slightly more complicated than the regular version). Enter the three following command carefully :
```
# wget https://install.yunohost.org -O install_script
# chmod +x install_script
# ./install_script -d testing
```
The last command effectively launches the installation and will take a few minutes. You might have to agree with a few disclaimers.

- 3 - After the install finishes, **test with your web browser** that you can now effectively access your server. This is done by accessing `https://11.22.33.44/` (again, replacing the numbers with your IP address). You will encounter a spooky warning about the certificate not being trusted - which is to be expected for now ! Ask your browser to add an exception about this certificate. After this, you can proceed with the postinstallation.

### Basic configuration

- 4 - The **post-installation** corresponds to the initial configuration of your server. In this step, you will need to choose the main domain name of your server, and a decent administrator password. Regarding the domain name, in the context of this workshop, it is proposed to use free domain names from the `netlib.re` services. You can choose `anything.netlib.re` or `anything.codelib.re` (as long as it's not already used by anybody else). For now, just enter the domain name and we'll configure it "for real" on `netlib.re` after the postinstall is done. Once the postinstall is complete, you should end up on the home screen of the YunoHost web admin interface.

- 5 - Let's now **actually configure the DNS**. Go to `https://netlib.re`. You can create an account or use the login `35c3` with password `iloveyunohost`. Then create the domain name you previously choosed during the postinstall, and click "Detail" to edit this domain's DNS records. Go back to your YunoHost's administration panel and get the recommended DNS configuration in Domains > yourdomain.netlib.re > DNS configuration. For each line given, create the corresponding DNS record on `netlib.re`'s interface. (Yes, that's a bit technical - and boring - but is difficult to automatize for now :s). Once you're done, try to access your server by accessing `https://yourdomain.netlib.re/yunohost/admin` instead of using the IP.

- 6 - (Port forwarding) : this step is not needed here, because we are working on a VPS. But if in the future you want to self-host at home, just know that you will need to configure port forwarding on your internet router ! This is described in the documentation at `https://yunohost.org/port_forwarding`.

- 7 - **Create a first user** using the webadmin interface, in Users > New user. Now if you go to the user interface at `yourdomain.netlib.re/yunohost/sso`, you should be able to login with the user you just created! The user will be able to access apps via this portal. It also has an email address and XMPP account.

- 8 - **Test to install an app!**. For instance, Nextcloud is a popular and officially-supported application. To install it, go in Applications > Install, then look for Nextcloud and click Install. If you want to access apps packaged by the community, you can enable the Community list by clicking 'Manage applications lists'.

- 9 - **Test email features**. Either by configuring a desktop mail client like Thunderbird and configuring a new mail account in it (see `https://yunohost.org/email_configure_client`), or install the Rainloop app (a webmail client) on the server. As a goal : try to send and receive emails to other trainees around you !

- 10 - ??? **Explore YunoHost!** If you want to browse the community apps catalog, you can add the community list in Apps > Install > Manage applications lists > Add (the community list). It's also possible to install a Let's Encrypt certificate so that new visitors won't encounter the spooky certificate warning (though keep in mind that there's a rate limit of 20 certificates per period of 7 days shared between all `netlib.re` domains, so only do this if you really need to !). Documentation is available at `https://yunohost.org/admindoc`.
