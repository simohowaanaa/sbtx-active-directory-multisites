# Guide visuel — Étape 02 : Virtualisation

Ce guide reprend, dans l'ordre, toutes les actions réalisées pour préparer la maquette Active Directory multi-sites dans VirtualBox.

## 1. Préparer VirtualBox

Le dossier par défaut des nouvelles machines virtuelles a été défini afin de centraliser la maquette dans un emplacement dédié.

![Dossier par défaut des VM](../assets/02-virtualisation/02-01-dossier-vm-virtualbox.png)

## 2. Créer le contrôleur de domaine Casablanca

La VM `DC-CASA` utilise l'ISO Windows Server. L'installation automatique est désactivée afin de contrôler les choix pendant l'installation.

![Création de DC-CASA](../assets/02-virtualisation/02-02-creation-dc-casa.png)

Les ressources attribuées sont de 4 Go de RAM et 2 vCPU.

![Ressources de DC-CASA](../assets/02-virtualisation/02-03-ressources-dc-casa.png)

Un disque VDI dynamique de 60 Go a été créé.

![Disque de DC-CASA](../assets/02-virtualisation/02-04-disque-dc-casa.png)

La machine apparaît ensuite dans VirtualBox sans être démarrée.

![DC-CASA créée](../assets/02-virtualisation/02-05-vm-dc-casa-creee.png)

Sa carte réseau est reliée au réseau interne du site Casablanca : `SBTX-CASA`.

![Réseau de DC-CASA](../assets/02-virtualisation/02-06-reseau-dc-casa.png)

## 3. Créer le poste client Casablanca

La VM `PC-CASA-01` utilise l'ISO Windows 11 Enterprise.

![Création de PC-CASA-01](../assets/02-virtualisation/02-07-creation-pc-casa.png)

Elle reçoit 4 Go de RAM, 2 vCPU et le démarrage UEFI.

![Ressources de PC-CASA-01](../assets/02-virtualisation/02-08-ressources-pc-casa.png)

Le disque VDI dynamique est dimensionné à 50 Go.

![Disque de PC-CASA-01](../assets/02-virtualisation/02-09-disque-pc-casa.png)

La VM a été créée avec succès.

![PC-CASA-01 créée](../assets/02-virtualisation/02-10-vm-pc-casa-creee.png)

Les paramètres système ont été ouverts pour activer les prérequis Windows 11.

![Paramètres de PC-CASA-01](../assets/02-virtualisation/02-11-parametres-pc-casa.png)

Le TPM a été localisé dans les paramètres de la carte mère.

![Configuration du TPM](../assets/02-virtualisation/02-12-tpm-pc-casa-configuration.png)

TPM 2.0, UEFI et Secure Boot sont activés.

![TPM 2.0 activé](../assets/02-virtualisation/02-13-tpm-pc-casa-active.png)

Enfin, le poste client est raccordé à `SBTX-CASA`.

![Réseau de PC-CASA-01](../assets/02-virtualisation/02-14-reseau-pc-casa.png)

## 4. Créer le contrôleur de domaine Oujda

La VM `DC-OUJDA` utilise la même ISO Windows Server que le premier contrôleur.

![Création de DC-OUJDA](../assets/02-virtualisation/02-15-creation-dc-oujda.png)

Les ressources prévues sont 4 Go de RAM et 2 vCPU.

![Ressources de DC-OUJDA](../assets/02-virtualisation/02-16-ressources-dc-oujda.png)

Le disque VDI dynamique est fixé à 60 Go.

![Disque de DC-OUJDA](../assets/02-virtualisation/02-17-disque-dc-oujda.png)

La VM est créée, sans démarrage.

![DC-OUJDA créée](../assets/02-virtualisation/02-18-vm-dc-oujda-creee.png)

Une première sélection du réseau Casablanca a été corrigée : `DC-OUJDA` doit appartenir au site Oujda.

![Correction du réseau](../assets/02-virtualisation/02-19-reseau-dc-oujda-correction.png)

La configuration finale utilise donc le réseau interne `SBTX-OUJDA`.

![Réseau de DC-OUJDA](../assets/02-virtualisation/02-20-reseau-dc-oujda.png)

## 5. Créer le poste client Oujda

La VM `PC-OUJDA-01` utilise Windows 11 Enterprise.

![Création de PC-OUJDA-01](../assets/02-virtualisation/02-21-creation-pc-oujda.png)

Elle reçoit 4 Go de RAM, 2 vCPU et UEFI.

![Ressources de PC-OUJDA-01](../assets/02-virtualisation/02-22-ressources-pc-oujda.png)

Son disque VDI dynamique est de 50 Go.

![Disque de PC-OUJDA-01](../assets/02-virtualisation/02-23-disque-pc-oujda.png)

La machine est créée dans VirtualBox.

![PC-OUJDA-01 créée](../assets/02-virtualisation/02-24-vm-pc-oujda-creee.png)

## 6. Créer le routeur inter-sites

Le routeur `RTR-SBTX` repose sur OPNsense, basé sur FreeBSD 64 bits.

![Création de RTR-SBTX](../assets/02-virtualisation/02-26-creation-routeur-rtr-sbtx.png)

Il utilise 1 Go de RAM et 1 vCPU.

![Ressources de RTR-SBTX](../assets/02-virtualisation/02-27-ressources-routeur-rtr-sbtx.png)

Son disque VDI dynamique est de 10 Go.

![Disque de RTR-SBTX](../assets/02-virtualisation/02-28-disque-routeur-rtr-sbtx.png)

La VM du routeur est ensuite créée.

![RTR-SBTX créée](../assets/02-virtualisation/02-29-vm-routeur-rtr-sbtx-creee.png)

L'Adaptateur 1 est réservé au WAN, en NAT, pour l'accès Internet temporaire.

![WAN NAT du routeur](../assets/02-virtualisation/02-30-reseau-routeur-wan-nat.png)

L'Adaptateur 2 est relié au réseau Casablanca.

![Interface Casablanca du routeur](../assets/02-virtualisation/02-31-reseau-routeur-casablanca.png)

L'Adaptateur 3 est relié au réseau Oujda.

![Interface Oujda du routeur](../assets/02-virtualisation/02-32-reseau-routeur-oujda.png)

## 7. Résultat final

Les cinq VM sont créées et restent éteintes. Les systèmes d'exploitation et les services réseau seront configurés dans les étapes suivantes.

![Topologie VirtualBox finale](../assets/02-virtualisation/02-33-topologie-virtualbox.png)
