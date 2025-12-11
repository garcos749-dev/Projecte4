# Guia completa amb espais per a les fotos (45 fotos)

## 1. Creació de grups i usuaris

Afegim els grups **admins** i **devs**.



![FOTO 1](../img/foto1.png)


Afegim l’usuari **admin01** i l’assignem al grup admins.



![FOTO 2](../img/foto3.png)


Afegim l’usuari **dev01** i l’assignem al grup devs.



![FOTO 3](../img/foto4.png)


Verifiquem que els usuaris han estat creats.



![FOTO 4](../img/foto2.png)


Verifiquem que els grups existeixen.



![FOTO 5](../img/foto5.png)


---

## 2. Creació i configuració de directoris

Creem les carpetes:

* **admin_tools**
* **dev_projects**



![FOTO 6](../img/foto6.png)


Assignem **root** com a propietari dels directoris.



![FOTO 7](../img/foto7.png)


Assignem els grups **admins** i **devs**.



![FOTO 8](../img/foto8.png)


Comprovem permisos.



![FOTO 9](../img/foto9.png)


---

## 3. Instal·lació i configuració de NFS al servidor

Instal·lem:


apt install nfs-kernel-server




![FOTO 10](../img/foto10.png)


Editem **/etc/exports**.



![FOTO 11](../img/foto11.png)


Afegim els recursos inicials.



![FOTO 12](../img/foto12.png)


Reiniciem el servei.



![FOTO 13](../img/foto13.png)


Comprovem l’estat del servei:


systemctl status nfs-kernel-server




![FOTO 14](../img/foto14.png)


Verifiquem els exports:


exportfs -u




![FOTO 15](../img/foto15.png)


---

## 4. Configuració del client Zorin OS

Instal·lem *Users and Groups*.



![FOTO 16](../img/foto16.png)


Creem els mateixos grups que al servidor.



![FOTO 17](../img/foto17.png)


Creem els usuaris equivalents.



![FOTO 18](../img/foto18.png)


---

## 5. Prova inicial de recurs compartit

Creem un fitxer de prova a **admin_tools/** des del servidor.



![FOTO 19](../img/foto19.png)


Comprovem que el fitxer existeix.



![FOTO 20](../img/foto20.png)


---

## 6. Preparació del client Zorin

Actualitzem i instal·lem NFS:


apt update
apt install nfs-common




![FOTO 21](../img/foto21.png)


Mostrem els recursos exportats:


showmount -e <IP_SERVER>




![FOTO 22](../img/foto22.png)


Creem el punt de muntatge:


mkdir /mnt/admin_tools




![FOTO 23](../img/foto23.png)


Muntem el recurs:


mount <IP_SERVER>:/admin_tools /mnt/admin_tools




![FOTO 24](../img/foto24.png)


Intentem crear un fitxer com a root (fallada).



![FOTO 25](../img/foto25.png)


---

## 7. Afegim **no_root_squash**

Modifiquem **/etc/exports**:


no_root_squash




![FOTO 26](../img/foto26.png)


Reiniciem NFS:



![FOTO 27](../img/foto27.png)


Tornem a provar:



![FOTO 28](../img/foto28.png)


---

## 8. Configuració de permisos per xarxa (dev_projects)

Modifiquem **/etc/exports**:

* 192.168.56.0 → RW
* 192.168.56.105 → RO



![FOTO 29](../img/foto29.png)


Reiniciem:



![FOTO 30](../img/foto30.png)


Creem /mnt/dev_projects:



![FOTO 31](../img/foto31.png)


Muntem el recurs:



![FOTO 32](../img/foto32.png)


---

## 9. Proves d’escriptura segons xarxa

Amb **dev01**, provem de crear un fitxer:



![FOTO 33](../img/foto33.png)


Confirmem que s’ha creat.



![FOTO 34](../img/foto34.png)


Canviem la IP:



![FOTO 35](../img/foto35.png)


Tornem a muntar:



![FOTO 36](../img/foto36.png)


Provem d’escriure:



![FOTO 37](../img/foto37.png)


Amb admin tampoc podem escriure.



![FOTO 38](../img/foto38.png)


Comprovem que podem llegir.



![FOTO 39](../img/foto39.png)


---

## 10. Automuntatge amb /etc/fstab

Editem el fitxer:



![FOTO 40](../img/foto40.png)


Reiniciem el daemon:


systemctl daemon-reload




![FOTO 41](../img/foto41.png)


Fem:


mount -a




![FOTO 42](../img/foto42.png)

Comprovem que està muntat:



![FOTO 43](../img/foto43.png)


Reiniciem el sistema:



![FOTO 44](../img/foto44.png)


Comprovem que el muntatge és automàtic:



![FOTO 45](../img/foto45.png)


---


