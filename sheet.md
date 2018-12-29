# Hands-on Introduction to Self-Hosting with YunoHost


## Setting up your first YunoHost server

### Use SSH to access the server

#### Linux and MacOS Users

1. Find and open the terminal software

2. **SSH in your server**. Using the IP address provided to you, run the following command in your terminal : 
```
ssh root@11.22.33.44
```
(replacing the number with your IP address).

#### Windows Users

1. Download *MobaXterm* somewhere on the internet and install it.

2. Create a new session (type: SSH) with
    - `Hostname`: `11.22.33.44` (replace with your provided IP address)
    - Set `Username` to **root**

### Log in with SSH

1. The program will ask you to check the server indentifier (fingerprint) to confirm its identity: just type `yes` then press `Enter key`. (usually people don't check it though it's a bad security practice :/).

2. Then enter the ssh password of your server, in our case `iloveyunohost`. While you type the password, nothing appears on the screen: it's normal! Once you've typed the password, just press `Enter`.

3. Then you should see some ascii art popping up, as well as technical info, and a new **command prompt** like:

```root@some_name:~# ```

 You can type commands in this prompt to control your server through command line !


### Install YunoHost 

**Let's run YunoHost's installation script**. For various reasons (please trust the teacher ;)), we will setup a instance of the testing version !
    
1. To download and prepare the installation script, copy or type the two following commands carefully :

```
# wget https://install.yunohost.org -O install_script
# chmod +x install_script
```

Tip: When a command displays nothing and gives you the prompt back (i.e. you can type something after the # symbol) it usually means that your command worked.

2. Now type this command and execute it: `# ./install_script -d testing`
    - It effectivelly launches the installation.
    - You might have to **agree** with a few disclaimers (select `Yes` or `Choose the maintainer's version` and press enter).

3. After the install finishes, test with your web browser that you can now effectively access your server.
    - Access the server in your web browser with the url : `https://11.22.33.44/` (again, replacing the numbers with your IP address).
    - You will encounter a spooky warning about the certificate not being trustable - which is to be expected for now !
    - Ask your browser to add an exception about this certificate.
    - You should see a page with a success message \o/ !
    
### Initial configuration (a.k.a. post-installation)

The **post-installation** corresponds to the initial configuration of your server. In this step, you will need to choose the **main domain name** (the address that will designate your server) and a decent **administrator password**. Regarding the domain name, in the context of this workshop, we will use an automatically configured domain name provided by the YunoHost team.

1. Access your server in the web browser and click the `Let's Go` button.

1. Choose `I don't have a domain name`.

1. Choose a domain name ending with `nohost.me` (for instance : `iloveynh.nohost.me`).
    - Choose whatever you want and it will tell you if this domain is available.
    - Note that the domain will then be unavailable for registration. If you want to reinstall a new server later using the same domain name, you should first ask the YunoHost team to make the domain available again for registration.

1. Choose an **administration password** for your server. A passphrase is often a good choice as it's strong, memorable and easy to type. For example: `allcomputersaredeeplybroken`.

Yunohost is now ready to be used !

### Access the administration interface

In the web browser you can now access your server using the domain name previously configured.

1. To access the web administration interface type `yourdomain.nohost.me` in the browser.
    - it will redirect you to the address `https://yourdomain.nohost.me/yunohost/admin`
    - Like before, you'll get a warning and you'll have to add an exception (the certificate is not already setup.We will configure that in some moment).

1. You now face a simple authentication form. Connect using your administration passphrase that you defined previously.

You can now control your server using this clean interface.

### Create a first user

1. Navigate to `Users` section and click `New user` button.

1. Fill in the form with (real or fake) information. Note that by doing this, you are not "creating yet another account on a commercial website" : you are creating an identity on *your very own server* which you control!

1. The email address you enter here will become *your very own new email address*, relying on the email softwares running on your YunoHost server. You can choose any email address ending with your domain name (for instance `me@yourdomain.nohost.me`)
    - You can choose a quota for the mailbox, or leave it empty to set no limitation.

1. At this end, choose a password (or passphrase) for the new user. It should be different from the admin password, and it will be used to access the **User Interface** with this new user account.

You should now have one user in the user list. Go back to the home section (tiny home icon).

### Install a first web application !

We have to choose an app among the YunoHost apps (around a hundred if you add the community list later). **Nextcloud** is a popular and officially-supported application.

1. To install it, navigate the `Applications` section and click `Install`.

1. Look for Nextcloud, typing `next` in the search field. and click `Install`.

1. For now, in the following form, you can probably keep the default values. So just click the `install` button at the bottom.

1. Details about the ongoing installation will be displayed at the top. Once the installation is complete, you should have the Nextcloud app in the app list.

Tip: By default only official apps are available in the application catalog. If you want to access apps packaged by the community, you can enable the Community list by clicking `Manage applications lists`.

### Access Nextcloud through the user interface

1. Click the blue "`User interface`" button in the upper right corner (or type in your browser `yourdomain.nohost.me/yunohost/sso`).

1. Login with the username and password defined in the previous sections.

1. Your are now accessing the user interface of YunoHost. All apps installed and accessible to your user account are shown here as colored tiles.

1. Click the Nextcloud icon. It will redirect you to the application path configured during the installation. In our case `yourdomain.nohost.me/nextcloud`.

1. You can now explore the Nextcloud interface. 
    - It's a cloud application, somehow similar to GoogleDrive for instance, but respecting your privacy since it's under your control.
    - Try to upload a file (choose a small one first) using the `+` button.

### Install a SSL certificate (get rid of the spooky warning)

1. Return to the administration interface:
    - Click the bottom left `Yunohost` button to get back to the user portal.
    - Then click the `Administration` link in the footer.

1. Navigate to the `Domains` section, click your domain (`something.nohost.me`).

1. In the `Operations` section, click the `SSL Certificate` button.

1. Launch the certifiate installation with the `Install a Let's Encrypt certificate` button then confirm with `Ok`.

1. When the installation is finished, reload the page. You browser should now display a green lock at the left of the address bar. New visitors arriving on your server won't encounter the spooky warning anymore!

### Emails!

1. Send an email to your new user email address (for instance `me@yourdomain.nohost.me`) using your current email service.

1. To read this message we will need an email client configured to access your user's mailbox. For instance, we can use the webmail client Rainloop. Go to the administration panel and install `Rainloop`. (Follow the same procedure with which you installed Nextcloud before).
    - Keep the default parameter values (except for the password).
    - Choose a different password from the user and admin passwords choosed previously.

1. Access this webmail by clicking the newly added Rainloop item in the app list and then follow the URL : `https://yourdomain.nohost.me/rainloop/`

1. You should find the email you send previously in the Inbox.

1. Then send a new email *from* your YunoHost server *to* your usual email address, still using Rainloop.
    - Click `New`, write a test message and click `Send`.

1. You can then fetch your usual email address, and should see your message popping up.


### Explore YunoHost!

- Add another user and install some other apps.

- Deny access to the apps for the second user : Apps > Click an app > Click the Access button and allow only the first user. The app won't display in the interface of other users.

- If you want to browse the community apps catalog, you can add the community list in Apps > Install > Manage applications lists > Add (the community list).

- You can buy a domain name you fully control and add it to your server.

- Etc.

## Resources

- Documentation is available at `https://yunohost.org/admindoc`.
- If you encounter issues or have questions, the forum is accessible at `https://forum.yunohost.org`
