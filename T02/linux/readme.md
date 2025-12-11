# Part 2 — Còpia de seguretat a Linux amb Duplicity + cron
Objectiu: configurar còpies completes i incrementals del directori /home en un volum extern muntat manualment a /media/backup. La documentació ha d’incloure les captures de pantalla de cada etapa, i el text no ha de contenir comandos.

Seqüència de la prova de concepte
Preparació de la unitat de còpia (10 GB): detecció del disc, formatació a XFS i creació del punt de muntatge.

![imatge](../img/foto20.png)

Formatació en XFS i habilitació del punt de muntatge

![imatge](../img/foto21.png)

Es defineix el sistema de fitxers i el punt de muntatge per a la unitat auxiliar.

Muntatge manual a /media/backup.

![imatge](../img/foto22.png)

![imatge](../img/foto23.png)

Crear usuaris.

![imatge](../img/foto25.png)



El volum queda disponible per rebre còpies de seguretat.

Instal·lació de Duplicity.

Instal·lar duplicity

![imatge](../img/foto24.png)

Instal·lació de l'eina de còpia per entorns Linux.

Preparació de dades de prova: creació d’usuaris addicionals i generació de fitxers de 10 MB dins de /home

![imatge](../img/foto26.png)

Fitxers de prova creats

Creem usuaris i contingut per validar les còpies.

Fer una còpia completa de /home cap a la unitat de backup.

![imatge](../img/foto27.png)

![imatge](../img/foto28.png)


Backup complet /home Verificar contingut backup

Validació de la restauració: eliminació i recuperació de fitxers

![imatge](../img/foto29.png)

![imatge](../img/foto30.png)


Esborrar fitxers Restore complet

Es simula una pèrdua de dades i es verifica la recuperació.

Fer una còpia incremental després d'afegir un fitxer de ~4 MB.

![imatge](../img/foto31.png)

![imatge](../img/foto32.png)

![imatge](../img/foto33.png)



Crear nou fitxer Backup incremental Comprovació versions

Es genera un canvi menor i s'executa una còpia incremental per observar diferències.

Desmuntar la unitat de backup.

![imatge](../img/foto34.png)


Desmuntar

La unitat queda desconnectada per seguretat.

Automatització amb scripts i cron (captures del procés).


Creació dels scripts i assignació de permiso
Es generen els scripts necessaris i se’ls dóna permís d’execució.

![imatge](../img/foto35.png)

![imatge](../img/foto36.png)

![imatge](../img/foto39.png)

![imatge](../img/foto40.png)


Edició del fitxer crontab per programar les tasques
S’incorporen les ordres de còpia programada, incloent-hi la incremental.

![imatge](../img/foto37.png)

![imatge](../img/foto41.png)

