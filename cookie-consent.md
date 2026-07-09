# Cookie Consent (Linee Guida)

In conformità alle direttive del Garante Privacy (2021) e all'ePrivacy Directive:

1. **Equipollenza Accept/Reject:** Il bottone "Rifiuta Tutti" (o la X in alto a destra) deve essere evidente e graficamente equivalente a "Accetta Tutti".
2. **Finestra di Silenzio:** Se l'utente rifiuta, il banner non deve ripresentarsi per almeno 6 mesi.
3. **Granularità:** Possibilità di scegliere (Analytics, Marketing, Profilazione). I cookie "Tecnici" sono esenti dal consenso ma vanno descritti.
4. **Logica di blocco:** I tag (es. GTM, Meta Pixel) non devono scattare finché il consenso non è esplicito.

## Esempio Tecnico (Frontend Vue/Nuxt)
\`\`\`vue
// Esempio logica blocco e preferenza (LocalStorage)
const acceptEssential = () => {
  localStorage.setItem('cookie_consent', 'essential');
  localStorage.setItem('cookie_consent_date', Date.now().toString());
}
// etc..
\`\`\`
