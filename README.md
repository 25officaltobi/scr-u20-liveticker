# SC Riessersee U20 Liveticker

Einfache Fanansicht und Admin-Oberfläche für einen Eishockey-Liveticker.

## Enthaltene Funktionen
- Live-Spielstand für Heim- und Auswärtsteam
- Teamnamen und Logo-URLs
- Manuelle Spielzeiteingabe und Drittelauswahl
- Drittelbeginn und Drittelende
- Tore mit Torschütze und Assists
- Strafen mit Dauer und Grund
- Allgemeine Meldungen
- Echtzeit-Aktualisierung über Firebase Realtime Database
- Admin-Anmeldung mit Firebase Authentication

## Noch erforderliche Einrichtung
Die Website-Datei ist vorbereitet, aber die Live-Funktionen werden erst aktiv, wenn ein Firebase-Projekt eingerichtet und dessen Werte in `index.html` eingetragen sind.

1. Firebase-Projekt unter https://console.firebase.google.com/ anlegen.
2. Realtime Database erstellen und Authentication mit E-Mail/Passwort aktivieren.
3. Admin-Benutzer in Firebase Authentication anlegen.
4. Die Firebase-Web-App-Konfiguration in `firebaseConfig` in `index.html` einsetzen.
5. Die UID des Admin-Benutzers in `ADMIN_UID` einsetzen.
6. Realtime Database Rules auf folgende Regel setzen und die UID ersetzen:

```json
{
  "rules": {
    "ticker": {
      ".read": true,
      ".write": "auth != null && auth.uid === 'HIER_ADMIN_UID'"
    }
  }
}
```

Die Fanansicht ist öffentlich lesbar. Schreibzugriff auf den Ticker ist ausschließlich für die angegebene Admin-UID erlaubt.

## Veröffentlichung
GitHub Pages für dieses Repository aktivieren: Settings → Pages → Deploy from a branch → main → /(root).

Die Seite ist ein Start-Prototyp. Vor einem offiziellen Spiel auf mehreren Geräten testen. Push-Mitteilungen, Korrektur/Löschen von Events und eine Spiel-Reset-Funktion sind noch nicht enthalten.
