# Initiation pratique à l'auto-hébergement avec YunoHost

## Installer votre premier serveur YunoHost

L`ors de cet atelier, nous utilisons serveur fourni gracieusement par Alsace Réseau Neutre (FAI associatif à Strasbourg, arn-fai.net) pour le temps des JDLL ! Dans la vraie vie, il faudrait commencer par commander un serveur chez eux - ou bien acheter un Raspberry Pi ou un serveur virtuel (VPS) en ligne chez des hébergeurs comme Scaleway, OVH, ...

### Utiliser SSH pour accéder au serveur

#### Sur Linux et MacOS

1. Trouver et ouvrir le terminal (généralement dans les programmes "Accessoires")

2. **Se connecter en SSH sur le serveur**. Taper la commande suivante dans le terminal, en utilisant l'adresse IP qui vous a été fournie :
```
ssh root@11.22.33.44
```
(remplacer les nombres par votre adresse IP).

#### Sur Windows

1. Télécharger *MobaXterm* quelquepart sur Internet et l'installer.

2. Créer une nouvelle session (de type SSH) avec :
    - `Hôte`: `11.22.33.44` (remplacer par votre adresse IP)
    - `Utilisateur` : **root** (attention, si vous souhaitez faire du SSH après la postinstallation il faudra se connecter en tant qu'**admin**)

### Se logger en SSH

1. Après avoir tapé la commande, le programme vous demandera de vérifier l'identité (empreinte cryptographique) pour confirmer son identité : tapez juste `yes` puis pressez `Entrée` (généralement on ne la vérifie pas car c'est compliqué, malgré le fait que ce n'est pas une pratique de sécurité idéale :/).

2. Puis entrer le mot de passe de votre serveur. Dans notre cas, c'est `iloveyunohost`. Pendant que vous tapez le mot de passe, rien n'apparaît sur l'écran : c'est normal (cela empêche quelqu'un de voir derrière votre épaule le nombre de caractère par exemple). Une fois le mot de passe tapé, appuyez simplement sur `Entrée`.

3. Ensuite, vous deviez voir quelques informations s'afficher puis une nouvelle **invite de commande** comme ceci :

```
root@un_nom:~#
```

À partir de là, vous pouvez taper des commandes dans le terminal pour controler le serveur à distance par ce biais !


### Installer YunoHost 

**Lançons le script d'installation de YunoHost**. 
    
1. Pour télécharger et lancer le script, taper cette commande :

```
curl https://install.yunohost.org | bash
```

2. ... et appuyer sur Entrée !
    - Cela lance l'installation
    - Il vous faut **accepter** quelques avertissements (choisissez `Oui` sur chacun d'entre eux et appuyez sur Entrée)

3. Une fois l'installation terminée, testez avec votre navigateur web que vous pouvez accéder à votre serveur.
    - Accéder au serveur depuis votre navigateur avec cette URL : `https://11.22.33.44/` (encore une fois, remplacer les nombres par votre adresse IP).
    - Un avertissement s'affiche car, pour le moment, votre navigateur ne peut pas faire confiance au certificat du serveur - c'est normal !
    - Demander au navigateur d'ajouter une exception pour le certificat.
    - Vous devriez maintenant voir une page avec un message de félicitations \o/ !

### Configuration initiale (a.k.a. la post-installation)

La **post-installation** corresponds à la configuration initiale de votre serveur. Pendant cette étape, il vous faut choisir le **nom de domaine principal** (l'adresse à taper pour désigner votre serveur) ainsi qu'un **mot de passe administrateur** d'une complexité raisonnable. Pour ce qui est du nom de domaine, dans le cadre de cet atelier, nous utiliserons un domaine fourni par le projet YunoHost, qui sera automatiquement configuré.

1. À partir de la page dans votre navigateur, cliquer sur le bouton `C'est parti`.

1. Choisir `Je n'ai pas de nom de domaine`.

1. Choisir un nom qui se termine en `nohost.me` (par exemple : `jadoreynh.nohost.me`).
    - Choisissez ce que vous voulez et le système vous dira si le domaine est disponible ou non.
    - Une fois enregistré, le domaine ne pourra plus être réservé pendant une autre installation. Si plus tard vous souhaitez réutiliser ce même domaine, il vous faudra demander à l'équipe YunoHost sur le forum pour réinitialiser le domaine.

1. Choisissez un **mot de passe administrateur** pour votre serveur. Il s'agit de la première ligne de défense de votre serveur !  Une *phrase de passe* est préférable car fourni une bonne sécurité tout en étant mémorisable et facile à taper. Par exemple : `touslesordinateurssontcassés`.

Yunohost est maintenant prêt !

### Accéder à l'inteface d'administration

Dans votre navigateur, il est maintenant possible d'accéder à votre serveur à l'aide du nom de domaine choisi.

1. Pour accéder à l'interface d'administration, tapez `votredomaine.nohost.me` dans votre navigateur.
    - Vous serez redirigez vers `https://votredomaine.nohost.me/yunohost/admin`
    - Comme avant, vous rencontrerez un avertissement de sécurité et il vous faut rajouter une exception (le certificat n'est pas encore configuré proprement. Nous pourrons le configurer plus tard).

1. Vous êtes maintenant face à l'interface d'authentification. Vous pouvez vous connecter en tapant que le mot de passe administrateur choisi précédemment.

Vous arrivez finalement devant l'interface de contrôle de YunoHost.

### Créer un premier utilisateur

1. Rentrer dans la section `Utilisateurs` et cliquez sur `Nouvel utilisateur`. L'identité que nous allons créer sera ensuite utilisée pour accéder à l'**interface utilisateur**.

1. Remplir le formulaire avec des informations (vraies ou fausses). Notez qu'en faisant cela, vous n'êtes pas en train de créer "encore un compte sur un site commercial qui va avoir mes infos" : il s'agit de créer une identité *sur votre propre serveur*, que vous contrôlez !

1. L'adresse email que vous définissez deviendra *votre propre adresse email*, fonctionnant grâce aux programmes qui tournent dans votre serveur. Vous pouvez choisir n'importe quelle adresse qui se termine par votre nom de domaine (par exemple `moi@votredomaine.nohost.me`)
    - Vous pouvez définir un quota pour la boîte mail, ou laisse le champ vide pour ne pas avoir de limite.

1. À la fin, choisissez un mot de passe (ou phrase de passe) pour le nouvel utilisateur. Idéalement il doit être différent du mot de passe utilisateur.

Une fois validé, vous devriez voir un utilisateur dans la liste des utilisateurs. Revenez à l'accueil (petite icone de maison).

### Installez une première application web !

Nous devons choisir une application parmi les applications YunoHost (il en existe une centaine si vous ajoutez la liste d'apps de la communauté plus tard). **Nextcloud** est une application populaire et officiellement supportée.

1. Pour l'installer, entrez dans la section `Applications` et cliquez sur `Installer`.

1. Cherchez Nextcloud : par exemple tapez "next" dans le champ de recherche, puis cliquez sur "Installer" sur l'application Nextcloud.

1. Dans le formulaire d'installation, vous pouvez probablement conserver toutes les valeurs par défaut. Il suffit donc de cliquer sur le bouton "Installer" en bas de l'écran.

1. Les détails sur l'installation en cours s'affichent en haut de l'écran. Une fois l'installation terminée, vous devriez voir l'application Nextcloud dans la liste des applications installées.

Astuce : Par défaut, seules les applications officielles sont disponibles dans le catalogue d'applications. Si vous voulez accéder aux applications packagées par la communauté, vous pouvez activer la liste Communauté en cliquant sur 'Gérer les listes d'applications'.

### Accès à Nextcloud via l'interface utilisateur

1. Cliquez sur le bouton bleu "Interface utilisateur" dans le coin supérieur droit (ou tapez dans votre navigateur `votredomaine.nohost.me/yunohost/sso`).

1. Connectez-vous avec le nom d'utilisateur et le mot de passe définis dans les sections précédentes.

1. Vous accédez maintenant à l'interface utilisateur de YunoHost. Toutes les applications installées et accessibles à votre compte utilisateur sont affichées ici sous forme de tuiles colorées.

1. Cliquez sur l'icône Nextcloud. Il vous redirigera vers le chemin de l'application configurée lors de l'installation. Dans notre cas `votredomaine.nohost.me/nextcloud`.

1. Vous pouvez maintenant explorer l'interface Nextcloud. 
    - C'est une application de cloud de fichiers, similaire à GoogleDrive par exemple, mais respectant votre vie privée puisqu'elle est sous votre contrôle.
    - Essayez de télécharger un fichier (choisissez d'abord un petit fichier) en utilisant le bouton "+".

### Installer un certificat SSL (se débarrasser de l'avertissement de sécurité)

1. Revenez à l'interface d'administration :
    - Cliquez sur le bouton `Yunohost` en bas à gauche pour revenir au portail utilisateur.
    - Cliquez ensuite sur le lien `Administration` dans le pied de page.

1. Rentrer dans la section `Domaines`, cliquez sur votre domaine (`votredomaine.nohost.me`).

1. Dans la section `Opérations`, cliquez sur le bouton `Certificat SSL`.

1. Lancez l'installation du certificat avec le bouton "Installer un certificat de chiffrement" puis confirmez avec "OK".

1. Lorsque l'installation est terminée, rechargez la page. Votre navigateur devrait maintenant afficher un cadenas vert à gauche de la barre d'adresse. Les nouveaux visiteurs arrivant sur votre serveur n'auront plus d'avertissement de sécurité !

### Des emails !

1. Envoyez un courriel à votre nouvelle adresse courriel (par exemple `moi@votredomaine.nohost.me`) en utilisant votre service de courriel actuel.

1. Pour lire ce message, il vous faudra un client de messagerie configuré pour accéder à la boîte aux lettres de votre utilisateur. Par exemple, nous pouvons utiliser le client webmail Rainloop. Allez dans le panneau d'administration et installez l'application `Rainloop`. (Suivez la même procédure que celle avec laquelle vous avez installé Nextcloud auparavant).
    - Conserver les valeurs par défaut des paramètres (sauf le mot de passe).
    - Choisissez un mot de passe différent de celui de l'utilisateur et des mots de passe administrateur choisis précédemment.

1. Accédez à ce webmail en cliquant sur l'élément Rainloop nouvellement ajouté dans la liste des applications, puis suivez l'URL : `https://votredomaine.nohost.me/rainloop/`

1. Vous devriez trouver le courriel que vous avez envoyé précédemment dans votre boîte de réception.

1. Envoyez ensuite un nouvel email *depuis* votre serveur YunoHost *à* votre adresse email habituelle, en utilisant toujours Rainloop.
    - Cliquez sur "Nouveau", écrivez un message de test et cliquez sur "Envoyer".

1. Vous pouvez alors aller sur votre adresse e-mail habituelle, et votre message devrait apparaître.


### Explorez YunoHost !

- Ajouter un autre utilisateur et installer d'autres applications.

- Gérer les permissions des applications : Applications > Cliquez sur une application > Cliquez sur le bouton Accès et n'autorisez que le premier utilisateur. L'application ne s'affichera pas dans l'interface des autres utilisateurs.

- Si vous voulez parcourir le catalogue des applications de la communauté, vous pouvez ajouter la liste Communauté dans Apps > Installer > Gérer les listes d'applications > Ajouter (la liste Communauté).

- Etc.

## Ressources, aller plus loin

- La documentation est disponible sur `https://yunohost.org/admindoc`.
- Si vous rencontrez des problèmes ou avez des questions, le forum est accessible sur `https://forum.yunohost.org`
- Vous pouvez acheter un nom de domaine (que vous contrôlerez alors entièrement) et l'ajouter à votre serveur. Attention : il vous faudra suivre la page de documentation `https://yunohost.org/dns_config` pour configurer le nom de domaine correctement.
- Vous pouvez acheter un Raspberry Pi (ou autre carte ARM) ou un VPS en ligne. Par exemple, Alsace Réseau Neutre propose des VPS hébergés sur de l'internet Bio !
- Si vous vous hébergez à la maison (sur une carte ARM), faites attention aux limitations imposées par votre FAI (c.f. `https://yunohost.org/isp`). Soyez conscient également qu'il vous faudra configurer les redirections de ports sur votre box comme décrit sur `https://yunohost.org/isp_box_config`.

