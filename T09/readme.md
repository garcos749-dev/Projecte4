# **T09: Servidor de fitxers Linux – NFS (tasca individual)**

## **Versió estil “punt 8”**

## **1. Introducció**

1. El projecte entra ara en un requisit tècnic molt comú: **centralització de dades en entorns Linux**.
2. Molts clients demanen un espai compartit per evitar caos de versions i pèrdues d’eficiència.

---

# **2. Cas del client: DevOptimize Solutions**

1. Startup dedicada al desenvolupament de programari, treballen **exclusivament amb Linux**.
2. Problema actual:

   * Codi font i documents **descontrolats**.
   * Cada desenvolupador té còpies locals.
   * Constant **desalineació de versions**.
   * Manca d’eficiència en el flux de treball.
3. Necessiten un **servidor de fitxers centralitzat**.
4. Com tot l’entorn és Linux, la solució òptima és **NFS (Network File System)**.
5. El client **NO utilitza autenticació centralitzada** i, de moment, no pensa implementar-la.

---

# **3. La vostra missió**

1. Crear una **demostració funcional** per ensenyar al client:

   * Com quedarà la solució proposada.
   * Quines **limitacions** tindrà sense autenticació centralitzada.
2. Implementar:

   * Un **servidor NFS (NFSv3)**.
   * Un **client Linux** que consumeixi els recursos compartits.
3. Crear **usuaris i grups** per simular l’entorn de treball del client.
4. Demostrar el **control d’accés** mitjançant:

   * Configuració de `/etc/exports`
   * Permisos del sistema de fitxers: `chmod`, `chown`, `chgrp`
5. Mostra al client com NFS gestiona:

   * Propietaris
   * Grups
   * UID/GID
   * Permisos segons exportacions

---

# **4. Recursos i instruccions de la tasca**

1. El repositori oficial amb la descripció detallada és:
   **[https://github.com/SMX2n/Projecte04-NFS](https://github.com/SMX2n/Projecte04-NFS)**
2. En aquest repositori trobaràs:

   * Esquema de xarxa
   * Configuració del servidor
   * Configuració del client
   * Exercicis de control d’accés
   * Validacions a realitzar

---

# **5. Materials i links de suport**

1. Material propi del Moodle:

   * **UD5. AA1. NFS**
2. Guia d’instal·lació (Serveis Linux):

   * Ruiz, P. (2021). *NFS Parte 1 – Instalación en servidor Ubuntu 20.04 LTS*
     [https://somebooks.es/nfs-parte-1-instalacion-en-un-servidor-ubuntu-20-04-lts/](https://somebooks.es/nfs-parte-1-instalacion-en-un-servidor-ubuntu-20-04-lts/)
   * Ruiz, P. (2021). *NFS Parte 2 – Instalación en cliente Ubuntu 20.04 LTS*
     [https://somebooks.es/nfs-parte-2-instalacion-en-un-cliente-ubuntu-20-04-lts/](https://somebooks.es/nfs-parte-2-instalacion-en-un-cliente-ubuntu-20-04-lts/)
3. Documentació oficial Ubuntu Server:

   * [https://documentation.ubuntu.com/server/how-to/networking/install-nfs/](https://documentation.ubuntu.com/server/how-to/networking/install-nfs/)

---
