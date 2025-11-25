# **Cas pràctic DPR: Còpies de seguretat — Versió estil “punt 8”**

## **1. Introducció al cas**

1. Has dissenyat una política de còpies per al client *Muntatges i Serveis Tècnics SL*.
2. Ara cal crear guies tècniques amb proves de concepte perquè el personal pugui implementar les còpies de seguretat.

---

# **Part 1: Còpia de seguretat equips Windows**

## **2. Preparació de l’entorn**

1. Crea una màquina virtual Windows 11.
2. Afegeix dos discos:

   * Disc 1: Sistema operatiu
   * Disc 2: 10 GB per a còpies de seguretat
3. Crea un compte de Google (no escolar) per simular el cloud.

## **3. Política de còpia 3-2-1**

1. Fer còpia del perfil de l’usuari **cada hora** al disc secundari.
2. Fer còpia a **Google Drive a les 18:00**.
3. Utilitzar l’eina **Duplicati**.

## **4. Procediment pràctic**

1. Instal·la Duplicati.
2. Configura el pla de còpies locals i al cloud.
3. Afegeix arxius a **Documents** i altres carpetes de l’usuari.
4. Esborra el contingut de *Documents*.
5. Fes una **restauració** des del disc secundari.
6. Comprova la **restauració des de Google Drive**.

---

# **Part 2: Còpia de seguretat servidor Linux**

## **5. Preparació de la màquina Linux**

1. Crea una VM amb Ubuntu Server.
2. Afegeix un segon disc de 10 GB.
3. Inicialitza i formata el disc en **xfs**.
4. Munta el disc manualment a `/media/backup`.

## **6. Configuració de duplicity**

1. Instal·la **duplicity**.
2. Crea dos usuaris nous amb carpeta personal.
3. Genera **4 fitxers de 10 MB** a `/home/<usuari>`.
4. Fes una còpia de seguretat de `/home`.
5. Esborra els fitxers i comprova la restauració.
6. Afegeix un fitxer de **4 MB**, fes nova còpia i observa la còpia **incremental**.
7. Desmunta la unitat de backup.

---

# **Automatització amb scripts i cron**

## **7. Script de còpia completa**

1. Crea l’script `fullbackup.sh`.
2. Ha de fer una còpia completa de `/home` a la unitat muntada.
3. Defineix la variable d’entorn:
   `export PASSPHRASE=contrasenya`
4. Dona permisos d’execució.

## **8. Programació de la còpia completa**

1. Com a *root*, programa l’script al **cron**:

   * Execució cada **diumenge a les 23:00**.

## **9. Script de còpia incremental**

1. Crea `incrementalbackup.sh`.
2. Fa còpies incrementals de `/home`.
3. Afegeix `export PASSPHRASE=contrasenya`.
4. Dona permisos d’execució.

## **10. Programació de la còpia incremental**

1. Com a *root*, programa l’script de **dilluns a dissabte a les 23:00**.

---

# **11. Enllaços de suport**

1. Duplicati — [https://duplicati.com/](https://duplicati.com/)
2. Crear arxius Windows — [https://waytoit.wordpress.com/2015/03/15/creando-archivos-con-fsutil/](https://waytoit.wordpress.com/2015/03/15/creando-archivos-con-fsutil/)
3. Arxius de prova Linux — [https://waytoit.wordpress.com/2015/03/21/creando-archivos-de-prueba-en-linux/](https://waytoit.wordpress.com/2015/03/21/creando-archivos-de-prueba-en-linux/)
4. Manual duplicity — [http://manpages.ubuntu.com/manpages/trusty/man1/duplicity.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/duplicity.1.html)
5. Cron — [https://geekytheory.com/programar-tareas-en-linux-usando-crontab](https://geekytheory.com/programar-tareas-en-linux-usando-crontab)

---
