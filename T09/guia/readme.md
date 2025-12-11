# Guia completa amb espais per a les fotos (45 fotos)

## 1. Creació de grups i usuaris

Afegim els grups **admins** i **devs**.

👉 *Foto 1 – Creació dels grups*

```
![FOTO 1](../img/foto1.png)
```

Afegim l’usuari **admin01** i l’assignem al grup admins.

👉 *Foto 2 – Creació de l’usuari admin01*

```
![FOTO 2](../img/foto2.png)
```

Afegim l’usuari **dev01** i l’assignem al grup devs.

👉 *Foto 3 – Creació de l’usuari dev01*

```
![FOTO 3](../img/foto3.png)
```

Verifiquem que els usuaris han estat creats.

👉 *Foto 4 – Verificació usuaris*

```
![FOTO 4](../img/foto4.png)
```

Verifiquem que els grups existeixen.

👉 *Foto 5 – Verificació grups*

```
![FOTO 5](../img/foto5.png)
```

---

## 2. Creació i configuració de directoris

Creem les carpetes:

* **admin_tools**
* **dev_projects**

👉 *Foto 6 – Directoris creats*

```
![FOTO 6](../img/foto6.png)
```

Assignem **root** com a propietari dels directoris.

👉 *Foto 7 – Propietari root*

```
![FOTO 7](../img/foto7.png)
```

Assignem els grups **admins** i **devs**.

👉 *Foto 8 – Assignació de grups als directoris*

```
![FOTO 8](../img/foto8.png)
```

Comprovem permisos.

👉 *Foto 9 – Permisos correctes*

```
![FOTO 9](../img/foto9.png)
```

---

## 3. Instal·lació i configuració de NFS al servidor

Instal·lem:

```
apt install nfs-kernel-server
```

👉 *Foto 10 – Instal·lació de NFS*

```
![FOTO 10](../img/foto10.png)
```

Editem **/etc/exports**.

👉 *Foto 11 – Fitxer /etc/exports*

```
![FOTO 11](../img/foto11.png)
```

Afegim els recursos inicials.

👉 *Foto 12 – Recursos exportats*

```
![FOTO 12](../img/foto12.png)
```

Reiniciem el servei.

👉 *Foto 13 – Servei reiniciat*

```
![FOTO 13](../img/foto13.png)
```

Comprovem l’estat del servei:

```
systemctl status nfs-kernel-server
```

👉 *Foto 14 – Estat del servei*

```
![FOTO 14](../img/foto14.png)
```

Verifiquem els exports:

```
exportfs -u
```

👉 *Foto 15 – Comprovació exportfs*

```
![FOTO 15](../img/foto15.png)
```

---

## 4. Configuració del client Zorin OS

Instal·lem *Users and Groups*.

👉 *Foto 16 – Users and Groups a Zorin*

```
![FOTO 16](../img/foto16.png)
```

Creem els mateixos grups que al servidor.

👉 *Foto 17 – Grups creats al client*

```
![FOTO 17](../img/foto17.png)
```

Creem els usuaris equivalents.

👉 *Foto 18 – Usuaris creats al client*

```
![FOTO 18](../img/foto18.png)
```

---

## 5. Prova inicial de recurs compartit

Creem un fitxer de prova a **admin_tools/** des del servidor.

👉 *Foto 19 – Fitxer de prova*

```
![FOTO 19](../img/foto19.png)
```

Comprovem que el fitxer existeix.

👉 *Foto 20 – Confirmació del fitxer*

```
![FOTO 20](../img/foto20.png)
```

---

## 6. Preparació del client Zorin

Actualitzem i instal·lem NFS:

```
apt update
apt install nfs-common
```

👉 *Foto 21 – Instal·lació nfs-common*

```
![FOTO 21](../img/foto21.png)
```

Mostrem els recursos exportats:

```
showmount -e <IP_SERVER>
```

👉 *Foto 22 – showmount*

```
![FOTO 22](../img/foto22.png)
```

Creem el punt de muntatge:

```
mkdir /mnt/admin_tools
```

👉 *Foto 23 – Punt de muntatge creat*

```
![FOTO 23](../img/foto23.png)
```

Muntem el recurs:

```
mount <IP_SERVER>:/admin_tools /mnt/admin_tools
```

👉 *Foto 24 – Recurs muntat al client*

```
![FOTO 24](../img/foto24.png)
```

Intentem crear un fitxer com a root (fallada).

👉 *Foto 25 – Error d’escriptura*

```
![FOTO 25](../img/foto25.png)
```

---

## 7. Afegim **no_root_squash**

Modifiquem **/etc/exports**:

```
no_root_squash
```

👉 *Foto 26 – Export modificat*

```
![FOTO 26](../img/foto26.png)
```

Reiniciem NFS:

👉 *Foto 27 – Reinici servei NFS*

```
![FOTO 27](../img/foto27.png)
```

Tornem a provar:

👉 *Foto 28 – Fitxer creat correctament amb root*

```
![FOTO 28](../img/foto28.png)
```

---

## 8. Configuració de permisos per xarxa (dev_projects)

Modifiquem **/etc/exports**:

* 192.168.56.0 → RW
* 192.168.56.105 → RO

👉 *Foto 29 – Configuració de xarxes*

```
![FOTO 29](../img/foto29.png)
```

Reiniciem:

👉 *Foto 30 – Reinici correcte*

```
![FOTO 30](../img/foto30.png)
```

Creem /mnt/dev_projects:

👉 *Foto 31 – Punt de muntatge*

```
![FOTO 31](../img/foto31.png)
```

Muntem el recurs:

👉 *Foto 32 – Recurs dev_projects muntat*

```
![FOTO 32](../img/foto32.png)
```

---

## 9. Proves d’escriptura segons xarxa

Amb **dev01**, provem de crear un fitxer:

👉 *Foto 33 – Escriptura correcta*

```
![FOTO 33](../img/foto33.png)
```

Confirmem que s’ha creat.

👉 *Foto 34 – Fitxer confirmat*

```
![FOTO 34](../img/foto34.png)
```

Canviem la IP:

👉 *Foto 35 – IP canviada*

```
![FOTO 35](../img/foto35.png)
```

Tornem a muntar:

👉 *Foto 36 – Recurs muntat amb nova IP*

```
![FOTO 36](../img/foto36.png)
```

Provem d’escriure:

👉 *Foto 37 – Error d’escriptura*

```
![FOTO 37](../img/foto37.png)
```

Amb admin tampoc podem escriure.

👉 *Foto 38 – Admin sense permisos*

```
![FOTO 38](../img/foto38.png)
```

Comprovem que podem llegir.

👉 *Foto 39 – Lectura correcta*

```
![FOTO 39](../img/foto39.png)
```

---

## 10. Automuntatge amb /etc/fstab

Editem el fitxer:

👉 *Foto 40 – /etc/fstab editat*

```
![FOTO 40](../img/foto40.png)
```

Reiniciem el daemon:

```
systemctl daemon-reload
```

👉 *Foto 41 – Daemon reload*

```
![FOTO 41](../img/foto41.png)
```

Fem:

```
mount -a
```

👉 *Foto 42 – mount -a correcte*

```
![FOTO 42](../img/foto42.png)
```

Comprovem que està muntat:

👉 *Foto 43 – Recursos muntats*

```
![FOTO 43](../img/foto43.png)
```

Reiniciem el sistema:

👉 *Foto 44 – Reinici del sistema*

```
![FOTO 44](../img/foto44.png)
```

Comprovem que el muntatge és automàtic:

👉 *Foto 45 – Muntatge automàtic correcte*

```
![FOTO 45](../img/foto45.png)
```

---

Si vols, te la puc:

✅ Convertir a PDF
✅ Posar portada, índex i numeració
✅ Afegir comandes destacades amb colors
Només digues!

