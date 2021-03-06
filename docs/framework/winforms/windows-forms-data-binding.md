---
title: Datenbindung
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: 68871db848ab46b88865e668f27f09972e8debcf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734609"
---
# <a name="windows-forms-data-binding"></a>Datenbindung in Windows Forms
Mit der Datenbindung in Windows Forms erhalten Sie die Möglichkeit, Informationen aus einer Datenquelle in Steuerelementen im Formular anzuzeigen und zu ändern. Sie können sowohl herkömmliche Datenquellen als auch beinahe alle Strukturen binden, die Daten enthalten.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Datenbindung und Windows Forms](data-binding-and-windows-forms.md)  
 Bietet eine Übersicht über die Datenbindung in Windows Forms.  
  
 [Von Windows Forms unterstützte Datenquellen](data-sources-supported-by-windows-forms.md)  
 Beschreibt die Datenquellen, die in Verbindung mit Windows Forms verwendet werden können.  
  
 [Auf Datenbindung bezogene Schnittstellen](interfaces-related-to-data-binding.md)  
 Beschreibt einige der Schnittstellen, die für die Windows Forms-Datenbindung verwendet werden.  
  
 [Gewusst wie: Navigieren durch Daten in Windows Forms](how-to-navigate-data-in-windows-forms.md)  
 Zeigt, wie Sie in den Elementen einer Datenquelle navigieren können.  
  
 [Änderungsbenachrichtigung in der Windows Forms-Datenbindung](change-notification-in-windows-forms-data-binding.md)  
 Beschreibt die unterschiedlichen Arten von Änderungsbenachrichtigungen für die Datenbindung in Windows Forms.  
  
 [Gewusst wie: Implementieren der INotifyPropertyChanged-Schnittstelle](how-to-implement-the-inotifypropertychanged-interface.md)  
 Zeigt, wie die <xref:System.ComponentModel.INotifyPropertyChanged>-Schnittstelle implementiert wird. Die Schnittstelle übergibt die Eigenschaftenänderungen an einem Geschäftsobjekt an ein gebundenes Steuerelement.  
  
 [Gewusst wie: Anwenden des PropertyNameChanged-Musters](how-to-apply-the-propertynamechanged-pattern.md)  
 Zeigt, wie das geänderte *propertyName*-Muster auf Eigenschaften eines Windows Forms Benutzer Steuer Elements angewendet wird.  
  
 [Gewusst wie: Implementieren der ITypedList-Schnittstelle](how-to-implement-the-itypedlist-interface.md)  
 Zeigt, wie die Ermittlung des Schemas für eine bindbare Liste durch Implementieren der <xref:System.ComponentModel.ITypedList>-Schnittstelle ermöglicht wird.  
  
 [Gewusst wie: Implementieren der IListSource-Schnittstelle](how-to-implement-the-ilistsource-interface.md)  
 Zeigt, wie die <xref:System.ComponentModel.IListSource>-Schnittstelle implementiert wird, um eine bindbare Klasse zu erstellen, die nicht <xref:System.Collections.IList> implementiert, sondern eine Liste von einem anderen Speicherort bereitstellt.  
  
 [Vorgehensweise: Sicherstellen, dass mehrere Steuerelemente, die an die gleiche Datenquelle gebunden sind, synchronisiert bleiben](multiple-controls-bound-to-data-source-synchronized.md)  
 Zeigt, wie das <xref:System.Windows.Forms.BindingSource.BindingComplete>-Ereignis behandelt wird, um sicherzustellen, dass alle an eine Datenquelle gebundenen Steuerelemente synchronisiert bleiben.  
  
 [Gewusst wie: Sicherstellen, dass die ausgewählte Zeile in einer untergeordneten Tabelle an der richtigen Position verbleibt](ensure-the-selected-row-in-a-child-table-correct.md)  
 Beschreibt, wie Sie sicherstellen können, dass die ausgewählte Zeile in einer untergeordneten Tabelle nicht geändert wird, wenn an einem Feld in der übergeordneten Tabelle eine Änderung vorgenommen wird.  
  
 Weitere Informationen finden Sie auch in [Bezug auf die Datenbindung](interfaces-related-to-data-binding.md), Vorgehens [Weise: Navigieren in Daten in Windows Forms](how-to-navigate-data-in-windows-forms.md)und Gewusst [wie: Erstellen eines einfach gebundenen Steuer Elements in einem Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).  
  
## <a name="reference"></a>Referenz  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 Beschreibt die Klasse, die für die Bindung zwischen einer bindbaren Komponente und einer Datenquelle steht.  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 Beschreibt die Klasse, die eine Datenquelle für die Bindung an Steuerelemente kapselt.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [BindingSource-Komponente](./controls/bindingsource-component.md)  
 Enthält eine Liste mit Themen, in denen gezeigt wird, wie die <xref:System.Windows.Forms.BindingSource>-Komponente verwendet wird.  
  
 [DataGridView-Steuerelement](./controls/datagridview-control-windows-forms.md)  
 Enthält eine Liste mit Themen, in denen gezeigt wird, wie ein bindbares DataGrid-Steuerelement verwendet wird.  
  
 Siehe auch [zugreifen auf Daten in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).
