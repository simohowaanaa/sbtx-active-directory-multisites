# 02 — Virtualisation

## Objectif

Construire l'environnement virtuel isolé qui hébergera l'infrastructure Active Directory multi-sites.

## Configuration VirtualBox

Le dossier par défaut des nouvelles machines virtuelles est configuré comme suit :

```text
C:\VirtualMachines\SBTX-AD-Lab
```

![Dossier des VM](../assets/02-virtualisation/02-01-dossier-vm-virtualbox.png)

## Machines virtuelles créées

| Machine | Système | RAM | vCPU | Disque | État |
| --- | --- | ---: | ---: | ---: | --- |
| `DC-CASA` | Windows Server 2025 Evaluation | 4 Go | 2 | 60 Go VDI dynamique | Créée |
| `PC-CASA-01` | Windows 11 Enterprise Evaluation | 4 Go | 2 | 50 Go VDI dynamique | Créée |
| `DC-OUJDA` | Windows Server 2025 Evaluation | 4 Go | 2 | 60 Go VDI dynamique | Créée |
| `PC-OUJDA-01` | Windows 11 Enterprise Evaluation | 4 Go | 2 | 50 Go VDI dynamique | Créée |
| `RTR-SBTX` | OPNsense / FreeBSD 64 bits | 1 Go | 1 | 10 Go VDI dynamique | Créée |

Les disques virtuels sont dynamiques : ils n'occupent sur le poste hôte que l'espace réellement utilisé.

## Réseaux virtuels

| Réseau | Type VirtualBox | Machines connectées | Rôle |
| --- | --- | --- | --- |
| `NAT` | NAT | `RTR-SBTX` — Adaptateur 1 | Accès Internet temporaire du routeur |
| `SBTX-CASA` | Internal Network | `DC-CASA`, `PC-CASA-01`, `RTR-SBTX` — Adaptateur 2 | Site Casablanca |
| `SBTX-OUJDA` | Internal Network | `DC-OUJDA`, `PC-OUJDA-01`, `RTR-SBTX` — Adaptateur 3 | Site Oujda |

## Paramètres importants

### Serveurs et postes clients

- `DC-CASA` et `PC-CASA-01` sont connectés au réseau `SBTX-CASA`.
- `DC-OUJDA` et `PC-OUJDA-01` sont connectés au réseau `SBTX-OUJDA`.
- Les deux postes Windows 11 utilisent UEFI, Secure Boot et TPM 2.0.

![Réseau de DC-CASA](../assets/02-virtualisation/02-06-reseau-dc-casa.png)

![TPM 2.0 de PC-CASA-01](../assets/02-virtualisation/02-13-tpm-pc-casa-active.png)

![Réseau de DC-OUJDA](../assets/02-virtualisation/02-20-reseau-dc-oujda.png)

### Routeur inter-sites

`RTR-SBTX` possède trois interfaces réseau :

1. Adaptateur 1 : NAT — accès Internet temporaire.
2. Adaptateur 2 : `SBTX-CASA` — réseau Casablanca.
3. Adaptateur 3 : `SBTX-OUJDA` — réseau Oujda.

![Interface Oujda du routeur](../assets/02-virtualisation/02-32-reseau-routeur-oujda.png)

## Captures conservées

Les captures de création, ressources, disques et cartes réseau sont archivées dans le dossier [`assets/02-virtualisation`](../assets/02-virtualisation/). Elles suivent la numérotation chronologique `02-01` à `02-33`.

Le déroulement complet avec toutes les captures est disponible dans le [guide visuel pas à pas](GUIDE_PAS_A_PAS.md).

## Validation

- ![Terminé](../assets/check-complete.svg) Les cinq machines virtuelles sont créées.
- ![Terminé](../assets/check-complete.svg) Les deux réseaux internes sont configurés.
- ![Terminé](../assets/check-complete.svg) Les interfaces du routeur sont affectées aux bons réseaux.
- ![Terminé](../assets/check-complete.svg) UEFI, Secure Boot et TPM 2.0 sont activés sur les postes Windows 11.

![Topologie VirtualBox validée](../assets/02-virtualisation/02-33-topologie-virtualbox.png)

## Prochaine étape

Installer Windows Server sur `DC-CASA`, puis configurer son adresse IP statique et le domaine Active Directory dans l'[étape 03](../03-dc-casa/README.md).
