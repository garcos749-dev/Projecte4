# **T10: Servidor d’impressió Linux – CUPS (tasca individual)**

## **Versió estil “punt 8”**

## **1. Introducció**

1. La gestió d’impressores en una empresa sol ser caòtica:

   * Drivers incompatibles
   * Costos descontrolats de tòner
   * Usuaris que no saben quina impressora estan utilitzant
2. La solució professional és un **Servidor d’Impressió Centralitzat**.
3. DevOptimize Solutions utilitza:

   * Clients Linux (Zorin OS)
   * Servidors Ubuntu Server
4. El client vol validar que un servidor Linux pot gestionar una impressora i compartir-la de forma transparent.

---

# **2. La vostra missió: Prova de Concepte (PoC)**

1. S’ha de demostrar que un servidor Linux pot:

   * Gestionar una impressora (virtual)
   * Compartir-la amb clients Zorin
   * Rebre i processar feines d’impressió
2. Per evitar comprar hardware, s’utilitzarà la impressora virtual **cups-pdf**.
3. Aquesta impressora genera un **PDF al servidor** en lloc de paper.

---

# **3. Escenari de treball**

1. Es reutilitza l’escenari de la PoC de NFS.
2. **Màquina 1 (Servidor):**

   * Ubuntu Server
   * Interfície NAT
   * Interfície Host-Only
3. **Màquina 2 (Client):**

   * Zorin OS Desktop
   * Mateixa configuració de xarxa

---

# **4. Prova de concepte (PoC)**

## **4.1. Tasques obligatòries**

1. Instal·lar **CUPS** al servidor.
2. Instal·lar i configurar la impressora virtual **cups-pdf**.
3. Configurar CUPS perquè:

   * L’administració web estigui habilitada
   * El servei escolti per totes les interfícies
4. Accedir al frontal web de CUPS i **compartir la impressora**.
5. Al client Zorin, **afegir la impressora** del servidor.
6. Enviar diverses feines d’impressió.
7. Comprovar al servidor que s’han generat els **fitxers PDF corresponents**.

---

# **5. Documentació**

1. Cal documentar totes les comandes utilitzades:

   * Instal·lació
   * Configuració
   * Validació
2. Cal afegir **captures de pantalla** que demostrin:

   * Impressora configurada
   * Impressora compartida
   * Impressió des de Zorin
   * Fitxers PDF apareixent al servidor
3. La documentació ha de permetre repetir exactament la PoC.

---

# **6. Materials i links de suport**

1. UD5. AA1. CUPS (Moodle)
2. J.B. Alex Mantich (2024). *Instalación CUPS en Linux* (YouTube)
   [https://www.youtube.com/watch?v=FNwSTrOSgZQ](https://www.youtube.com/watch?v=FNwSTrOSgZQ)
3. Documentació oficial Ubuntu Server (NFS):
   [https://documentation.ubuntu.com/server/how-to/networking/install-nfs/](https://documentation.ubuntu.com/server/how-to/networking/install-nfs/)
4. idroot (2024). *How to Install CUPS Print Server on Ubuntu 24.04*
   [https://idroot.us/install-cups-print-server-ubuntu-24-04/](https://idroot.us/install-cups-print-server-ubuntu-24-04/)

---
