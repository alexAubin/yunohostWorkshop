# Hands-on Introduction to Self-Hosting with YunoHost


## Setting up your first YunoHost server

### Use SSH to access the server

#### Linux and MacOS Users

1. Find and open the terminal software

1. **SSH in your server**. Using the IP address provided to you, run the following command in your terminal : 
```
ssh root@11.22.33.44
```
(replacing the number with your IP address).

#### Windows Users

1. Download *MobaXterm* somewhere on the internet and install it.

1. Create a new session (type: SSH) with
    - `Hostname`: `11.22.33.44` (replace with your provided IP address)
    - Set `Username` to **root**

### Log in with SSH

1. The program will ask you to check the server indentifier (fingerprint) to confirm its identity: just type `yes` then press `Enter key`. (usually people don't check it though it's a bad security practice :/).

1. Then enter the ssh password of your server, in our case `iloveyunohost`. When you type nothing appears on the screen. It's normal. Once you've typed it press `Enter` anyway.
 
1. Then you should see some ascii art popping up, as well as technical info, and a new **command prompt** like:

```root@some_name:~# ```

 You can type commands in this prompt to control your server through command line !


### Install yunohost 

**Let's run YunoHost's installation script**. For various reasons (please trust the teacher ;)), we will setup a instance of the testing version !
    
1. To download and prepare the installation script, copy or type the two following commands carefully :

```
# wget https://install.yunohost.org -O install_script
# chmod +x install_script
```
    - Tip: when a command display nothing and gives you the prompt back (i.e. you can type something after the # symbol) it usually means that your command worked.

1. Now type this command and execute it: 
    - ```
      # ./install_script -d testing
      ```
    - It effectivelly launches the post-installation.
    - You might have to **agree** with a few disclaimers (select yes) and select configuration version (choose the maintainer's version and press enter).

1. After the install finishes, test with your web browser that you can now effectively access your server.
    - Access the server in your web browser `https://11.22.33.44/` (again, replacing the numbers with your IP address).
    - You will encounter a spooky warning about the certificate not being trustable - which is to be expected for now !
    - Ask your browser to add an exception about this certificate.
    - You should see a page with a success message \o/ !
    
### Basic configuration (post-installation)

The **post-installation** corresponds to the initial configuration of your server. In this step, you will need to choose the **main domain name** (the address you type designate your server) and a decent **administrator password**. Regarding the domain name, in the context of this workshop, we will use an automatically configured domain name provided by the yunohost team.

1. Access your server in the web browser and clic `Let's Go` button.

1. Choose the `I don't have a domain name` section.

1. You will now choose a domain name finishing with `nohost.me` (for instance : `iloveynh.nohost.me`).
    - Choose whatever you want and it will tell you if it's available.
    - Note that it will block this name and this is a workshop testing server. So you should choose a domain name you don't wan't to use later for a real server.
    - You can still unblock later the name by asking on the yunohost forum.

1. Choose the **administration password** of your server. A passphrase is often a good choice as it's strong, memorable and easy to type. For example: `allcomputersaredeeplybroken`.

Yunohost is now ready to be used !

### Access the administration interface

In the web browser you can now access your server using the domain name previously configured.

1. To access the web administration interface type `yourdomain.nohost.me` in the browser.
    - it will redirect you to the address `https://yourdomain.nohost.me/yunohost/admin`
    - Like before, you'll get a warning and you'll have to add an exception (the certificate is not already setup.We will configure that in some moment).

1. You now face a simple authentication form. Connect using your administration passphrase.

You can now control your server using this clean interface.

### Create a First user

1. Navigate to `Users` section and click `New user` button.

1. Fill the form with (real or fake) informations
    - Note that you can trust this service since it's **YOUR SERVER** ! No one's else is getting access to thoses informations. Amazing, right ?

1. The email address you enter here is **YOUR NEW email address** created using the email software of your yunohost server. So you can choose any email address ending with your domain name (for instance `me@yourdomain.nohost.me`)
    - You can choose a maximal size for the mail box or leave it empty, no to set any limit.

1. At this end, choose a password (or passphrase) for the new user. It will be used to access the **User Interface** with your new user account.

You should now have one user in the list. Go back to the home section (tiny home icone).


## Test to install an app!

We have to choose an app among the yunohost apps (around a hundred). **Nextcloud** is a popular and officially-supported application.

1. To install it, navigate the `Applications` section and click `Install`.

1. Look for Nextcloud, typing `next` in the search field. and click `Install`.

1. Form now, in the following form, you can let each value to it's default. So just click the `install` button (we will go though this parameters later).

Tip: By default only official apps are available. If you want to access apps packaged by the community, you can enable the Community list by clicking `Manage applications lists`.

### Access Nextcloud through the user interface

1. 

- 9 - **Test email features**. Either by configuring a desktop mail client like Thunderbird and configuring a new mail account in it (see `https://yunohost.org/email_configure_client`), or install the Rainloop app (a webmail client) on the server. As a goal : try to send and receive emails to other trainees around you !

- 10 - ??? **Explore YunoHost!** If you want to browse the community apps catalog, you can add the community list in Apps > Install > Manage applications lists > Add (the community list). It's also possible to install a Let's Encrypt certificate so that new visitors won't encounter the spooky certificate warning (though keep in mind that there's a rate limit of 20 certificates per period of 7 days shared between all `netlib.re` domains, so only do this if you really need to !). Documentation is available at `https://yunohost.org/admindoc`.

