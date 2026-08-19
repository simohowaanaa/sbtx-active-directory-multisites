# Infrastructure Active Directory multi-sites – SBTX

Projet de stage portant sur la conception, le déploiement et la sécurisation d'une infrastructure Active Directory multi-sites pour SBTX, avec des sites à Casablanca et à Oujda.

## Contexte

L'entreprise comprend notamment les services suivants :

- Direction technique
- Département achats
- Service matériel et équipements
- Comptabilité fournisseurs
- Moyens généraux
- Systèmes d'information
- Communication

Le projet vise à centraliser la gestion des identités, des postes de travail et des droits d'accès, tout en tenant compte de la séparation géographique des deux sites.

## Objectifs

- Déployer un domaine Active Directory sécurisé.
- Mettre en place deux sites Active Directory : Casablanca et Oujda.
- Assurer la réplication sécurisée entre les contrôleurs de domaine.
- Structurer les utilisateurs et les ressources avec des unités organisationnelles (OU).
- Gérer les autorisations par groupes de sécurité et selon le principe du moindre privilège.
- Appliquer des stratégies de groupe (GPO) de sécurité aux utilisateurs et aux postes.
- Mettre en place la journalisation, la sauvegarde et un scénario de restauration.

## Architecture cible

| Composant | Casablanca | Oujda |
| --- | --- | --- |
| Contrôleur de domaine | Principal | Secondaire |
| Services | AD DS, DNS, GPO | AD DS, DNS, réplication |
| Connectivité | VPN site-à-site / liaison sécurisée | VPN site-à-site / liaison sécurisée |

## Organisation Active Directory envisagée

```text
SBTX
├── Casablanca
│   ├── Utilisateurs
│   └── Postes
├── Oujda
│   ├── Utilisateurs
│   └── Postes
└── Services
    ├── DirectionTechnique
    ├── Achats
    ├── MaterielEtEquipements
    ├── ComptabiliteFournisseurs
    ├── MoyensGeneraux
    ├── SystemesInformation
    └── Communication
```

## Mesures de sécurité prévues

- Politique de mots de passe robuste et verrouillage des comptes.
- Comptes administrateurs dédiés et séparés des comptes utilisateurs.
- Application de GPO : pare-feu, verrouillage de session, restrictions USB et mises à jour.
- Journalisation des connexions et des modifications sensibles.
- Sauvegarde régulière de l'état du système des contrôleurs de domaine.
- Tests de restauration et de continuité de service.

## Environnement de laboratoire

La maquette pourra être réalisée avec Hyper-V, VMware ou VirtualBox :

- Deux machines virtuelles Windows Server : `DC-CASA` et `DC-OUJDA`.
- Une ou plusieurs machines clientes Windows 10/11 Professionnel.
- Un routeur ou pare-feu virtuel pour simuler la liaison sécurisée entre les sites.
- Un domaine de test, par exemple `ad.sbtx.lab`.

## Livrables prévus

- Schéma de l'architecture réseau et Active Directory.
- Plan d'adressage et configuration des sites AD.
- Documentation d'installation et de configuration.
- Politique de gestion des utilisateurs, groupes et droits d'accès.
- Documentation des GPO de sécurité.
- Procédure de sauvegarde, restauration et tests effectués.
