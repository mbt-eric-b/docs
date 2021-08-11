---
title: Come utilizzare l’API Nova
excerpt: Come utilizzare l'API Nova
slug: come_utilizzare_lapi_nova
legacy_guide_number: g1935
section: Gestione via OpenStack
---


## 
Se vuoi automatizzare le tue operazioni sul Public Cloud, puoi utilizzare le API di OpenStack per creare diversi script.
Il client Nova di OpenStack ti consente di gestire le tue istanze e i tuoi dischi.

Ad esempio, puoi craere istanze aggiuntive per evitare un sovraccarico della tua infrastruttura quando i tuoi sistemi di monitoring rilevano picchi di carico, oppure pianificare la creazione di Snapshot.

Questa guida ti mostra come utilizzare le API OpenStack per gestire le tue istanze con il client Python Nova.


## Requisiti necessari

- [Prepara il tuo ambiente di sviluppo per utilizzare l'API OpenStack]({legacy}1851)
- [Imposta le variabili d'ambiente OpenStack]({legacy}1852)




## Documentazione Nova
Per visualizzare la lista dei comandi disponibili, consulta la documentazione del client:


```
admin@server-1:~$ nova help
```


Per visualizzare le informazioni relative a un comando specifico, aggiungi "help" all'inizio:


```
admin@server-1:~$ nova help flavor-list

usage: nova flavor-list [--extra-specs] [--all]

Print a list of available 'flavors' (sizes of servers).

Optional arguments:
--extra-specs Get extra-specs of each flavor.
--all Display all flavors (Admin only).
```


La documentazione del client Nova è disponibile anche sul [sito OpenStack](http://docs.openstack.org/cli-reference/content/novaclient_commands.html)


## Aggiungi una chiave SSH pubblica
Prima di tutto, aggiungi una chiave SSH pubblica per accedere alle istanze.


- Visualizza la lista dei comandi associati alla chiave SSH:


```
admin@server-1:~$ nova help | grep keypair

keypair-add Create a new key pair for use with servers.
keypair-delete Delete keypair given by its name.
keypair-list Print a list of keypairs for a user
keypair-show Show details about the given keypair.
```


- Aggiungi la chiave SSH pubblica:


```
admin@server-1:~$ nova keypair-add --pub-key .ssh/id_rsa.pub SSHKEY
```


- Visualizza la lista delle chiavi SSH disponibili:


```
admin@server-1:~$ nova keypair-list

+--------+-------------------------------------------------+
| Name | Fingerprint |
+--------+-------------------------------------------------+
| SSHKEY | 0e:93:fb:90:82:xx:xx:xx:xx:xx:xx:6e:22:42:c3:ea |
+--------+-------------------------------------------------+
```





## Visualizza la lista dei modelli di istanze
Recupera l'ID del modello che vuoi utilizzare eseguendo questo comando:


```
admin@server-1:~$ nova flavor-list
+--------------------------------------+------------+-----------+------+-----------+---------+-------+-------------+-----------+
| ID | Name | Memory_MB | Disk | Ephemeral | Swap_MB | VCPUs | RXTX_Factor | Is_Public |
+--------------------------------------+------------+-----------+------+-----------+---------+-------+-------------+-----------+
| 0c36bb1d-bd1e-4294-ac75-60fd727054c8 | win-eg-15 | 15000 | 400 | 0 | | 4 | 1.0 | True |
| 0e2b8841-d764-49b4-b2ac-24c8df2c6806 | sp-30 | 30000 | 200 | 0 | | 2 | 1.0 | True |
| 169e7020-0436-4e8c-b2c8-213a57a044b5 | win-sp-120 | 120000 | 800 | 0 | | 8 | 1.0 | True |
| 18811d09-053e-4ad0-b297-3c11ceefd136 | sp-60 | 60000 | 400 | 0 | | 4 | 1.0 | True |
| 1e2c13fc-4ba9-4773-a13e-75ce96fb4e96 | eg-120 | 120000 | 1600 | 0 | | 32 | 1.0 | True |
| 1e5a7cf5-d58c-4633-8069-5aba49b00be1 | win-sp-240 | 240000 | 1600 | 0 | | 16 | 1.0 | True |
| 22096e9d-5150-4f54-bb8d-6c8b243a28bb | win-sp-60 | 60000 | 400 | 0 | | 4 | 1.0 | True |
| 23ec7924-483c-4414-9aaf-bf03575f0bfe | eg-15 | 15000 | 400 | 0 | | 4 | 1.0 | True |
| 24c1f706-3278-4ca7-a773-7df7f999cf14 | win-eg-60 | 60000 | 1600 | 0 | | 16 | 1.0 | True |
| 30b43ca1-131f-4b0d-8087-e03bc99f7ec6 | sp-120 | 120000 | 800 | 0 | | 8 | 1.0 | True |
| 3502c448-8c96-4062-bf78-c5d2ac962e6d | win-eg-120 | 120000 | 1600 | 0 | | 32 | 1.0 | True |
| 3a9711d2-a4fb-4d2f-a3cd-1972fd53eb5e | vps-ssd-3 | 8000 | 40 | 0 | | 2 | 1.0 | True |
| 6763bd1b-5d23-4c87-aca7-d46e35d343a4 | win-eg-7 | 7000 | 200 | 0 | | 2 | 1.0 | True |
| 7eacbe7c-5033-4123-8eec-d61bf27359f9 | win-sp-30 | 30000 | 200 | 0 | | 2 | 1.0 | True |
| 8f08b006-a68b-4eed-80cf-36f8212f8d73 | win-eg-30 | 30000 | 800 | 0 | | 8 | 1.0 | True |
| 98c1e679-5f2c-4069-b4da-4a4f7179b758 | vps-ssd-1 | 2000 | 10 | 0 | | 1 | 1.0 | True |
| a42a6051-16c7-4563-9cca-9c1abf36e460 | sp-240 | 240000 | 1600 | 0 | | 16 | 1.0 | True |
| b41c89be-7b7d-4ecc-9cd8-bea145bbbd76 | eg-7 | 7000 | 200 | 0 | | 2 | 1.0 | True |
| b62d1735-774d-4983-9ed6-283c921d29d7 | eg-30 | 30000 | 800 | 0 | | 8 | 1.0 | True |
| c3d1d22a-03b3-4fa4-bcc4-1dff4e2b2d32 | vps-ssd-2 | 4000 | 20 | 0 | | 1 | 1.0 | True |
| ccb922b6-04ad-422d-a8bc-7aff1eae6954 | eg-60 | 60000 | 1600 | 0 | | 16 | 1.0 | True |
+--------------------------------------+------------+-----------+------+-----------+---------+-------+-------------+-----------+
```




## Visualizza la lista delle immagini disponibili
Per recuperare l'ID dell'immagine che verrà utilizzata per la tua istanza, esegui questo comando:

[code]admin@server-1:~$ glance image-list
+--------------------------------------+------------------------+--------+--------+
|ID|Name|Status|Server|

+--------------------------------------+------------------------+--------+--------+
|c17f13b5-587f-4304-b550-eb939737289a|Centos 7|ACTIVE||
|73958794-ecf6-4e68-ab7f-1506eadac05b|Debian 7|ACTIVE||
|bdcb5042-3548-40d0-b06f-79551d3b4377|Debian 8|ACTIVE||
|7250cc02-ccc1-4a46-8361-a3d6d9113177|Fedora 19|ACTIVE||
|57b9722a-e6e8-4a55-8146-3e36a477eb78|Fedora 20|ACTIVE||
|3bda2a66-5c24-4b1d-b850-83333b580674|Ubuntu 12.04|ACTIVE||
|9bfac38c-688f-4b63-bf3b-69155463c0e7|Ubuntu 14.04|ACTIVE||
|6a123897-a5bb-46cd-8f5d-ecf9ab9877f2|Windows-Server-2012-r2|ACTIVE||

+--------------------------------------+------------------------+--------+--------+


## Crea un'istanza
Crea l'istanza utilizzando i dati recuperati:


```
admin@server-1:~$ nova boot --key_name SSHKEY --flavor 98c1e679-5f2c-4069-b4da-4a4f7179b758 --image bdcb5042-3548-40d0-b06f-79551d3b4377 Instance1
```


Dopo qualche minuto, controlla la lista delle istanze esistenti per trovare quella appena creata:


```
admin@server-1:~$ nova list
+--------------------------------------+----------------------------------------+--------+------------+-------------+-------------------------+
| ID | Name | Status | Task State | Power State | Networks |
+--------------------------------------+----------------------------------------+--------+------------+-------------+-------------------------+
| 81d01a19-b2d5-454d-98d9-bd8992ec2037 | Instance1 | ACTIVE | - | Running | Ext-Net=149.xxx.xxx.192 |
+--------------------------------------+----------------------------------------+--------+------------+-------------+-------------------------+
```




## Elimina un'istanza
Per eliminare un'istanza, utilizza questo comando:

```
admin@serveur-1:~$ nova delete Instance1
Request to delete server Instance1 has been accepted.
```




## 
[Ritorna all'indice delle guide Cloud]({legacy}1785)

