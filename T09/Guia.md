# T09: Guia NFS — Configuració d'usuaris, permisos i recursos compartits
Aquest document explica, pas a pas i de manera senzilla, com configurar un servidor NFS i un client Zorin, com gestionar usuaris i grups, posar permisos i muntar els recursos compartits.

1. Preparació de grups i usuaris al servidor

![imatge](./img/foto1.png)

Creem els usuaris dev01 i admin01, els assignem als grups corresponents, amb el seu directori personal i amb la shell bash per defecte.

![imatge](./img/foto3.png)
![imatge](./img/foto4.png)

Creem els directoris de treball admin_tools i dev_projects.

![imatge](./img/foto5.png)

Assignem el propietari i el grup a les carpetes (usuari root i grup admins o devs, segons correspongui) i configurem els permisos.

![imatge](./img/foto6.png)

2. Configuració del servei NFS al servidor
Instal·lem NFS 
![imatge](./img/foto50.png)

Definim els recursos que es volen compartir al fitxer /etc/exports.

![imatge](./img/foto7.png)

Reiniciem el servei i comprovem l’estat del nfs-kernel-server.

![imatge](./img/foto11.png)

Verifiquem els exports 

![imatge](./img/foto9.png)

Verifiquem que els usuaris i els grups s’han creat correctament.

![imatge](./img/foto12.png)

3. Preparació al client Zorin

Instal·lem l’eina “Users and Groups” per gestionar els usuaris localment.

![imatge](./img/foto13.png)
Repliquem els usuaris i grups amb les mateixes UIDs i GIDs que al servidor.
![imatge](./img/foto14.png)
![imatge](./img/foto15.png)
![imatge](./img/foto17.png)

Al servidor, creem un fitxer de prova dins del recurs compartit.
![imatge](./img/foto18.png)

Actualitzem repositoris a Zorin.

![imatge](./img/foto19.png)

Instal·lem nfs-common al client.

![imatge](./img/foto20.png)

Llistem els recursos compartits del servidor amb showmount -e.

![imatge](./img/foto21.png)
Creem la carpeta de muntatge 
![imatge](./img/foto22.png)

Muntem el recurs compartit en la carpeta creada.

![imatge](./img/foto23.png)

4. Proves de permisos i ajustos d'exports
Intentem crear un fitxer com a root des del client; si no és possible, cal afegir no_root_squash al fitxer /etc/exports.

![imatge](./img/foto24.png)

Afegim el paràmetre no_root_squash al fitxer /etc/exports i apliquem els canvis.

![imatge](./img/foto25.png)

Tornem a muntar i provem de crear un arxiu com a root de nou.

![imatge](./img/foto26.png)

Modifiquem el fitxer /etc/exports per al recurs dev_projects: la xarxa 192.168.56.0 amb permisos d’escriptura i la IP 192.168.56.105 només amb permisos de lectura.

![imatge](./img/foto27.png)

Reiniciem el servei i comprovem que arrenca correctament.

![imatge](./img/foto28.png)

Creem la carpeta de muntatge per dev_projects i la muntem.

![imatge](./img/foto29.png)

Com a usuari dev01, provem de crear un fitxer (hauria de ser possible a la xarxa amb permisos d’escriptura).

![imatge](./img/foto30.png)

Canviem la IP per comprovar accés de només lectura.

![imatge](./img/foto31.png)
![imatge](./img/foto32.png)

Tornem a muntar el recurs.

![imatge](./img/foto33.png)

Com a usuari dev01, provem d’escriure en un fitxer (no hauria de ser permès) i ho confirmem.

![imatge](./img/foto34.png)

Amb admin tampoc ha de permetre l'escriptura.

![imatge](./img/foto35.png)

5. Muntatge automàtic amb /etc/fstab
Configurem el fitxer /etc/fstab perquè els recursos es muntin automàticament a l’inici del sistema.
![imatge](./img/foto36.png)







