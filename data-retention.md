# Data Retention

Il principio di limitazione della conservazione del GDPR richiede che i dati personali non vengano mantenuti più del necessario per gli scopi specificati.

## Strategia Consigliata (Cron Job)
- Dati Inattivi: Contatti o Clienti che non hanno eseguito alcuna attività (es. `updatedAt`) per oltre 2, 5 o 10 anni (a seconda dello scopo, ad es. fini fiscali 10 anni).
- Job Cron: Esecuzione notturna che lancia uno script (o via API/CLI) che esegue `deleteMany` o `updateMany` (se si preferisce l'anonimizzazione sostituendo i campi con hash) su record più vecchi di una determinata data.
