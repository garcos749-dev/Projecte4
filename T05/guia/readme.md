# Guia d’instal·lació i configuració SSH (Ubuntu ↔ Windows)
---

## **Instal·lar el servei SSH a Ubuntu**

Instal·lem l’SSH des d’Ubuntu:
![imatge](../img/foto1.png)

```bash
sudo apt install openssh-server
```

Activem el servei SSH:
![imatge](../img/foto3.png)

```bash
sudo systemctl enable ssh
sudo systemctl start ssh
```

Comprovem que el servei està actiu:

```bash
systemctl status ssh
```

---

## **Primera connexió SSH i validació del certificat**

Fem:
![imatge](../img/foto2.png)


per veure la IP de l’adaptador **només amfitrió** a Ubuntu.

Des de Windows (PowerShell/Terminal):


```bash
ssh nom_ubuntu@IP_ubuntu
```
![imatge](../img/foto4.png)

Apareixerà un avís demanant acceptar la clau del servidor (`yes`) i després la contrasenya.

---

## **Habilitar l’usuari root a Ubuntu**

Assignem contrasenya a `root`:

```bash
sudo passwd root
```
![imatge](../img/foto5.png)

Introdueix la contrasenya actual i després la nova (exemple: `usuari`).

---

## **Configurar sshd_config per permetre només certs usuaris**

A Ubuntu obrim:

```bash
sudo nano /etc/ssh/sshd_config
```
![imatge](../img/foto6.png)

Afegim:

```
AllowUsers nom_usuari
```
![imatge](../img/foto7.png)

Reiniciem el servei SSH:

```bash
sudo systemctl restart ssh
```

---

## **Comprovació: root pot iniciar sessió local però no remotament**

Login local a Ubuntu:

```bash
su -
```
![imatge](../img/foto8.png)

Des de Windows:

```bash
ssh root@IP_ubuntu
```
![imatge](../img/foto9.png)

Resposta esperada: **Access denied**

---

## **Configurar SSH amb certificat en lloc de contrasenya**

### 1. Generar claus RSA des de Windows

```bash
ssh-keygen -t rsa -b 4096
```
![imatge](../img/foto10.png)

Apareixen dos fitxers, per exemple:

* `id_rsa`
* `id_rsa.pub`  ← **aquest és el que hem de copiar a Ubuntu**

![imatge](../img/foto11.png)

### 2. Copiar la clau pública a Ubuntu

```bash
scp id_rsa.pub nom_ubuntu@IP_ubuntu:/home/nom_ubuntu/
```
![imatge](../img/foto12.png)

### 3. Afegir la clau al fitxer authorized_keys

A Ubuntu:

```bash
touch ~/.ssh/authorized_keys
cat ~/id_rsa.pub >> ~/.ssh/authorized_keys

```
![imatge](../img/foto13.png)

Ara, des de Windows:

```bash
ssh nom_ubuntu@IP_ubuntu
```
![imatge](../img/foto14.png)

Ja no hauria de demanar contrasenya.

---

## **Configurar el servidor OpenSSH a Windows 11**

1. Obrir **Configuració** → **Sistema**

   ![imatge](../img/foto15.png)


2. Entrar a **Característiques opcionals**

    ![imatge](../img/foto16.png)


3. Clicar **Veure característiques disponibles**

    ![imatge](../img/foto17.png)


4. Buscar **OpenSSH Server**

    ![imatge](../img/foto18.png)


5. Marcar-lo i fer *Afegir*

---

## **Activar el servei OpenSSH a Windows**

A PowerShell (com administrador):

![imatge](../img/foto20.png)

powershell
Set-Service -Name sshd -StartupType Automatic
Start-Service sshd

![imatge](../img/foto24.png)

![imatge](../img/foto25.png)



Desactivar firewall (per a la pràctica):

```
Firewall i protecció de xarxa → Xarxa pública → Desactivar
```
![imatge](../img/foto21.png)

![imatge](../img/foto22.png)


Veure IP Windows “només amfitrió”:

```powershell
ipconfig
```
![imatge](../img/foto26.png)

---

## **Connexió remota des d’Ubuntu cap a Windows**

### 1. Comprovar ping

```bash
ping IP_windows
```
![imatge](../img/foto27.png)

### 2. Connexió SSH

```bash
ssh nom_windows@IP_windows
```
![imatge](../img/foto28.png)

---

## **Crear un túnel com el de la guia**


![imatge](../img/foto29.png)

---

## **Configuració del túnel *proxy* a Windows**

(Configura’l segons els paràmetres del túnel creat.)

---
