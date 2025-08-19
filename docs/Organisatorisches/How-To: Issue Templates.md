# How-To: Issue Templates

Zur strukturierten Zusammenarbeit bei Next-Exam stehen maßgeschneiderte Issue Templates bereit. Mit diesen Vorlagen kannst du Feature-Wünsche, Anpassungen, Fehlerberichte, Action Points, Epics sowie technische Vorhaben klar und übersichtlich dokumentieren.

**Hinweis:**  
Leere Issues ohne Template sind nicht erlaubt (`blank_issues_enabled: false`). Bitte nutze immer das passende Template!

---

## Übersicht & Anwendungsfälle

| Template            | Einsatzgebiet                                         | Typische Beispiele                         |
|---------------------|------------------------------------------------------|--------------------------------------------|
| **User Story**      | Funktionale Anforderungen aus Anwendersicht           | Neue Prüfungsoption, Prozessvereinfachung  |
| **Technisches Feature** | Technische Neuerungen, Refactoring, Architektur         | Modul-Überarbeitung, Library-Upgrade       |
| **Anpassung**       | Änderungen vorhandener Features, Texte oder Workflows | UI-Text fix, Flow ändern, Design-Feinheiten|
| **Bug**             | Fehler und unerwartetes Verhalten melden              | Abstürze, Anzeigenfehler, falsches Ergebnis|
| **Action Point**    | Offene Fragen, Diskussionspunkte, Projekt-ToDos       | Abstimmungen, Entscheidungen klären        |
| **Epic**            | Große Themenbereiche & Sammel-Issues                  | Digitalisierung, umfangreiche Modernisierung|

---

## So erstellst du ein neues Issue

1. **Navigiere zur „Issues“-Sektion**  
   Klicke im Repository auf „Issues“ > „New Issue“.

2. **Wähle das passende Template**  
   Entscheide nach Inhalt & Anlass, welches der folgenden Templates du nutzen möchtest.

3. **Formular sorgfältig ausfüllen**  
   Jede Vorlage bietet Hilfetexte zur leichten Orientierung. Pflichtfelder sind mit *Stern* markiert.

4. **Issue absenden**  
   Fertig ausgefülltes Issue abschicken – fertig!

---

## Templates im Detail & Beispiele

### User Story
*Zur Beschreibung von Nutzerbedürfnissen und neuen Funktionen aus Anwendersicht.*

**Wichtige Felder:**
- **Beschreibung (Format: Als \<Rolle\> möchte ich \<Ziel\>, um \<Nutzen\>)**
- **Akzeptanzkriterien** (GIVEN-WHEN-THEN)
- **Link zu Designs** (optional)
- **Implementierungsdetails, Notizen** (optional)

**Beispiel:**
Als Lehrkraft möchte ich für jede digitale Prüfung einen Zeitrahmen angeben können,  
um eine faire Bewertung zu gewährleisten.

Akzeptanzkriterien:
- GIVEN eine neue Prüfung
- WHEN ich einen Prüfungszeitraum angebe
- THEN wird der Zeitraum angezeigt und die Prüfung nach Ablauf automatisch beendet

---

### Technisches Feature

*Für technische Aufgaben, Verbesserungen oder Architekturarbeiten.*

**Wichtige Felder:**
- **Beschreibung:** Was soll technisch geändert oder erweitert werden?
- **Akzeptanzkriterien:** Wann gilt die technische Aufgabe als abgeschlossen? (Im Format „GIVEN-WHEN-THEN“)
- **Implementierungsdetails:** (optional) Hinweise zur Umsetzung, Architektur, Schnittstellen, Libraries, etc.
- **Notizen, Risiken & Annahmen:** (optional) Potenzielle Risiken, technische Annahmen, Abhängigkeiten

**Beispiel:**
Beschreibung:  
Refactoring des Multiple-Choice-Moduls zur besseren Wartbarkeit.

Akzeptanzkriterien:
- GIVEN bestehende MC-Fragen
- WHEN ausgewertet
- THEN stimmen Ergebnisse und der Code erfüllt Clean Code-Prinzipien

Implementierungsdetails:
- Modularisierung der Auswertungslogik
- Unit-Tests aktualisieren

Notizen, Risiken & Annahmen:
- Risiko: Fehler bei Anpassung bestehender Funktionen
- Annahme: Alle bisherigen Auswertungsfälle sind durch Tests abgedeckt

---

### Anpassung
*Zur Aufnahme von UI-/Text-Änderungen und kleinen Ablaufoptimierungen.*

**Wichtige Felder:**
- **Beschreibung** (Was soll geändert werden?)
- **Grund** (Warum?)
- **Betroffene Bereiche** (optional)

**Beispiel:**
Beschreibung:  
Button in der Lehrermaske von "Prüfung starten" in "Exam starten" umbenennen.

Grund:
Klarere Terminologie für alle Lehrkräfte.

Betroffene Bereiche:
Lehrermaske, Hilfetexte, automatisierte UI-Tests.

---

### Bug
*Um Fehler, unerwartetes Verhalten und Probleme nachvollziehbar zu melden.*

**Wichtige Felder:**
- **Was ist passiert?** (Fehlerbeschreibung)
- **Schritte zur Reproduktion** (so detailliert wie möglich)
- **Erwartetes/aktuelles Verhalten** (optional)

**Beispiel:**
Was ist passiert?  
Beim Starten einer Prüfung wird die Teilnehmendenliste nicht geladen, sondern nur eine leere Seite angezeigt.

Schritte zur Reproduktion:
1. Login als Lehrkraft.
2. Gehe zu „Prüfungen“.
3. Klicke auf „Prüfung starten“ – Liste fehlt.

Erwartetes Verhalten:
Liste aller Teilnehmenden wird korrekt angezeigt.

---

### Action Point
*Um offene Punkte, Ideen und Entscheidungsbedarfe festzuhalten.*

**Wichtige Felder:**
- **Beschreibung des Action Points**
- **Ansprechpartner:innen/Beteiligte** (optional)
- **Referenzen/Links** (optional)

**Beispiel:**
Beschreibung:  
Entscheidung: Einführung eines anonymisierten Bewertungsmodus für alle Prüfungen.

Beteiligte:
@max @team-admin

Referenzen:
Spezi-Dokument, verwandtes Issue #42

---

### Epic
*Nutzt du für große Themengebiete, die mehrere Themen/Issues bündeln.*

**Wichtige Felder:**
- **Beschreibung (Umfang/Ziel)**
- **Link zu Designs/Konzepten** (optional)

**Beispiel:**
Beschreibung:  
Epic zur Digitalisierung der kompletten Prüfungsorganisation und -abwicklung bei Next-Exam.

---

## Gute Practices für alle Issues

- So präzise & konkret wie möglich ausfüllen  
- Relevante Anhänge, Bilder oder Design-Links hinzufügen  
- Betroffene Personen mit GitHub-Handle @-taggen, wenn nötig  
- Nutze die Akzeptanzkriterien zur Definition von „fertig“  
- Stelle Rückfragen innerhalb des Issues, falls Details fehlen

---

## Hinweis zur Konfiguration

Aktuell ist das Erstellen leerer Issues ohne Template deaktiviert (`blank_issues_enabled: false`).  
Bitte wähle immer einen der vorhandenen Typen für dein Anliegen aus!

---

**Herzlichen Dank für deinen Beitrag zur weiteren Optimierung von Next-Exam! 🚀**

---

*Fragen zu den Templates oder Wünsche für weitere Vorlagen? Melde dich gerne beim Dev-Team!*
