# Fase 3: Treball en Grup – Proposta Final Unificada de Còpies de Seguretat

A partir de les aportacions del Grup 1 i el Grup 2, s’ha creat un esquema final unificat de còpies de seguretat basat en els requisits del cas pràctic i el model 3-2-1.

**Grup 1: Oscar Fernandez i Javier Garcia.
Grup 2: Biel batalla e Ivan sicra.**

---

## 1. Comparació de les Propostes

### Coincidències entre els dos grups
Dades crítiques identificades igual:
  - Bases de Dades Comptabilitat/Clients (20 GB)
  - Documents de Projectes (300 GB)
  - Carpetes Personals (100 GB)
Prioritzen còpies incrementals freqüents per complir el RPO de 4 h.
Proposen NAS com a mitjà local i Cloud com a còpia externa.
Apliquen el model 3-2-1.

### Diferències principals
Grup 1 aporta més detall: incremental cada 4 h + completes diàries, setmanals i mensuals.
Grup 2 proposa incremental + completa diària però sense aprofundir en retenció.
Grup 1 inclou més detalls sobre Documents i Carpetes Personals.

**Conclusió:** les dues propostes són compatibles; la del Grup 1 és més completa, però es fa una síntesi equilibrada.

---

## 2. Proposta Final Unificada (Esquema 3-2-1)

| Element | Proposta Final del Grup | Justificació |
|--------|---------------------------|--------------|
| **Dades Crítiques** | BD Comptabilitat/Clients (20 GB), Documents de Projectes (300 GB), Carpetes Personals (100 GB) | Dades essencials per al funcionament de l’empresa; BD amb RPO i RTO estrictes. |
| **Periodicitat BD** | Incremental cada 4 hores + completa nocturna + completa setmanal | Compliment del RPO de 4 h i manteniment d’històric. |
| **Tipus Còpia BD** | Incremental 4 h + Completa diària + Completa setmanal + Completa mensual | Velocitat i retenció equilibrades. |
| **Documents Projectes** | Incremental diària + Completa setmanal + Completa mensual | Protecció de dades importants de creixement moderat. |
| **Carpetes Personals** | Incremental diària + Completa setmanal | Ús diari, però risc moderat. |
| **Equips Clients** | Només còpia de la carpeta Documents si s’utilitza per treball crític | Es recomana treballar directament al servidor. |
| **Mitjà Local** | NAS dins de l’empresa | Restauració ràpida i compliment del RTO < 4 h. |
| **Mitjà Extern** | Cloud (AWS, Azure, Backblaze B2) | Protecció davant robatori, incendi, ransomware o desastres. |
| **Còpia més recent** | Emmagatzemada al NAS | Recuperació immediata. |
| **Còpia fora de lloc** | Cloud | Seguretat i redundància off-site. |

---

## 3. Model 3-2-1 Final

**3 Còpies:** servidor + NAS local + Cloud
**2 Mitjans:** NAS i Cloud
**1 Còpia fora de lloc:** Cloud (100% off-site)

Compliment assegurat:
**RTO < 4 h**
**RPO < 4 h**
Històric garantit: diari, setmanal i mensual

---

## 4. Conclusions del Grup

La proposta final garanteix:
Alta disponibilitat i recuperació ràpida en cas d’incident
Protecció completa davant fallades, errors humans o atacs ransomware
Compliment estricte dels requisits del cas pràctic
Un equilibri entre eficiència, cost i seguretat

Aquesta solució combina el millor de les aportacions dels dos subgrups i és adequada per a una empresa com Muntatges i Serveis Tècnics SL.
