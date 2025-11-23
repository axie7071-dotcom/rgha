# SendGrid Email Setup

Diese Anleitung erklärt, wie Sie SendGrid für echte E-Mail-Benachrichtigungen einrichten.

## Schritt 1: .env.local Datei erstellen

Erstellen Sie eine Datei `.env.local` im Projekt-Root mit folgendem Inhalt:

```env
SENDGRID_API_KEY=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
SENDGRID_FROM_EMAIL=axie7071@gmail.com
SENDGRID_FROM_NAME=DolmetscherPro
```

## Schritt 2: SendGrid-Paket installieren

Öffnen Sie PowerShell **als Administrator** und führen Sie aus:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Dann im Projekt-Verzeichnis:

```bash
npm install @sendgrid/mail
```

## Schritt 3: Absender-E-Mail verifizieren

1. Gehen Sie zu: https://app.sendgrid.com/settings/sender_auth
2. Klicken Sie auf "Verify a Single Sender"
3. Geben Sie ein:
   - From Name: `DolmetscherPro`
   - From Email Address: `axie7071@gmail.com`
   - Reply To: `axie7071@gmail.com`
4. Bestätigen Sie die Verifizierungs-E-Mail

## Schritt 4: Dev-Server neu starten

```bash
npm run dev
```

## Testen

1. Öffnen Sie: http://localhost:3000/buchen
2. Buchen Sie einen Termin
3. Prüfen Sie Ihr E-Mail-Postfach (Admin + Kunde)

## Troubleshooting

### "PowerShell-Skript kann nicht geladen werden"
Führen Sie PowerShell als Administrator aus:
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### "SendGrid API-Key nicht gefunden"
- Prüfen Sie, ob `.env.local` im Projekt-Root existiert
- Starten Sie den Dev-Server neu

### "Unauthorized sender"
- Verifizieren Sie Ihre Absender-E-Mail in SendGrid
- Warten Sie einige Minuten nach der Verifizierung

### E-Mails landen im Spam
- Fügen Sie `axie7071@gmail.com` zu Ihren Kontakten hinzu
- Markieren Sie die E-Mail als "Kein Spam"

## Fallback-Modus

Wenn kein API-Key gefunden wird, nutzt die App automatisch den Mock-Service (Konsolen-Ausgabe).
