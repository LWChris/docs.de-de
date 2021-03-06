---
title: Datenbindung und LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: 2b49e2a3ff0d95dcbceff8099f51993c0f08d64e
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634871"
---
# <a name="data-binding-and-linq-to-dataset"></a>Datenbindung und LINQ to DataSet
Die *Datenbindung* ist der Prozess, der eine Verbindung zwischen der Anwendungs Benutzeroberfläche und der Geschäftslogik herstellt. Wenn die Bindungseinstellungen korrekt sind und bei einer Änderung des Werts ordnungsgemäße Benachrichtigungen ausgegeben werden, werden die Elemente, die an die Daten gebunden sind, automatisch aktualisiert. Beim <xref:System.Data.DataSet> handelt es sich um eine im Arbeitsspeicher residierende Darstellung von Daten, die – unabhängig von der Quelle der Daten – ein konsistentes relationales Programmiermodell bereitstellt. Die ADO.NET 2.0-<xref:System.Data.DataView> ermöglicht es Ihnen, die in einer <xref:System.Data.DataTable> gespeicherten Daten zu sortieren und zu filtern. Diese Funktionalität wird häufig in Datenbindungsanwendungen verwendet. Mit einer <xref:System.Data.DataView> können Sie die Daten in einer Tabelle mit verschiedenen Sortierreihenfolgen verfügbar machen und nach Zeilenstatus oder auf der Basis eines Filterausdrucks filtern. Weitere Informationen zum <xref:System.Data.DataView>-Objekt finden Sie unter [DataViews](./dataset-datatable-dataview/dataviews.md).  
  
 LINQ to DataSet ermöglicht es Entwicklern, mithilfe von LINQ (Language-Integrated Query) komplexe, leistungsstarke Abfragen für eine <xref:System.Data.DataSet> zu erstellen. Eine LINQ to DataSet Abfrage gibt jedoch eine Enumeration von <xref:System.Data.DataRow> Objekten zurück, die in einem Bindungs Szenario nicht einfach verwendet werden kann. Um die Bindung zu vereinfachen, können Sie eine <xref:System.Data.DataView> aus einer LINQ to DataSet-Abfrage erstellen. In diesem <xref:System.Data.DataView> werden die in der Abfrage angegebenen Filter-und Sortiervorgänge verwendet, Sie eignet sich jedoch besser für die Datenbindung. LINQ to DataSet erweitert die Funktionen des <xref:System.Data.DataView>, indem LINQ-Ausdrucks basiertes Filtern und Sortieren bereitgestellt wird. Dies ermöglicht viel komplexere und leistungsfähigere Filter-und Sortiervorgänge als die Zeichen folgen basierte Filterung und Sortierung.  
  
 Beachten Sie, dass die <xref:System.Data.DataView> die Abfrage selbst ist und es sich dabei nicht um eine Ansicht handelt, die der Abfrage aufgesetzt wurde. Die <xref:System.Data.DataView> ist an ein Benutzeroberflächensteuerelement, wie z. B. ein <xref:System.Windows.Forms.DataGrid> oder eine <xref:System.Windows.Forms.DataGridView>, gebunden und stellt so ein einfaches Datenbindungsmodell bereit. Eine <xref:System.Data.DataView> kann auch aus einer <xref:System.Data.DataTable> erstellt werden, sodass eine Standardansicht dieser Tabelle zur Verfügung steht.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erstellen eines DataView-Objekts](creating-a-dataview-object-linq-to-dataset.md)  
 Enthält Informationen zum Erstellen einer <xref:System.Data.DataView>.  
  
 [Filtern mit DataView](filtering-with-dataview-linq-to-dataset.md)  
 Beschreibt das Filtern mit der <xref:System.Data.DataView>.  
  
 [Sortieren mit DataView](sorting-with-dataview-linq-to-dataset.md)  
 Beschreibt das Sortieren mit der <xref:System.Data.DataView>.  
  
 [Abfragen der DataRowView-Sammlung in einer DataView](querying-the-datarowview-collection-in-a-dataview.md)  
 Bietet Informationen über das Abfragen der von der <xref:System.Data.DataRowView> bereitgestellten <xref:System.Data.DataView>-Auflistung.  
  
 [DataView-Leistung](dataview-performance.md)  
 Enthält Informationen zur <xref:System.Data.DataView> und zur Leistung.  
  
 [Vorgehensweise: Binden eines DataView-Objekts an ein Windows Forms-DataGridView-Steuerelement](how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Beschreibt die Vorgehensweise beim Binden eines <xref:System.Data.DataView>-Objekts an eine <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="see-also"></a>Siehe auch

- [Programmierhandbuch](programming-guide-linq-to-dataset.md)
