---
title: Übersicht über LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: 20d9be052ba2567c16718b4b1c1019427c9b5df1
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634819"
---
# <a name="linq-to-dataset-overview"></a>Übersicht über LINQ to DataSet
Der <xref:System.Data.DataSet> ist eine der am häufigsten verwendeten Komponenten von ADO.net. Es ist ein Schlüsselelement des getrennten Programmiermodells, auf dem ADO.NET basiert, und ermöglicht es Ihnen, Daten aus verschiedenen Datenquellen explizit zwischenzuspeichern. Für die Darstellungsebene arbeitet das <xref:System.Data.DataSet> eng mit GUI-Steuerelementen für die Datenbindung zusammen. Für die mittlere Ebene stellt es einen Cache bereit, in dem die relationale Form von Daten zwischengespeichert wird, und es bietet Dienste für die schnelle und einfache Navigation in Abfragen und Hierarchien. Ein gängiges Verfahren, mit dem die Anzahl von Anforderungen für eine Datenbank gesenkt wird, besteht darin, die <xref:System.Data.DataSet> für die Zwischenspeicherung in der mittleren Ebene zu verwenden. Stellen Sie sich beispielsweise eine datengesteuerte ASP.NET-Webanwendung vor. Ein beträchtlicher Teil der Anwendung weist keine häufigen Änderungen auf und bleibt auch über Sitzungsgrenzen hinweg und bei verschiedenen Benutzern unverändert. Diese Daten können im Arbeitsspeicher des Webservers abgelegt werden, wodurch sich die Zahl der Datenbankanfragen verringert und die Interaktionen des Benutzers beschleunigt werden. Ein weiterer nützlicher Aspekt des <xref:System.Data.DataSet> besteht darin, dass eine Anwendung Daten Teilmengen aus einer oder mehreren Datenquellen in den Anwendungsbereich bringen kann. Die Anwendung kann dann die Daten im Arbeitsspeicher bearbeiten, während die relationale Form erhalten bleibt.  
  
 Trotz seiner häufigen Verwendung sind die Abfragefunktionen des <xref:System.Data.DataSet> begrenzt. Zum Filtern und Sortieren kann die <xref:System.Data.DataTable.Select%2A>-Methode verwendet werden, und die Methoden <xref:System.Data.DataRow.GetChildRows%2A> und <xref:System.Data.DataRow.GetParentRow%2A> ermöglichen die Navigation in der Hierarchie. Für komplexere Dinge muss der Entwickler jedoch eine benutzerdefinierte Abfrage schreiben. Das Ergebnis sind häufig Anwendungen, deren Leistung zu wünschen übrig lässt und die sich schwer warten lassen.  
  
 Mit LINQ to DataSet wird das Abfragen von Daten, die in einem <xref:System.Data.DataSet> Objekt zwischengespeichert sind, vereinfacht. Die entsprechenden Abfragen werden nicht als in den Anwendungscode eingebettete Zeichenfolgenliterale, sondern in der Programmiersprache selbst ausgedrückt. Dies bedeutet, dass Entwickler keine separate Abfragesprache erlernen müssen. Außerdem ermöglicht LINQ to DataSet Visual Studio-Entwicklern, produktiver zu arbeiten, da die Visual Studio-IDE Syntax Überprüfung zur Kompilierzeit, statische Typisierung und IntelliSense-Unterstützung für LINQ bereitstellt. LINQ to DataSet können auch verwendet werden, um Daten abzufragen, die aus einer oder mehreren Datenquellen konsolidiert wurden. Dadurch werden viele Szenarios möglich, in denen ein gewisses Maß an Flexibilität für die Darstellung und Behandlung von Daten erforderlich ist. Diese Manipulationsmethode wird insbesondere bei der Erstellung von Berichterstellungs-, Analyse- und Business Intelligence-Anwendungen benötigt.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>Abfragen von "DataSets" mit LINQ to DataSet  
 Bevor Sie mit dem Abfragen eines <xref:System.Data.DataSet> Objekts mit LINQ to DataSet beginnen können, müssen Sie die <xref:System.Data.DataSet>auffüllen. Es gibt mehrere Möglichkeiten zum Laden von Daten in eine <xref:System.Data.DataSet>, z. b. die Verwendung der <xref:System.Data.Common.DataAdapter> Klasse oder [LINQ to SQL](./sql/linq/index.md). Nachdem die Daten in ein <xref:System.Data.DataSet> Objekt geladen wurden, können Sie damit beginnen, Sie abzufragen. Das Formulieren von Abfragen mithilfe von LINQ to DataSet ähnelt der Verwendung von LINQ (Language-Integrated Query) mit anderen LINQ-fähigen Datenquellen. LINQ-Abfragen können für einzelne Tabellen in einem <xref:System.Data.DataSet> oder für mehr als eine Tabelle mithilfe der <xref:System.Linq.Enumerable.Join%2A>-und <xref:System.Linq.Enumerable.GroupJoin%2A>-Standard Abfrage Operatoren ausgeführt werden.  
  
 LINQ-Abfragen werden sowohl bei typisierten als auch bei nicht typisierten <xref:System.Data.DataSet> Objekten unterstützt. Wenn das <xref:System.Data.DataSet>-Schema zum Zeitpunkt der Anwendungskonzeptionierung bereits bekannt ist, wird empfohlen, mit einem typisierten <xref:System.Data.DataSet> zu arbeiten. In einem typisierten <xref:System.Data.DataSet> haben die Tabellen und Zeilen für jede Spalte typisierte Member, wodurch die Abfragen einfacher und lesbarer werden.  
  
 Zusätzlich zu den in "System. Core. dll" implementierten Standard Abfrage Operatoren fügt LINQ to DataSet mehrere <xref:System.Data.DataSet>spezifische Erweiterungen hinzu, die die Abfrage eines Satzes von <xref:System.Data.DataRow> Objekten vereinfachen. Diese <xref:System.Data.DataSet>-spezifischen Erweiterungen enthalten Operatoren für den Vergleich von Zeilenfolgen sowie Methoden, die den Zugriff auf die Spaltenwerte einer <xref:System.Data.DataRow> ermöglichen.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>n-Ebenen-Anwendungen und LINQ to DataSet  
 N-Tier-Datenanwendungen sind datenzentrische Anwendungen, die in mehrere logische Ebenen (oder Tiers) unterteilt sind. Eine typische n-Ebenen-Anwendung besteht aus einer Darstellungsebene, einer mittleren Ebene und einer Datenschicht. Die Aufteilung der Anwendungskomponenten in verschiedene Ebenen erhöht die Verwaltbarkeit und die Skalierbarkeit der Anwendung. Weitere Informationen zu n-Tier-Daten Anwendungen finden Sie unter [Arbeiten mit Datasets in n-Tier-Anwendungen](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
 In n-Ebenen-Anwendungen wird das <xref:System.Data.DataSet> häufig in der mittleren Ebene verwendet, um Informationen für Webanwendungen zwischenzuspeichern. Die LINQ to DataSet Abfrage Funktionalität wird durch Erweiterungs Methoden implementiert und erweitert die vorhandene ADO.NET 2,0-<xref:System.Data.DataSet>.  
  
## <a name="see-also"></a>Siehe auch

- [Abfragen von DataSets](querying-datasets-linq-to-dataset.md)
- [Language Integrated Query (LINQ) – C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Language Integrated Query (LINQ) – Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](./sql/linq/index.md)
