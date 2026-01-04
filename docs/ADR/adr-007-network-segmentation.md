# ADR-007: Netzwerk-Segmentierung und Isolation von Workloads

**Status:** Accepted  
**Datum:** 2026-01-04  

## Context
In einer Azure-Plattform mit mehreren Workloads erhöht ein gemeinsames, flaches Netzwerk die Angriffsfläche und das Risiko von lateralen Bewegungen bei Sicherheitsvorfällen.  
Zusätzlich erschwert ein fehlendes Netzwerkdesign die klare Trennung von Verantwortlichkeiten sowie den Betrieb unterschiedlicher Sicherheits- und Compliance-Anforderungen.

## Decision
Die Architektur setzt auf eine segmentierte Netzwerkstruktur.  
Plattform- und Workload-Komponenten werden in getrennten Virtual Networks betrieben.  
Die Kommunikation zwischen Netzsegmenten erfolgt ausschließlich kontrolliert und explizit freigegeben.

## Rationale
Durch Netzwerk-Segmentierung werden Sicherheitsvorfälle auf einzelne Workloads begrenzt, laterale Bewegungen verhindert und unterschiedliche Schutzbedarfe technisch durchsetzbar.  
Das Design unterstützt das Zero-Trust-Prinzip sowie eine klare Trennung von Verantwortlichkeiten.

## Alternatives
- Gemeinsames Virtual Network für alle Workloads  
- Trennung ausschließlich über Subnets und Network Security Groups  

## Consequences
- Verbesserte Sicherheitsisolation zwischen Workloads  
- Klar definierte Netzwerkgrenzen und Verantwortlichkeiten  
- Erhöhter initialer Design- und Betriebsaufwand
