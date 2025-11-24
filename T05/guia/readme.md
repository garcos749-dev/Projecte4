# 📌 Ubicació de totes les fotos

## **1. SSH a Linux (Ubuntu)**

### **Comprovar i activar el servei**

Després d’aquest bloc:

```bash
systemctl status ssh
systemctl start ssh    # només si estava aturat
```

👉 **Aquí va aquesta foto:**
`![imatge](img/foto1.png)` → (Aquesta és la foto de l’estat del servei SSH)

---

### **Obtenir la IP**

Després d’aquest bloc:

```bash
ip addr show
```

👉 **Aquí va aquesta foto:**
`![imatge](img/foto2.png)`
*(La foto que mostra la IP, la que en el document original era “img/1.png”)*

---

## **2. Connexió des de Windows a Linux per SSH**

Després de:

```bash
ssh usuari@192.168.56.101
```

👉 **Aquí van dues fotos:**

1. **Confirmació del fingerprint (yes)**
   `![imatge](img/foto3.png)` *(abans era img/3.png)*

2. **Entrada de la contrasenya**
   `![imatge](img/foto4.png)` *(abans era img/4.png)*

---

## **3. Editar la configuració de SSH**

Després de:

```bash
sudo nano /etc/ssh/sshd_config
```

👉 **Aquí va aquesta foto:**
`![imatge](img/foto6.png)`
*(La foto on es veu l’arxiu sshd_config editat per permetre root — abans img/6.png)*

### **Opcional: habilitar login root**

Després de:

```bash
passwd root
```

👉 **Aquí va aquesta foto:**
`![imatge](img/foto5.png)` *(abans img/5.png)*

---

## **4. Seguretat: deshabilitar root i limitar usuaris**

Després d’aquest segon cop que obres l’arxiu:

```bash
sudo nano /etc/ssh/sshd_config
```

👉 **Aquí va aquesta foto:**
`![imatge](img/foto8.png)`
*(Configuració que bloqueja root i usuari2 — abans img/8.png)*

### Crear usuari nou

Després de:

```bash
passwd usuari2
```

👉 **Aquí va aquesta foto:**
`![imatge](img/foto9.png)` *(abans img/9.png)*

### Provar que usuari2 NO pot fer SSH

Després de:

```bash
ssh usuari2@192.168.56.101
```

👉 **Aquí va aquesta foto:**
`![imatge](img/foto10.png)` *(abans img/10.png)*

### Provar que root tampoc pot fer SSH

Després de:

```bash
ssh root@192.168.56.101
```

👉 **Aquí va aquesta foto:**
`![imatge](img/foto11.png)` *(abans img/11.png)*

### Però root sí pot iniciar sessió local

Després de:

```bash
login root
```

👉 **Aquesta foto:**
`![imatge](img/foto12.png)` *(abans img/12.png)*

### Provar SSH amb l’usuari permès

👉 **Aquesta foto va just després:**
`![imatge](img/foto13.png)` *(abans img/13.png)*

---

## **5. Accedir per certificat**

### Generar la clau amb ssh-keygen

Després de:

```bash
ssh-keygen -t rsa
```

👉 **Aquí va aquesta foto:**
`![imatge](img/foto14.png)` *(abans img/14.png)*

### Veure el directori `.ssh`

Després de:

```powershell
ls C:\Users\cfgm2smxb19\.ssh
```

👉 **Aquí va aquesta foto:**
`![imatge](img/foto15.png)` *(abans img/15.png)*

### Copiar la clau pública al servidor

Després de:

```powershell
scp C:\Users\cfgm2smxb19\.ssh\id_rsa.pub usuari@192.168.56.101:
```

👉 **Aquí va aquesta foto:**
`![imatge](img/foto16.png)` *(abans img/16.png)*

---

