# Guide pas à pas — DC-CASA

## 1. Installer Windows Server

Choisir le français pour l'installation, le clavier correspondant au poste de travail, puis l'édition **Windows Server 2025 Standard Evaluation (expérience utilisateur)**.

![Langue](../assets/03-dc-casa/03-01-choix-langue.png)

![Clavier](../assets/03-dc-casa/03-02-choix-clavier.png)

Choisir l'installation de Windows Server, puis l'édition avec expérience utilisateur : elle fournit une interface graphique pratique pour l'administration du laboratoire.

![Choix du type d'installation](../assets/03-dc-casa/03-03-choix-installation.png)

![Choix de l'édition](../assets/03-dc-casa/03-04-edition-windows-server.png)

Accepter les conditions de licence, sélectionner le disque virtuel de 60 Go et confirmer le lancement de l'installation.

![Conditions de licence](../assets/03-dc-casa/03-05-licence-windows-server.png)

![Disque d'installation](../assets/03-dc-casa/03-06-disque-installation.png)

![Confirmation de l'installation](../assets/03-dc-casa/03-07-lancement-installation.png)

Créer l'installation sur le disque virtuel de 60 Go et attendre la fin de la copie des fichiers.

![Installation en cours](../assets/03-dc-casa/03-08-installation-en-cours.png)

Lors de la première ouverture de session, définir le mot de passe de l'administrateur local sans le publier ni le réutiliser comme mot de passe DSRM.

![Personnalisation de l'administrateur](../assets/03-dc-casa/03-09-personnalisation-administrateur.png)

![Première ouverture de session](../assets/03-dc-casa/03-10-premiere-ouverture-session.png)

## 2. Préparer le serveur

Après la première connexion, renommer l'ordinateur en `DC-CASA`, puis redémarrer.

![Accès aux propriétés système](../assets/03-dc-casa/03-11-acces-proprietes-systeme.png)

![Paramètres réseau et système](../assets/03-dc-casa/03-12-parametres-reseau.png)

![Adresse IP statique](../assets/03-dc-casa/03-13-adresse-ip-statique.png)

![Renommage](../assets/03-dc-casa/03-14-renommage-dc-casa.png)

![Vérification du nom d'hôte](../assets/03-dc-casa/03-15-verification-nom-hote.png)

Configurer l'interface Ethernet avec les paramètres suivants :

| Paramètre | Valeur |
| --- | --- |
| IPv4 | `192.168.10.10` |
| Masque | `255.255.255.0` |
| Passerelle | `192.168.10.1` |
| DNS préféré | `192.168.10.10` |

![Configuration IPv4](../assets/03-dc-casa/03-16-configuration-ipv4.png)

Vérifier la configuration avec `ipconfig /all`.

![IP statique vérifiée](../assets/03-dc-casa/03-17-verification-ipconfig.png)

Créer un premier instantané VirtualBox : `DC-CASA - Base configuree`.

![Instantané de base](../assets/03-dc-casa/03-18-instantane-base.png)

## 3. Installer AD DS et DNS

Dans le Gestionnaire de serveur, utiliser **Gérer > Ajouter des rôles et fonctionnalités**, choisir l'installation basée sur un rôle, puis cocher **Services de domaine Active Directory** et accepter l'ajout des outils associés.

![Ajout du rôle AD DS](../assets/03-dc-casa/03-19-ajout-role-ad-ds.png)

Promouvoir ensuite le serveur en contrôleur de domaine. Créer une **nouvelle forêt** avec le domaine racine `ad.sbtx.lab`.

![Nouvelle forêt](../assets/03-dc-casa/03-20-creation-foret-ad-sbtx-lab.png)

Conserver l'installation du serveur DNS et du catalogue global, choisir le nom NetBIOS `SBTX`, puis lancer l'installation après la validation des prérequis. Le serveur redémarre automatiquement.

## 4. Vérifier la promotion

Après redémarrage, `whoami` doit retourner `sbtx\administrateur`.

![Domaine SBTX](../assets/03-dc-casa/03-21-verification-domaine-sbtx.png)

Vérifier que les services `NTDS` et `DNS` sont en état `Running`.

![NTDS](../assets/03-dc-casa/03-22-service-ntds-actif.png)

![DNS](../assets/03-dc-casa/03-23-service-dns-actif.png)

Créer enfin l'instantané `DC-CASA - AD DS et DNS`.
