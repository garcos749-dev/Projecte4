# **T03: Pla de recuperació davant desastres — Versió estil “punt 8”**

## **1. Introducció al cas**

1. Recorda el cas del portàtil inaccesible: la teva actuació va impressionar el client.
2. Ara el client et demana participar en l'elaboració del **Pla de Contingència i Continuïtat del Negoci**.
3. Dins d’aquest pla s’ha d’implementar el **Pla de Recuperació davant Desastres (DRP)**.
4. L’objectiu és garantir la restauració ràpida de dades, hardware i software crítics després d’un desastre.
5. Un aspecte clau és garantir que els treballadors puguin recuperar els seus equips amb rapidesa en cas de robatori o avaria.
6. Per aquest motiu, cal crear **imatges de restauració del sistema** que permetin posar en marxa un equip en minuts.
7. Tots els equips del client utilitzen **Zorin OS 18** amb aplicacions prèviament configurades.

---

# **Fase 1: Anàlisi i justificació de la solució tècnica**

## **2. Objectiu de la fase**

1. Investigar eines que permetin **crear imatges de disc complertes** restaurables posteriorment.
2. Seleccionar **2 eines comercials** i **2 eines de comunitat** per fer una comparativa.
3. La comparativa ha d’incloure:

   * Característiques destacades
   * Preu
   * Diferències rellevants
4. Ha de ser una **comparativa real**, no una còpia de webs.
5. Finalment, proposa quina solució recomanes i justifica-ho segons: cost, facilitat d’ús, compatibilitat, escalabilitat, suport, etc.

---

# **Fase 2: Guia d’ús tècnica (Manual Operatiu)**

## **3. Preparació**

1. S’utilitza una màquina proporcionada pel client (simulada amb una OVA).
2. Cal realitzar dues accions:

   * Crear una **imatge completa del sistema**.
   * Restaurar-la en una màquina virtual **idèntica**, però **sense SO instal·lat**.
3. La guia tècnica ha de permetre al personal de manteniment reproduir els processos sense dubtes.
4. La documentació ha d’incloure **imatges i captures significatives**.
5. Com que és una prova de concepte i encara no hi ha eina aprovada, s’utilitzarà **Rescuezilla**.

---

# **4. Procediment pràctic amb Rescuezilla**

## **4.1. Crear una imatge completa del sistema**

1. Inicia la màquina en mode **Rescuezilla Live**.
2. Selecciona l’opció *Backup*.
3. Tria el disc origen (disc del sistema Zorin OS 18).
4. Selecciona la destinació on es desarà la imatge (disc extern, NAS, ISO, etc.).
5. Configura:

   * Nom de la imatge
   * Compressió
   * Divisió d’arxius (si cal)
6. Executa la còpia i espera que finalitzi.
7. Comprova que la imatge s’ha creat correctament.

## **4.2. Restaurar la imatge en un equip buit**

1. Crea una màquina virtual idèntica a l’original:

   * Mateixa RAM
   * Mateix número de CPUs
   * Mateixa configuració de xarxa
   * Mateixa mida de disc
2. Inicia la màquina amb **Rescuezilla Live**.
3. Selecciona *Restore*.
4. Tria la imatge prèviament creada.
5. Selecciona el disc destí (ha d’estar buit).
6. Executa la restauració i espera que finalitzi.
7. Reinicia i comprova que el sistema restaurat és funcional i idèntic a l’original.

---

# **5. Resultat de la guia**

1. El personal de manteniment ha de saber:

   * Crear imatges de disc dels equips Zorin OS 18
   * Restaurar-les ràpidament en equips nous o avariats
2. El procés garanteix:

   * Reducció del temps de recuperació (RTO)
   * Continuïtat del negoci en cas de desastre
   * Estalvi de temps i reducció d’errors manuals
3. La simplicitat de Rescuezilla facilita el desplegament en entorns no especialitzats.

---

# **6. Materials i links de suport**

1. INCIBE — *¿Ya tienes tu Plan de Recuperación ante Desastres?*
   [https://www.incibe.es/empresas/blog/tienes-tu-plan-recuperacion-desastres](https://www.incibe.es/empresas/blog/tienes-tu-plan-recuperacion-desastres)
2. Pàgina oficial de Rescuezilla (documentació i descàrrega).

---
