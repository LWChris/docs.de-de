---
ms.openlocfilehash: e8fcd496b9c1921753ad0e1c2632f29bc5036956
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802508"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView löst ArgumentOutOfRangeException aus

|   |   |
|---|---|
|Details|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> wird asynchron ausgeführt, wenn die Spaltenvirtualisierung zwar aktiviert ist, die Spaltenbreiten aber noch nicht festgelegt wurden.  Wenn Spalten entfernt werden, bevor der asynchrone Vorgang abgeschlossen ist, kann eine <xref:System.ArgumentOutOfRangeException?displayProperty=name>-Ausnahme auftreten.|
|Vorschlag|Führen Sie eine der folgenden Aktionen aus:<ol><li>Upgrade auf .NET Framework 4.7</li><li>Den neuesten Wartungspatch für .NET Framework 4.6.2 installieren</li><li>Entfernen Sie Spalten erst, wenn die asynchrone Antwort auf die <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> abgeschlossen wurde.</li></ol>|
|Bereich|Microsoft Edge|
|Version|4.6.2|
|Typ|Laufzeit|
|Betroffene APIs|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|

