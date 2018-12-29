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

Tip: When a command displays nothing and gives you the prompt back (i.e. you can type something after the # symbol) it usually means that your command worked.

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
    - Note that those informations are not accessible by anyone else since they are on **YOUR SERVER** ! You are reclaiming responsibility on them. Amazing, right ?

1. The email address you enter here is **YOUR NEW email address** created using the email software of your yunohost server. So you can choose any email address ending with your domain name (for instance `me@yourdomain.nohost.me`)
    - You can choose a maximal size for the mail box or leave it empty, no to set any limit.

1. At this end, choose a password (or passphrase) for the new user. It's different to the administrator password and it will be used to access the **User Interface** with this new user account.

You should now have one user in the list. Go back to the home section (tiny home icon).

### Install a first web application !

We have to choose an app among the yunohost apps (around a hundred). **Nextcloud** is a popular and officially-supported application.

1. To install it, navigate the `Applications` section and click `Install`.

1. Look for Nextcloud, typing `next` in the search field. and click `+ Install`.

1. Form now, in the following form, you can let each value to it's default. So just click the `install` button (we will go though this parameters later).

1. You should now have the Nextcloud app in the app list.

Tip: By default only official apps are available. If you want to access apps packaged by the community, you can enable the Community list by clicking `Manage applications lists`.

### Access Nextcloud through the user interface

1. Click the blue `user interface` button in the upper right corner (or type in your browser yourdomain.nohost.me/yunohost/sso).

1. Login with the user nickname and password of the preceding section.

1. Your now accessing the user interface of yunohost. All apps installed andaccessible to your user account are shown here as colored squared icons.

1. Click the Nextcloud icon. It will redirect you to the application path configured during the installation. In our case `yourdomain.nohost.me/nextcloud`.

1. You can now explore the Nextcloud interface. 
    - It's a cloud application, somehow similar to GoogleDrive for instance, but respecting your privacy since it's under your control.
    - Try to upload a file (choose a small one first) using the `+` button.

### Install a SSL certificate (get rid of the spooky warning)

1. Return to the administration interface:
    - Click the bottom left `Yunohost` button to get back to the user interface.
    - Then click the `Administration` link in the footer of the page.

1. Navigate to the `Domains` section, click your created domain (something.nohost.me).

1. In the `Operations` section, click the `SSL Certificate` button.

1. Launch the certifiate installation with the `Install a Let's Encrypt certificate` button then confirm with `Ok`.

1. When the installation is finished, reload the page. You browser should now display a closed lock at the left. The SSL connections of your server will now be accepted by any browser or client, ensuring the some level of security for the connexions.

### Send some email


1. Send an email to your new user email address (for instance me@yourdomain.nohost.me) using your current email service.

1. To read this message we will need an email client. Go to the administration panel and install the webmail application named `Rainloop` (Follow the same procedure with which you installed Nextcloud before).
    - Let the default parameter values except for the password.
    - Choose a different password of the user and admin password.

1. Access this webmail by clicking the newly added Rainloop item in the app list and then follow the URL : https://yourdomain.nohost.me/rainloop/

1. You should see your email incomming in your Inbox.

1. Then send a new email to your usual email address using rainloop.
    - Click `New`, write some test message and click send.

1. You can then fetch and see this email with your usual email client.



### Explore YunoHost!

- Add another user and Install some other apps.

- Deny access to the apps for the second user : Apps > Click an app > Click the Access button and allow only the first user. The app won't display in the interface of other users.

- If you want to browse the community apps catalog, you can add the community list in Apps > Install > Manage applications lists > Add (the community list).

- You can buy a domain name you fully control and add it to your server

- Etc.


## Resources
- Documentation is available at `https://yunohost.org/admindoc`.
- To find answers, the forum is accessible at https://forum.yunohost.org
- Some following tutorials comming.