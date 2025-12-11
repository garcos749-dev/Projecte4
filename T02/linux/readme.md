# Part 2 — Còpia de seguretat a Linux amb Duplicity + cron

**Objectiu:** configurar còpies completes i incrementals del directori */home* en un volum auxiliar muntat manualment a */media/backup*, mostrant-ho amb captures però **sense incloure comandos en el text**.

## Seqüència de la prova de concepte

### Preparació del dispositiu de backup (10 GB): detecció, formatació en XFS i creació del punt de muntatge.

Formatació XFS i creació del punt de muntatge

S’estableix el sistema de fitxers i s’habilita el directori on es muntarà la unitat externa.

Muntatge manual a */media/backup*.

Volum muntat correctament.

### Creació d’usuaris.

Es deixa el volum llest per rebre les còpies de seguretat.

### Instal·lació de Duplicity.

Instal·lació de duplicity

S’incorpora l’eina encarregada de gestionar les còpies en sistemes Linux.

### Preparació del material de prova: afegir nous usuaris i generar fitxers de 10 MB dins *home*.

Creació de fitxers de prova

Es generen comptes i dades per comprovar la funcionalitat del backup.

### Realitzar una còpia completa de */home* cap al dispositiu de backup.

Còpia completa de */home* i comprovació del contingut guardat

### Validació de la restauració: eliminació i recuperació de fitxers.

Esborrat de fitxers i restauració completa

Es reprodueix una situació de pèrdua de dades i es comprova que la recuperació funciona.

### Execució d’una còpia incremental després d’afegir un fitxer d’uns 4 MB.

Creació del fitxer nou, còpia incremental i revisió de versions

S’introdueix una modificació petita i es genera una còpia incremental per analitzar els canvis.

### Desmuntatge del volum de backup.

Desconnexió del dispositiu

El volum es desmunta per garantir la seva seguretat.

### Automatització mitjançant scripts i cron (amb captures del procés).

Creació dels scripts i assignació de permisos Permisos d’execució

S’obre el fitxer de *crontab* per programar les tasques que cron haurà d’executar.
Permisos d’execució i programació de la còpia incremental.

---

Si vols, també puc:
✅ simplificar-lo més
✅ traduir-lo
✅ adaptar-lo a un format d’informe formal
Només digues què prefereixes!
