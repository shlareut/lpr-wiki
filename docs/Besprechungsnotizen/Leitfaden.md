# Leitfaden

Effektive Meetings sind ein Schlüsselelement für eine erfolgreiche, transparente und zielgerichtete Zusammenarbeit im Projekt „Next-Exam“. Auf dieser Seite werden alle wiederkehrenden und einmaligen Meetings unseres Teams dokumentiert und zentral zugänglich gemacht.

**Zweck:**  
Dieses Kapitel dient als zentrale Anlaufstelle für Meeting-Protokolle, Agenden und wichtige Entscheidungen. Es schafft Transparenz über besprochene Themen, getroffene Beschlüsse und offene ToDos – sowohl für das Team selbst als auch für alle Stakeholder.

**Was findest du hier?**
- Übersicht und Leitfäden zu den wichtigsten Meeting-Formaten
- Detaillierte Protokolle vergangener Meetings
- Zentrale Aufgaben und Verantwortlichkeiten, die während der Meetings definiert wurden
- Referenzen zu relevanten Dokumenten, Tickets oder Entscheidungsvorlagen

**Hinweis:**  
Bitte nutze dieses Verzeichnis auch zur Vorbereitung auf kommende Meetings oder um offene Themen nachzuvollziehen. Für Fragen oder Anregungen zur Meetingdokumentation wende dich gerne an das Projektteam.

---

Dieses How-To beschreibt, wie du ein neues Meeting-Protokoll in der MkDocs-Dokumentation erstellst.  
Die Navigation und das Inhaltsverzeichnis werden von MkDocs automatisch aus der Seiten- und Ordnerstruktur erzeugt – es ist also keine manuelle Pflege eines Verzeichnisses nötig.

## 1. Neues Meeting-Protokoll anlegen

1. Lege im Repository im passenden Ordner (z. B. `/docs/Besprechungsnotizen/`) eine neue Markdown-Datei für das Protokoll an, z. B.:

       Besprechungsnotizen/2024-08-08 Sprint Review.md

   > **Tipp:** Verwende das Muster `YYYY-MM-DD Kurztitel.md`, so bleiben die Protokolle übersichtlich und leicht auffindbar.

2. Trage dein Protokoll in die Datei ein, zum Beispiel:

       # Sprint Review – 08.08.2024

       **Datum:** 08.08.2024  
       **Teilnehmer:** Max, Anna, Sara  
       **Moderation:** Daniel

       ## Agenda
       - Demo der neuen Features
       - Review der letzten Sprintziele
       - Feedback und ToDos

       ## Besprochene Themen
       - Feature X erfolgreich abgeschlossen
       - Feature Y braucht mehr Zeit (#123)
       - Verbesserung: Regelmäßige Retros einführen

       ## ToDos
       - [ ] Max: Feedback ausarbeiten
       - [ ] Anna: Dokumentation für Feature X ergänzen

       ## Nächste Schritte
       - Nächstes Meeting: 15.08.2024, 9:30 Uhr, Teams-Call

3. Speichere die Datei und führe ggf. einen Commit & Push ins Repository aus.

## 2. Strukturierung

- Du kannst Unterordner nutzen (z. B. nach Jahr oder Meeting-Art: `Besprechungsnotizen/2024/`), um die Übersicht zu bewahren.
- Die MkDocs-Navigation wird automatisch entsprechend der gewählten Struktur erstellt.
- Es ist keine manuelle Pflege eines Inhaltsverzeichnisses notwendig.

---

**Tipp:**  
Um die Auffindbarkeit zu verbessern, wähle sprechende Dateinamen und Überschriften für jedes Protokoll. Die Seiten erscheinen automatisch in der Navigation – ganz ohne weiteren Aufwand.

---

Wenn du Fragen zur Struktur oder Einrichtung hast, wende dich gerne an das Projektteam!
