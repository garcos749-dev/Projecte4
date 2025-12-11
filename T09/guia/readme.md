# Guia de configuració NFS i gestió d’usuaris


Afegim els grups **admins** i **devs**.  

![FOTO 1](../img/foto1.png)

Creem l’usuari **dev01** i l’assignem al grup **devs**, amb el directori personal i **bash** com a shell per defecte.  

![FOTO 4](../img/foto4.png)

Creem l’usuari **admin01** i l’assignem al grup **admins**, amb el seu directori personal i shell **bash** per defecte.  

![FOTO 3](../img/foto3.png)

Creem els directoris **admin_tools** i **dev_projects**.  

![FOTO 5](../img/foto5.png)

Assignem la propietat dels directoris a **root** i el grup corresponent a **admins** o **devs**.  

![FOTO 6](../img/foto6.png)

Instal·lem el servidor **NFS** (`nfs-kernel-server`).  

![FOTO 7](../img/foto7.png)

Definim els recursos compartits en `/etc/exports`.  

![FOTO 8](../img/foto8.png)

Comprovem l’estat del servei **nfs-kernel-server**.  

![FOTO 9](../img/foto9.png)

Verifiquem que els **exports** s’han creat amb `exportfs -u`.  

![FOTO 10](../img/foto10.png)

Comprovem que els usuaris i els grups s’han creat correctament.  

![FOTO 11](../img/foto11.png)

---

Al **client Zorin**, instal·lem **Users and Groups** per poder gestionar els usuaris.  

![FOTO 12](../img/foto12.png)

Creem els mateixos usuaris i grups amb les mateixes IPs que al servidor.  

![FOTO 13](../img/foto13.png)

---

Creem un arxiu de prova amb contingut des del servidor al recurs compartit `admin_tools/`.  

![FOTO 14](../img/foto14.png)

---

Actualitzem els repositoris de Zorin.  

![FOTO 15](../img/foto15.png)

Instal·lem `nfs-common`.  

![FOTO 16](../img/foto16.png)

Fem `showmount -e <IP_SERVER>` des del client Zorin per veure els recursos compartits disponibles.  

![FOTO 17](../img/foto17.png)

Creem la carpeta de muntatge: `/mnt/admin_tools`.  

![FOTO 18](../img/foto18.png)

Muntem el recurs compartit a la carpeta que acabem de crear.  

![FOTO 19](../img/foto19.png)

Intentem crear un arxiu com a **root**; no ens deixa, així que afegirem l’opció **no_root_squash**.  

![FOTO 20](../img/foto20.png)

Afegim el paràmetre `no_root_squash` als **exports**.  

![FOTO 21](../img/foto21.png)

Ara tornem a provar de crear un arxiu i ja ens deixa, ja que estem actuant com a root en el recurs compartit gràcies a `no_root_squash`.  

![FOTO 22](../img/foto22.png)

---

Modifiquem `/etc/exports` al servidor per ajustar el recurs `dev_projects`:  

* La xarxa **192.168.56.0** tindrà permisos d’escriptura (RW).  
* L’altra xarxa **192.168.56.105** només podrà llegir (RO).  

![FOTO 23](../img/foto23.png)

Reiniciem el servei i comprovem que s’inicialitza correctament.  

![FOTO 24](../img/foto24.png)

Creem la carpeta per muntar el nou recurs `dev_projects` i la muntem.  

![FOTO 25](../img/foto25.png)

---

Com a usuari **dev01**, intentem crear un arxiu; ens hauria de deixar.  

![FOTO 26](../img/foto26.png)

Confirmem que efectivament es crea. Ara canviem la IP per verificar si només es permet llegir.  

![FOTO 27](../img/foto27.png)

Comprovem que tenim la IP correcta.  

![FOTO 28](../img/foto28.png)

Tornem a muntar el recurs.  

![FOTO 29](../img/foto29.png)

Ara, amb el mateix usuari **dev01**, provem d’escriure a un arxiu; no hauria de deixar i efectivament no deixa.  

![FOTO 30](../img/foto30.png)

Comprovem que amb l’usuari **admin** tampoc es pot escriure.  

![FOTO 31](../img/foto31.png)

---

Configurem el fitxer `/etc/fstab` per fer que els recursos es muntin automàticament en iniciar sessió, evitant haver de muntar-los manualment.  

![FOTO 32](../img/foto32.png)

Reiniciem el daemon:

```bash
systemctl daemon-reload
