---
title: Copier un datastore entre deux PCC
slug: datastore-copy
excerpt: Découvrez comment acceder à la copie d'un datastore d'un PCC vers un autre PCC via les API OVHcloud
section: Fonctionnalités OVHcloud
hidden: true
---

**Dernière mise à jour le 25/03/2021**

## Objectif

Suite à l'incident survenu sur le datacentre SBG, vous pouvez migrer les datastores d'un PCC concerné par l'incident vers un PCC de destination.

**Découvrez comment acceder à la copie d'un datastore d'un PCC vers un autre PCC via les API OVHcloud**

## Prérequis

- Être connecté aux [API OVHcloud](https://api.ovh.com/)
- Être connecté à votre [interface vSphere](../connexion-interface-vsphere/).

> [!warning]
>
> Si votre PCC source dispose d'une certification [HDS](https://www.ovhcloud.com/fr/enterprise/certification-conformity/hds/) ou [PCI-DSS](https://www.ovhcloud.com/fr/enterprise/certification-conformity/pci-dss/), votre PCC de destination devra disposer de la même certification **active** afin de récupérer le datastore.
>
> Pour plus d'informations, consultez notre guide [Activation de la mise en conformité Healthcare (HDS) ou Payment Services (PCI DSS)](../activer-l-option-hds-ou-pci-dss/).
>

## En pratique

Si vous n'êtes pas habitué au fonctionnement des API OVHcloud, consultez notre guide [Premiers pas avec les API OVHcloud](../../api/api-premiers-pas/).

### Etape 1 : récupérer le filer du datastore

Vous devez d'abord cibler le filerId à migrer.

Connectez-vous sur [https://api.ovh.com/](https://api.ovh.com/) et utilisez l'appel suivant :

> [!api]
>
> @api {GET} /dedicatedCloud/{serviceName}/datacenter/{datacenterId}/filer

Renseignez les variables :

- serviceName : le nom du PCC d'origine situé à SBG (ex: pcc-192-0-2-15).
- datacenterId : l'ID du datacentre source (ex: 1337).

### Etape 2 : lancer la copie du datastore

> [!warning]
>
> Le PCC de destination doit être situé dans une zone différente de sbg1a.
>

Une fois le filerId identifié, utilisez l'appel suivant pour migrer le datastore vers le PCC de destination :

> [!api]
>
> @api {POST} /dedicatedCloud/{serviceName}/datacenter/{datacenterId}/linkFilerFromSbg

Renseignez les variables :

- serviceName : le nom du PCC de destination (ex: pcc-192-0-2-50).
- datacenterId: l'ID du datacentre de destination (ex: 1515).
- filerId : le filerId récupéré à l'étape précédente (ex: 001234).

La réplication des données peut durer plusieurs heures. Lorsque celle-ci est terminée, vous recevrez un e-mail confirmant la réussite de la migration.

### Etape 3 : accéder à la copie depuis vSphere

Dans votre [interface vSphere](../connexion-interface-vsphere/), placez-vous dans la vue `Stockage`{.action}.

![ds_restore](images/ds-restore.png){.thumbnail}

La copie est présentée au travers d'un datastore sur tous les hosts du datacenter de destination, sous le nom `restore-XXXXXX` (XXXXXX désignant le numéro du datastore source).

> [!warning]
>
> Le datastore récupéré est en lecture-seule.
>

Pour les machines virtuelles, il faut [enregistrer celle-ci dans l'inventaire vSphere](../vsphere-register-vm-vmx) puis [cloner](../cloner-une-vm) celle-ci vers un des datastores avant de pouvoir démarrer celle-ci.

## Aller plus loin

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com/>.