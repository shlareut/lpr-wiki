# Bildungsportal-Integration 

Die Integration mit dem Bildungsportal (BiP; https://www.bildung.gv.at/) soll die effiziente Planung und Organisation von Next-Exam-Prüfungen ermöglichen. Lehrkräfte authentifizieren sich im BiP mithilfe ihrer ID Austria und können über ein Next-Exam Plugin neue Prüfungen anlegen, relevante Parameter wie Datum und Prüfungsfach inkl. Prüfungsfachparameter konfigurieren und z. B. Materialien bereitstellen, die die Schüler:innen während der Prüfung nutzen können.

Grundsätzlich soll das Next-Exam Plugin alle Einstellungsmöglichkeiten im Rahmen der Prüfungsplanung bieten, die derzeit auch der Teacher-Client bietet.

## 1. Scope

- Phase 1 richtet sich ausschließlich an Lehrkräfte.
- Phase 2 erweitert die Funktionen um die Schüler:innen-Perspektive: Nach der Anmeldung mit ID Austria im BiP erhalten Schüler:innen eine übersichtliche Auflistung aller bevorstehenden Prüfungen sowie wichtiger Details wie Prüfungsfach und Prüfungstermin (z. B. Mathematik-Prüfung am 18.08.2025).
 
## 2. Grober Workflow

1. **Anmeldung:**  
   Die Lehrkraft authentifiziert sich im Bildungsportal (BiP) via ID Austria.

2. **Prüfungsplanung starten:**  
   Nach dem Login erscheint im BiP-Dashboard die Option „Prüfung planen“.

3. **Eingabemaske:**  
   Mit Klick auf „Prüfung planen“ öffnet sich eine Eingabemaske, in der die Lehrkraft alle relevanten Prüfungsdetails (z. B. Fach, Prüfungsart, Datum) einträgt.  
   *Die konkreten Felder werden noch spezifiziert.*

4. **Vorausplanung und Materialbereitstellung:**  
   Lehrkräfte können Prüfungen frühzeitig planen und benötigte Materialien hochladen.  
   Alle wesentlichen Optionen (Prüfungsart, Zeitlimit, Materialien etc.) sind direkt auswählbar.

   > **Hinweis:**  
   > Die Lehrkraft meldet sich in Next-Exam mit BiP-Zugangsdaten an.  
   > Next-Exam liest die vom BiP geplanten Prüfungen aus, die Lehrkraft kann aus der Liste auswählen.

5. **Prüfungsdurchführung:**  
   Zur Prüfungssituation wählt die Lehrkraft einfach die gewünschte Prüfung aus der Liste und startet diese. Eine zusätzliche Konfiguration ist nicht mehr erforderlich.

   > Nach dem Start meldet Next-Exam den Status (z. B. „Prüfung läuft“) sowie relevante Daten (Lehrer-IP, Lehrer-ID, Exam-Status, Exam-ID, Prüfungs-Pincode) zurück an das BiP.  
   > Ziel: Schüler:innen sehen in ihrem BiP-Portal die gestartete Prüfung und können sich unkompliziert per Prüfungs-Pincode einwählen und teilnehmen.

## 3. Anforderungen (Grob)

**1. Modusauswahl**

- Auswahl bestehender Moodle-Kurse (z. B. eduvidual, TIBS) als Prüfungsgrundlage
- Nutzung von Vorlagen aus eduthek (Klonen von Kursen oder spezifischen Tests)
- Zuweisung zentraler Prüfungen (z. B. sRDP, Diagnosechecks) möglich
- Unterstützung verschiedener digitaler Prüfungsumgebungen & Tools:
    - Auswahl der Umgebungssprache
    - Integration von Mathematik-Tools (z. B. GeoGebra)
    - Einbindung Microsoft 365
    - Einbindung Google Suite
    - Ergänzung von Links zu externen Ressourcen
    - Nutzung schulbereitgestellter Remote-Desktop (RDP)-Lösungen

**2. Zeit, Teilnehmer:innen, Sitzplan**

- Festlegung der Start- und Endzeit bzw. Gesamtdauer der Prüfung
- Auswahl des Prüfungsraums aus einer Liste
- Auswahl und Zuweisung der teilnehmenden Schüler:innen zur Prüfung
- Verwaltung eines Sitzplans (späteres Feature; ab Version 1 nicht erforderlich)

**3. Prüfer:innen**

- Zuweisung weiterer Prüfer:innen und Vergabe entsprechender Berechtigungen

**4. Prüfungsregeln**

- Aktivierung/Deaktivierung der Rechtschreibkorrektur
- Aktivierung/Deaktivierung von KI-Funktionen während der Prüfung
- Konfiguration individueller Prüfungsregeln

**5. Sicherheit**

- Auswahl der Authentifizierungsmethode pro Prüfung: 1FA, 2FA (ID Austria), 3FA (inkl. PIN)
- Optionale Fotoaufnahme zur Identitätsprüfung am Prüfungs-PC

**6. Kalenderintegration & Kursstruktur**

- Automatische Anzeige anstehender Prüfungen im Moodle-Kalender der Teilnehmenden
- Automatische Erstellung von Prüfungen als Moodle-Kurse mit Einzelaktivität (mod_dpu)
- Option, Prüfungsaktivitäten künftig direkt in bestehenden Klassenkursen (via local_classregister) anzulegen
- Verwaltung der Schulzugehörigkeit der Prüflinge via Moodle-Gruppen

**7. Application-Interface (API)**

- Authentifizierung registrierter Nutzer:innen via Moodle-Login-Token
- Endpunkte zum Abruf und zur Konfiguration relevanter Prüfungsinformationen für eingeloggte Nutzer:innen
- Endpunkte zur Protokollierung von Prüfungsstart und Prüfungsende (Ende wird durch Lehrkraft im Prüfungsclient definiert)
- → [API-Dokumentation](https://github.com/BiP-org/next-exam/blob/main/teacher/bip-demo-api/api.js)

**8. Bildungsportal**

- Pilot-Schulen müssen im BiP zwei zuständige, geschulte Lehrkräfte inkl. Kontaktdaten hinterlegen

---

## 4. Weitere Informationen

- **Bestehende Tickets/Grobanforderungen:**  
  [Grobanforderungen (veraltet, nicht für API-Spezifikation verwenden)](https://github.com/BiP-org/next-exam/blob/ProjectManagement/epics/BiPExamConfiguration.md)
- **Mock-API Spezifikationen:**  
  [Lehrer-BiP-Demo-API](https://github.com/BiP-org/next-exam/blob/main/teacher/bip-demo-api/api.js)

---

## 5. Offene Fragen & Antworten

- **Fallback ID Austria:**  
  Was tun bei fehlendem Zugang zu ID Austria bei Lehrer:in/Schüler:in (z. B. Backup-Verfahren, Prüfungsverschiebung)?
  > Schulen definieren einen Notfallplan.  
  > Lehrer können ad hoc Prüfungen anlegen.  
  > Schüler nehmen wie bisher mit einem vom Lehrer vergebenen PIN teil.

- **Übernahme von Rechten/Rollen:**  
  Soll das Plugin Rechte/Rollen aus dem BiP übernehmen?
  > Ja, das geschieht API-seitig über das Bildungsportal.

- **Speicherung personenbezogener Daten:**  
  Welche personenbezogenen Daten aus ID Austria werden wie verarbeitet?
  > Es wird nur Name und BiP-ID des Schülers temporär verarbeitet (DSGVO-konform). Speicherung relevant bei Upload von Schülerarbeiten ins BiP (zukünftig).

- **Teilnahmeberechtigung:**  
  Wie wird sichergestellt, dass nur berechtigte Schüler:innen teilnehmen?
  > Schüler sind Klassen zugeordnet (im BiP hinterlegt); Lehrer können Klasse(n) oder Einzelne auswählen (inkl. klassenübergreifende Gruppen wie Sprachgruppen).  
  > Daten stammen ggf. auch aus „Sokrates“.

- **Individuelle Prüfungszuordnung:**  
  Können Prüfungen für einzelne Schüler:innen geplant werden?
  > Ja, Auswahl nach Schüler-ID möglich, „Schulklasse“ dient als Filter.

- **Auswahl der Prüflinge:**  
  Wie werden Prüflinge im Plugin ausgewählt?
  > Lehrer filtert nach Klasse und wählt Schüler:innen manuell aus.

- **Serien-/Sammelprüfung:**  
  Sollen Prüfungsserien/Mehrfachtermine unterstützt werden?
  > Duplizieren von Prüfungen möglich.  
  > Nach Abschluss weiterhin Zugriff, Kopieren/Retrospektive möglich.  
  > Zukünftig: Verwendung von Ministeriumsvorlagen.

- **Import aus Moodle-Kurs:**  
  Werden bei Auswahl eines Moodle-Kurses als Quelle die Teilnehmer:innen übernommen?
  > Ja.

- **Gruppenimport aus Moodle:**  
  Werden Moodle-Gruppen als Gruppen übernommen?
  > Nein, alle Teilnehmenden werden als Liste übernommen.

- **Prüfungsvorlagen:**  
  Können Prüfungsvorlagen gespeichert werden?
  > Langfristig geplant (insb. für Templates des BMBWF), kurzfristig optional (bei geringem Mehraufwand).

- **Prüfungsübersicht:**  
  Soll eine Übersicht aller Prüfungen mit Filter-/Suchfunktion angeboten werden?
  > Ja, inkl. vergangener Prüfungen.

- **Prüfungsbearbeitung:**  
  Können geplante Prüfungen bearbeitet oder storniert werden?
  > Ja, solange „geplant“.  
  > Bearbeitung/Stornierung NICHT während der Prüfung.  
  > Löschung möglich, solange keine Ergebnisse ins BiP hochgeladen wurden.

- **Prüfungshistorie:**  
  Gibt es eine Historie geplanter/vergangener Prüfungen?
  > Ja.

- **Weitere Prüfer:innen:**  
  Auswahl und Berechtigungsvergabe an Zusatzprüfer:innen?
  > Nicht Phase 1.  
  > “Aufsichtsübergabe” später (z. B. für Matura).

- **Feedback an Schüler:innen:**  
  Sollen Rückmeldungen oder Noten im BiP rückgemeldet werden?
  > Zukünftig, nicht Phase 1.

- **Benachrichtigungsfunktion:**  
  E-Mail/BiP-Benachrichtigung für Lehrkräfte/Schüler:innen?
  > Nice-to-have.

- **API für Drittsysteme:**  
  Soll die API für Drittsysteme (z. B. Schulverwaltung) geöffnet werden?
  > Zukunft (z. B. automatisierte Planung von Zentralmatura).

- **Authentifizierungsoptionen pro Prüfung:**  
  Können mehrere Authentifizierungsoptionen parallel erlaubt sein?
  > Wird vom BiP zentral gesteuert (Next-Exam muss nur unterstützen, was BiP vorgibt).

- **Mehrsprachigkeit:**  
  Gibt es Anforderungen an Mehrsprachigkeit?
  > BiP und Next‑Exam sind auf Englisch/Deutsch verfügbar; weitere Übersetzungen nicht geplant.

- **Sitzplan-Feature ab Version 1?**
  > Nein.

---

**ToDo:**  
- **Welche APIs stellt das Bildungsportal zur Verfügung (z. B. für Auswahl der Schulklasse)?**  
  → Schnittstellendokumentation von Christoph/Robert einholen!

## 6. Screenshots

Persönliches Dashboard:
<img width="1711" height="1241" alt="Screenshot_20250811_155049" src="https://github.com/user-attachments/assets/764117b6-dc19-474f-ac7d-84dde290d858" />

Schulspezifisches Dashboard:
<img width="1681" height="739" alt="Screenshot_20250811_155733" src="https://github.com/user-attachments/assets/e7ad57a0-93d7-48b5-b637-fbc059ad002d" />
