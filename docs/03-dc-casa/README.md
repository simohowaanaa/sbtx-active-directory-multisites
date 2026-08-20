# 03 — DC-CASA : premier contrôleur de domaine

Cette étape installe et configure le premier contrôleur de domaine du laboratoire. Il héberge Active Directory Domain Services et DNS pour la forêt unique `ad.sbtx.lab`.

## Résultat obtenu

| Élément | Valeur |
| --- | --- |
| Serveur | `DC-CASA` |
| Adresse IPv4 | `192.168.10.10/24` |
| Passerelle | `192.168.10.1` |
| DNS préféré | `192.168.10.10` |
| Forêt et domaine | `ad.sbtx.lab` |
| Nom NetBIOS | `SBTX` |
| Rôles installés | AD DS et DNS |

## Réalisation

1. Installation de Windows Server 2025 Standard Evaluation avec expérience utilisateur.
2. Attribution du nom `DC-CASA` et redémarrage du serveur.
3. Configuration de l'adresse IP fixe et du DNS local.
4. Installation du rôle **Services de domaine Active Directory** avec le rôle DNS.
5. Promotion du serveur en premier contrôleur de domaine d'une nouvelle forêt `ad.sbtx.lab`.
6. Configuration du nom NetBIOS `SBTX` et création du catalogue global.
7. Vérification de l'appartenance au domaine et des services NTDS / DNS.
8. Création des instantanés VirtualBox avant et après la configuration.

## Preuves

### Installation et configuration réseau

![Choix de la langue](../assets/03-dc-casa/03-01-choix-langue.png)

![Vérification IP](../assets/03-dc-casa/03-17-verification-ipconfig.png)

### Création du domaine

![Création de la forêt](../assets/03-dc-casa/03-20-creation-foret-ad-sbtx-lab.png)

![Vérification de l'appartenance au domaine](../assets/03-dc-casa/03-21-verification-domaine-sbtx.png)

### Vérification des services

![Service NTDS actif](../assets/03-dc-casa/03-22-service-ntds-actif.png)

![Service DNS actif](../assets/03-dc-casa/03-23-service-dns-actif.png)

## Documentation détaillée

Le déroulement illustré est disponible dans [GUIDE_PAS_A_PAS.md](GUIDE_PAS_A_PAS.md). La synthèse technique est disponible dans [NOTE.md](NOTE.md).
