# 00 — Préparation de l'environnement

## Objectif

Préparer une maquette isolée pour concevoir et tester une infrastructure Active Directory multi-sites représentant les sites de Casablanca et d'Oujda.

## Périmètre de la maquette

- Deux contrôleurs de domaine Windows Server.
- Deux postes clients Windows 11 Enterprise.
- Deux réseaux virtuels, un par site.
- Un domaine de laboratoire : `ad.sbtx.lab`.
- Aucun changement sur le réseau, les comptes ou les équipements réels de l'entreprise.

## Poste hôte

| Élément | Configuration |
| --- | --- |
| Système hôte | Windows 11 Home |
| Processeur | Intel Core i9-14900HX |
| Mémoire vive | 32 Go RAM |
| Carte graphique | NVIDIA RTX 5060 |
| Outil de virtualisation | VirtualBox |

Le poste hôte sert uniquement à exécuter et administrer les machines virtuelles. Il ne rejoindra pas le domaine Active Directory.

## Machines virtuelles prévues

| Nom | Rôle | Système | RAM | vCPU | Disque |
| --- | --- | --- | ---: | ---: | ---: |
| `DC-CASA` | Contrôleur de domaine principal | Windows Server Evaluation | 4 Go | 2 | 60 Go |
| `DC-OUJDA` | Contrôleur de domaine secondaire | Windows Server Evaluation | 4 Go | 2 | 60 Go |
| `PC-CASA-01` | Poste client Casablanca | Windows 11 Enterprise Evaluation | 4 Go | 2 | 50 Go |
| `PC-OUJDA-01` | Poste client Oujda | Windows 11 Enterprise Evaluation | 4 Go | 2 | 50 Go |

Lorsque les quatre VM sont actives, elles utilisent 16 Go de RAM. Les disques seront créés au format dynamique afin de ne pas réserver tout l'espace immédiatement.

## Ressources logicielles

| Ressource | Utilisation | État |
| --- | --- | --- |
| VirtualBox | Hébergement des VM et réseaux virtuels | Disponible |
| ISO Windows Server Evaluation (FR) | Installation des deux contrôleurs de domaine | À confirmer après téléchargement |
| ISO Windows 11 Enterprise Evaluation (FR) | Installation des deux postes clients | À confirmer après téléchargement |

## Réseaux de laboratoire envisagés

| Site | Réseau | Machines associées |
| --- | --- | --- |
| Casablanca | `192.168.10.0/24` | `DC-CASA`, `PC-CASA-01` |
| Oujda | `192.168.20.0/24` | `DC-OUJDA`, `PC-OUJDA-01` |

Les paramètres détaillés des cartes réseau virtuelles seront documentés dans l'[étape 02](../02-virtualisation/README.md).

## Checklist avant de continuer

- [ ] Vérifier que les deux ISO sont téléchargées.
- [ ] Vérifier qu'au moins 150 Go d'espace disque sont disponibles sur le poste hôte.
- [ ] Créer un dossier local dédié aux machines virtuelles.
- [ ] Vérifier que la virtualisation matérielle est activée dans le BIOS/UEFI.
- [ ] Ouvrir VirtualBox et confirmer qu'il démarre sans erreur.

## Prochaine étape

Après validation de cette checklist, créer les réseaux virtuels et la machine `DC-CASA` dans l'[étape 02 — Virtualisation](../02-virtualisation/README.md).
