# ADR-008: Backup und Disaster Recovery

**Status:** Accepted  
**Datum:** 2026-01-04  

## Context
Der Betrieb geschäftskritischer Workloads in Azure erfordert Schutz vor Datenverlust durch Fehlbedienung, Softwarefehler, Sicherheitsvorfälle oder Infrastruktur-Ausfälle.  
Ohne definierte Backup- und Disaster-Recovery-Konzepte sind Wiederherstellbarkeit und Geschäftsfortführung nicht sichergestellt.

## Decision
Für alle produktiven Workloads werden verbindliche Backup- und Disaster-Recovery-Standards definiert.  
Backups werden zentral gesteuert und regelmäßig überprüft.  
Recovery-Ziele (RPO und RTO) werden pro Workload festgelegt und dokumentiert.

## Rationale
Ein strukturiertes Backup- und Disaster-Recovery-Konzept stellt sicher, dass Datenverluste begrenzt und Services innerhalb definierter Zeiträume wiederhergestellt werden können.  
Die klare Definition von Wiederherstellungszielen ermöglicht eine risikobasierte und wirtschaftlich sinnvolle Architektur.

## Alternatives
- Verzicht auf zentrale Backup-Standards  
- Verlass auf Plattformverfügbarkeit ohne eigene Wiederherstellungsstrategie  

## Consequences
- Zusätzlicher Speicher- und Betriebsaufwand  
- Erhöhte Betriebssicherheit und Wiederherstellbarkeit  
- Klare Erwartungshaltung gegenüber Fachbereichen und Management
