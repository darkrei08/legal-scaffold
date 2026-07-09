# GDPR & Privacy Compliance Checklist

Questa è la checklist master di compliance per progetti software, ispirata alle logiche di Calicchia Design Platform.

## Aree di Compliance

| Area | Cosa fa | Referenza |
|---|---|---|
| **Cookie consent** | Banner con Accept/Reject equipollenti (Garante 2021 §6), vendor disclosure granulare, finestra di silenzio 6 mesi sul rifiuto. | [cookie-consent.md](./cookie-consent.md) |
| **PII scrubber** | Hook shared client/server/edge: email, telefono, IBAN, CF, IP, Bearer token rimossi prima dell'invio ai log (Sentry/Bugsink) (art. 6(1)(f)). | [pii-scrubber.md](./pii-scrubber.md) |
| **Newsletter** | Double opt-in con timestamp + IP + user-agent come prova del consenso (art. 7 GDPR, Decisione Garante 330/2025). | _Da definire_ |
| **Data retention** | Anonimizzazione automatica di customers/leads post-X-anni dall'ultima attività (cron daily). | [data-retention.md](./data-retention.md) |
| **Portale clienti** | Gate di accettazione T&C + DPA prima del primo accesso, con scroll-to-bottom obbligatorio e audit trail IP/UA. Bypass per chi ha già preventivi accettati. | _Da definire_ |
| **WhatsApp/SMS** | Disclaimer GDPR auto-appeso al primo contatto outbound (gestione preferenze + opt-out "STOP" intercettato dal Webhook). | _Vedi WaForge repo_ |
| **Documenti legali** | Privacy Policy, Cookie Policy, T&C (18 sezioni con diritti consumatore + ODR EU), DPA standard art. 28 GDPR. | `legal-docs/` |
