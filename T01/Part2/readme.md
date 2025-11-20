# Fase 2: Treball per Parelles – Proposta Unificada de Còpies de Seguretat

## 1. Discussió i Consens
Comparant els dos treballs individuals, s’ha arribat a un acord sobre què és crític i com programar les còpies:

**Dades Crítiques**
  - **Bases de Dades (Comptabilitat i Clients, 20 GB):** Prioritat màxima, canvia constantment. RTO < 4 h, RPO < 4 h.
  - **Documents de Projectes (300 GB):** Prioritat alta, creixement moderat, necessiten protecció.
  - **Carpetes Personals dels Usuaris (100 GB):** Prioritat mitjana, ús diari.
**Equips Clients:** No cal còpia completa dels 10 ordinadors; només la carpeta Documents si hi guarden informació important temporalment. Millor fomentar que aquests arxius s’emmagatzemin al servidor.

---

## 2. Proposta de la Parella (Esquema 3-2-1)

| Element                | Proposta de la Parella                                                                 | Justificació                                                                                     |
|------------------------|---------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| **Dades Crítiques**     | Bases de Dades, Documents de Projectes, Carpetes Personals dels Usuaris               | Protecció de dades essencials per al funcionament diari i complir RPO/RTO                       |
| **Periodicitat (BD)**   | Incremental cada 4 h + còpia completa nocturna + còpia completa setmanal            | Permet RPO ≤ 4 h i restauració ràpida                                                          |
| **Tipus de Còpia (BD)** | Incremental (cada 4 h), Completa diària, Completa setmanal, Completa mensual         | Combinació de còpies ràpides i consolidació històrica                                           |
| **Mitjà 1 (Local)**     | NAS dins de l’empresa                                                                 | Restauració ràpida, còpies automàtiques, accessible immediatament                                |
| **Mitjà 2 (Extern)**    | Cloud (Backblaze B2, Azure, AWS S3)                                                   | Protecció fora de lloc, anti-ransomware, manteniment històric 1 mes                              |
| **Còpia més recent**    | Sempre al NAS                                                                         | RTO < 4 h, recuperació immediata, no depèn d’internet                                          |
| **Còpia fora de lloc**  | Cloud                                                                                 | Protecció davant robatori, incendi o desastre físic                                              |

---

### 3. Detall de Còpies Addicionals

**Documents de Projectes / Carpetes Personals**
  - Incremental diari
  - Completa setmanal
  - Completa mensual

**Equips Clients (carpeta Documents)**
  - Incremental diari
  - Completa setmanal (si cal)

---

### 4. Justificació del Model 3-2-1

**3 còpies:** Original al servidor + còpia al NAS + còpia al Cloud  
**2 mitjans diferents:** NAS (local) i Cloud (extern)  
**1 còpia fora de lloc:** Cloud off-site, accessible en cas de desastre

**Objectiu:** Garantir disponibilitat immediata per a dades crítiques i protecció davant qualsevol incident, complint els requisits RTO/RPO.
