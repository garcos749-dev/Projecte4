# T01: DRP – Còpies de Seguretat  
## Estudi Cas Client (Treball Cooperatiu)

---

## **Breu Descripció – Introducció**

La primera hora, el responsable de seguretat presenta el tema de les còpies de seguretat a partir d’un material didàctic.  
Després, els alumnes han de treballar els diferents aspectes del tema mitjançant una dinàmica cooperativa.

---

## **Presentació del Cas Client**

**"Muntatges i Serveis Tècnics SL"** és una petita empresa dedicada a la instal·lació i manteniment d’equips industrials.

### **Infraestructura Tècnica**

- **Servidor de Fitxers (Ubuntu Server)**  
  Conté tota la documentació crítica:
  - **Documents de Projectes:** Plànols, especificacions tècniques (300 GB, creixement moderat).
  - **Bases de Dades (Comptabilitat i Clients):** Crítiques i d'ús diari (20 GB, canvi constant).
  - **Carpetes Personals dels Usuaris:** Documents de feina diària (100 GB).

- **10 Equips Clients (Windows 10/11)**  
  Els usuaris treballen majoritàriament amb fitxers del servidor, però alguns tècnics guarden temporalment informes importants a la carpeta *Documents*.

- **Connexió a Internet:**  
  Fibra òptica de 600 Mbps (simètrica).

### **Requisits de Recuperació**

- **RTO (Temps de Recuperació):**  
  Les dades de Comptabilitat/Clients han d'estar disponibles en menys de 4 hores.

- **RPO (Pèrdua de Dades Admesa):**  
  Per a la majoria de dades es pot perdre fins a 24 h, però les dades de Comptabilitat/Clients no poden perdre més de 4 h.

- **Retenció:**  
  Cal guardar un historial mínim d’un mes.

---

# **Fase 1: Treball Individual**

Cada alumne ha de respondre les preguntes següents basant-se en el cas pràctic:

1. **Què copiar? (Priorització):**  
   Quines són les dades més crítiques del servidor?  
   Cal fer còpia dels 10 equips clients? Justifica-ho.

2. **Periodicitat i Tipus de Còpia:**  
   Proposa un calendari bàsic per a la setmana (diari, setmanal, mensual).  
   Indica quin tipus de còpia aplicaràs (Completa, Diferencial, Incremental) a les dades crítiques.

3. **Mitjans i Ubicació:**  
   Quin mitjà de còpia utilitzaries (discs durs externs, NAS, cloud, cintes)?  
   On s’ha de guardar físicament la còpia més recent (Regla 3-2-1)?

---

# **Fase 2: Treball per Parelles**

Treballant en parelles:

1. **Discussió i Consens:**  
   Comparen les respostes individuals de la Fase 1.

2. **Proposta Unificada:**  
   Elaboren un esquema propi 3-2-1 (3 còpies, 2 mitjans, 1 fora de lloc) adaptat als requisits del cas.

### **Taula de treball per emplenar**

| Element                  | Proposta de la Parella | Justificació |
|--------------------------|-------------------------|--------------|
| **Dades Crítiques**      |                         |              |
| **Periodicitat (BD)**    |                         |              |
| **Tipus de Còpia (BD)**  |                         |              |
| **Mitjà 1 (Local)**      |                         |              |
| **Mitjà 2 (Extern)**     |                         |              |

---

# **Fase 3: Treball en Grup**

1. **Debat i Selecció:**  
   Cada parella presenta el seu esquema.  
   El grup discuteix avantatges i inconvenients (cost, temps recuperació, seguretat, simplicitat).

2. **Política Final:**  
   El grup redacta la **Política de Còpies de Seguretat Definitiva** que presentaran a l’empresa.

---

# **Document Final (Fase 3)**

El document final del grup ha d’incloure:

---

## **1) Dades Objecte de Còpia**

- Quines dades es copien  
- Amb quina freqüència  
- Separant Servidor / Equips Clients  
- I dades crítiques / no crítiques

---

## **2) Cronograma Setmanal Detallat**

| Dia      | Dades (ex: BD) | Tipus de còpia | Mitjà |
|----------|----------------|----------------|--------|
| Dilluns  |                |                |        |
| Dimarts  |                |                |        |
| ...      |                |                |        |
| Diumenge |                |                |        |

---

## **3) Elecció de Mitjans i Ubicació (Regla 3-2-1)**

- **Mitjà 1 (Local):**  
  Ex: NAS, Disc dur USB…

- **Mitjà 2 (Extern):**  
  Ex: Cloud, Cintes LTO  
  Proveïdor suggerit: Azure, Google Cloud, AWS…

- **Ubicació Fora de Lloc:**  
  On es guarda la còpia externa i qui n’és responsable.

---

## **4) Estratègia de Recuperació (RTO/RPO)**

Com es garanteix que les dades de Comptabilitat/Clients compleixen:

- **RPO ≤ 4 hores**  
- **RTO ≤ 4 hores**

---

## **Materials i Links de Suport**

- Moodle 0226 Seguretat Informàtica – RA2.AA3 Còpies  
- INCIBE: *Copias de seguridad. Guía de aproximación para el empresario*  
- Vídeo Xataka – Backup 3-2-1  
  https://youtu.be/PM_M4Iz6I4o?si=F7DRyDDTZE3hjWn8
