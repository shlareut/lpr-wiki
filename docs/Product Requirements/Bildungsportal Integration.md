# Bildungsportal Integration 
**Plugin zur Organisation und Durchführung digitaler Prüfungen über das Bildungsportal (BiP)**

---

# Beschreibung  
Dieses Plugin dient der Planung, Organisation und Durchführung digitaler Prüfungen innerhalb einer modernen digitalen Prüfungsumgebung. Kernfunktionen sind das Anlegen von Prüfungen über das Bildungsportal, die Konfiguration durch Lehrende sowie die Bereitstellung der relevanten Informationen und Berechtigungen für Prüflinge und Prüfer:innen. Prüfungserstellungen und -konfigurationen erfolgen zentralisiert, die Durchführung und Dokumentation ist in die bestehende IT-Umgebung (insb. Moodle und BiP) eingebettet.

---

# Technische Details

## Prüfungsclient  
- Referenz: https://github.com/BiP-org/next-exam

## User-Interface – Prüfung anlegen  
**1. Modusauswahl**
- Bestehender Moodle-Kurs (Quellen: eduvidual, TIBS)
- Vorlage aus eduthek (Klonen von Kursen oder spezifischen Tests)
- Zentrale Prüfungen (z.B. sRDP, Diagnosechecks)
- Digitale Umgebung und Tools:
    - Sprache
    - Mathematik (Geogebra)
    - Microsoft 365 Umgebung
    - Google Umgebung
    - Link
    - RDP (Remote Desktop, durch Schule bereitgestellt)
    
**2. Zeit/Prüflinge/Sitzplan**
- Start- und geplante Endzeit bzw. Dauer
- Raumauswahl
- Auswahl der prüfungsteilnehmenden Schüler:innen
- Option: Sitzplan

**3. Prüfer:innen**
- Zuweisung weiterer Prüfer:innen zur Prüfung

**4. Regeln**
- Aktivierung/Deaktivierung von:
    - Rechtschreibkorrektur
    - Künstlicher Intelligenz
    - Weiteren Prüfungsregeln (offen für Ergänzungen)

**5. Sicherheit**
- Authentifizierungsoptionen:
    - 1FA (Ein-Faktor)
    - 2FA (ID-Austria)
    - 3FA (ID-Austria + PIN)
    - Fotoaufnahme (auf dem Prüfungs-PC als Verifikation der Person vor Ort)

## Kalender-Integration / Kursstruktur  
- Anstehende Prüfungen erscheinen im Moodle-Kalender.
- Prüfungen werden als Moodle-Kurse angelegt; im Kurs liegt die Einzelaktivität mod_dpu.
- Spätere Möglichkeit: Anlage von Prüfaktivitäten direkt in bestehenden Klassenkursen (z.B. über local_classregister).
- Prüfungszuordnung via Moodle-Gruppen: Prüflinge werden über Gruppenzugehörigkeit abgebildet und verwaltet.

## Application-Interface (API)
- Schnittstelle zur Authentifizierung registrierter Nutzer über Moodle-Login-Token.
- Endpunkte zum:
    - Abruf aller anstehenden Prüfungen & deren Konfiguration für die eingeloggte Person.
    - Protokollieren von Prüfungsstart und Prüfungsende (Ende wird vom Prüfungsclient der Lehrperson bestimmt).
- Spezifikation:  
    - https://github.com/BiP-org/next-exam/blob/main/teacher/bip-demo-api/api.js

## Related Tickets  
- Projektboard & Issues:  
    - https://github.com/orgs/BiP-org/projects/18/views/1?filterQuery=dpu&pane=issue&itemId=98220623&issue=BiP-org%7Cnext-exam%7C77

---

# Sonstige Informationen

## Feature-Phasen

**Phase 1: Lehrer-Version**
- Lehrpersonen planen Prüfungen und stellen diese ein.

**Phase 2: Schüler-Version**
- Schüler erhalten eine Übersicht über ihre anstehenden Prüfungen (Beispiel: "Matheklausur am XX.XX.XXXX").

## Beispiel-Feature-Beschreibung  
1. Lehrkraft meldet sich am Bildungsportal mit ID-Austria-Authentifizierung an.
2. Nach Login auf dem BiP-Dashboard mit "Prüfung planen"-Button.
3. Nach Button-Klick erscheint die Eingabemaske (Fach, Art, Datum, etc. → genaue Felder noch zu spezifizieren).
4. Ziel: Lehrkräfte können Prüfungen im Voraus planen und konfigurieren sowie erforderliche Materialien hochladen. Sämtliche Konfigurationsoptionen im Vorfeld auswählbar (z.B. Exam Type, Zeitlimit, Materialien).
5. In der Prüfungssituation selbst ist keine zusätzliche Konfiguration mehr nötig: Prüfung kann aus einer Liste ausgewählt und sofort gestartet werden.

**Schüler:innen melden sich ebenfalls über das Bildungsportal per ID-Austria an.**

## Screenshots

Persönliches Dashboard:
<img width="1711" height="1241" alt="Screenshot_20250811_155049" src="https://github.com/user-attachments/assets/764117b6-dc19-474f-ac7d-84dde290d858" />

Schulspezifisches Dashboard:
<img width="1681" height="739" alt="Screenshot_20250811_155733" src="https://github.com/user-attachments/assets/e7ad57a0-93d7-48b5-b637-fbc059ad002d" />

# Offene Fragen

## 1. Authentifizierung & Benutzerverwaltung

- **Fallback/Prozess bei Ausfall der ID-Austria-Authentifizierung**
    - Wie soll vorgegangen werden, wenn Schüler:innen keinen Zugriff mehr auf ihre ID-Austria haben? (Backup-Verfahren, Prüfungsverschiebung, vor-Ort-Validierung etc.)
- **Übernahme von Nutzungsrechten/Rollen**
    - Soll das Plugin Nutzungsrechte/Rollen aus dem Bildungsportal übernehmen (z. B. nur Lehrkräfte dürfen Prüfungen planen)?

## 2. Datenschutz & personenbezogene Daten

- **Umgang mit personenbezogenen Daten aus ID-Austria**
    - Werden personenbezogene Daten gespeichert?
        - Falls ja: Wo, wie lange, durch wen abrufbar und wann erfolgt die Löschung?
        - Falls nein: Wie läuft die temporäre Nutzung (Session-basiert)?

## 3. Prüfungs­planung & Teilnehmer­verwaltung

- **Prüfungsberechtigung/Validierung**
    - Wie wird technisch/organisatorisch sichergestellt, dass nur für die jeweilige Prüfung vorgesehene Schüler:innen teilnehmen können?
    - Können individuelle Prüfungen für einzelne Schüler:innen geplant und verwaltet werden?
- **Teilnehmerauswahl**
    - Wie werden die Prüflinge einer Prüfung im Plugin ausgewählt – manuell aus einer Liste der Schule oder über einen automatischen Import (z. B. aus dem Schülerverzeichnis des BiP)?
- **Serien-/Sammelprüfungen**
    - Sollen nur Einzelprüfungen oder auch Serien-/Sammelprüfungen (z. B. gleiche Prüfung für mehrere Klassen oder parallele Termine in unterschiedlichen Räumen) geplant werden können?
- **Import aus Moodle-Kurs**
    - Wenn ein Moodle-Kurs als Quelle gewählt wird – sollen dann auch Teilnehmerlisten automatisch importiert werden?
    - [Beantwortet: Ja, Teilnehmerlisten werden übernommen.]
    - Sollen Gruppen aus Moodle mit importiert werden, oder werden alle Teilnehmenden in einer Liste übernommen?
    - [Beantwortet: Nein, alle Teilnehmenden werden in einer Liste übernommen.]

## 4. Prüfungs­vorlagen und Verwaltung

- **Prüfungsvorlagen**
    - Sollen auch Prüfungsvorlagen im Plugin gespeichert werden können, um wiederkehrende Einstellungen schnell zu übernehmen?
- **Prüfungsübersicht**
    - Soll das Plugin eine Übersicht aller geplanten Prüfungen einer Lehrkraft bereitstellen (inkl. Filter-/Suchfunktion)?
- **Prüfungsbearbeitung**
    - Sollen geplante Prüfungen bearbeitet oder storniert werden können, und falls ja, bis zu welchem Zeitpunkt vor Prüfungsbeginn?
- **Prüfungshistorie**
    - Soll es für Lehrkräfte eine Prüfungshistorie geben, um vergangene Prüfungen einzusehen und ggf. zu kopieren?

## 5. Prüfungsteam & Zusatzberechtigungen

- **Zusätzliche Prüfer:innen**
    - Wie sollen zusätzliche Prüfer:innen ausgewählt werden – aus einer vordefinierten Lehrerliste der Schule oder per freier Suche im gesamten BiP-Lehrendenverzeichnis?

## 6. Feedback, Benachrichtigung & Kommunikation

- **Feedback an Schüler:innen über BiP**
    - Sollen Schüler:innen im BiP Feedback, Benachrichtigungen oder Noten zur Prüfung erhalten?
- **Benachrichtigungsfunktion**
    - Soll es eine Benachrichtigungsfunktion geben (z. B. E-Mail oder BiP-Notification) für Lehrkräfte und Prüflinge bei neuen oder geänderten Prüfungen?

## 7. Technische Schnittstellen & APIs

- **API-Nutzung durch Drittsysteme**
    - Soll die API später auch von Drittsystemen (z. B. Schulverwaltung) aufgerufen werden können, um Prüfungen automatisiert anzulegen?

## 8. Authentifizierungsoptionen je Prüfung

- **Einstellung pro Prüfung**
    - Sollen Authentifizierungsoptionen (1FA, 2FA, 3FA, Fotoaufnahme) fix pro Prüfung gesetzt werden oder können mehrere Optionen erlaubt sein?
    - [Teils beantwortet: ID-Austria ist verpflichtend – andere Methoden sind aktuell irrelevant.]

## 9. Internationalisierung & Nutzerfreundlichkeit

- **Mehrsprachigkeit**
    - Gibt es Anforderungen an Mehrsprachigkeit der Oberfläche (Deutsch/Englisch) oder nur in Deutsch?


----


- Bildungsportal-Plugin -> Pilot-Schulen sollen jeweils 2 Lehrer (inkl. Kontaktdaten) im Bildungsportal vermerken können, die zuständig für Next-Exam sind und die Schulung absolviert haben.
