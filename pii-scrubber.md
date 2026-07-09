# PII Scrubber

Prima di inviare log a servizi di terze parti (come Sentry, Datadog o Bugsink), è fondamentale ripulire i log dai Personally Identificable Information (PII) per evitare la diffusione non voluta di dati personali (Data Breach).

## Logica (Nitro Plugin o Hook Sentry)
Intercetta la stringa/log in uscita e applica delle RegEx per mascherare i dati:

\`\`\`typescript
export const scrubPii = (text: string) => {
  let safeText = text
  
  // Mask Emails
  safeText = safeText.replace(/([a-zA-Z0-9._-]+@[a-zA-Z0-9._-]+\.[a-zA-Z0-9_-]+)/gi, '[EMAIL_REDACTED]')
  
  // Mask Phones (+39 o generico EU/US)
  safeText = safeText.replace(/(\+?\d{1,3}[\s-]?\d{3}[\s-]?\d{3,4}[\s-]?\d{3,4})/g, '[PHONE_REDACTED]')
  
  // Mask IP (v4)
  safeText = safeText.replace(/\b(?:\d{1,3}\.){3}\d{1,3}\b/g, '[IP_REDACTED]')
  
  // Mask IBAN
  safeText = safeText.replace(/\b[A-Z]{2}\d{2}[A-Z0-9]{11,30}\b/gi, '[IBAN_REDACTED]')
  
  // Mask Bearer Tokens
  safeText = safeText.replace(/Bearer\s+[A-Za-z0-9\-\._~+\/]+=*/gi, 'Bearer [TOKEN_REDACTED]')

  return safeText
}
\`\`\`
