# **Guia d’instal·lació SSH per Linux i Windows**

## **1. SSH a Linux (Ubuntu)**

### **Actualitzar sistema**

```bash
sudo apt update && sudo apt upgrade -y
```

### **Instal·lar SSH (si no està instal·lat)**

```bash
sudo apt install ssh
```

### **Comprovar i activar el servei**

```bash
systemctl status ssh
systemctl start ssh    # només si estava aturat
```

### **Obtenir la IP**

```bash
ip addr show
```

---

## **2. Connexió des de Windows a Linux per SSH**

A Windows, obre PowerShell i escriu:

```bash
ssh usuari@192.168.56.101
```

Accepta la connexió escrivint **yes** i introdueix la contrasenya.

---

## **3. Editar la configuració de SSH**

Obre el fitxer:

```bash
sudo nano /etc/ssh/sshd_config
```

### **Opcional: habilitar login del root**

(Per fer proves)

```bash
passwd root
systemctl restart ssh
ssh root@192.168.56.101
```

---

## **4. Seguretat: deshabilitar root per SSH i limitar usuaris**

Torna a editar:

```bash
sudo nano /etc/ssh/sshd_config
```

Configura perquè **root NO pugui fer SSH** i **només un usuari concret hi tingui accés**.

### Crear usuari nou (per proves)

```bash
useradd -m -s /bin/bash usuari2
passwd usuari2
```

Comprova que **usuari2 no pot fer SSH** si així ho has configurat.

Comprova també que **root no pot fer SSH** però **sí pot iniciar sessió en local**:

```bash
login root
```

---

## **5. Accedir per certificat (clau pública) en lloc de contrasenya**

### Generar la clau des de Windows (PowerShell)

```bash
ssh-keygen -t rsa
```

Prem *Enter* fins acabar.

### Veure el directori de les claus

```bash
ls C:\Users\cfgm2smxb19\.ssh
```

### Copiar la clau pública al servidor Linux

```bash
scp C:\Users\cfgm2smxb19\.ssh\id_rsa.pub usuari@192.168.56.101:
```

A partir d’aquí continuaràs amb la configuració a Windows.

---


