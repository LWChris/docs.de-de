---
title: Abrufen von unterstützten Steuerelementmustern für Benutzeroberflächenautomatisierung
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: b1da13cf5eb39a61f40848a5f199cfd39b16d7c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435640"
---
# <a name="get-supported-ui-automation-control-patterns"></a>Abrufen von unterstützten Steuerelementmustern für Benutzeroberflächenautomatisierung
> [!NOTE]
> Diese Dokumentation ist für .NET Framework-Entwickler vorgesehen, die die verwalteten [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-Klassen verwenden möchten, die im <xref:System.Windows.Automation>-Namespace definiert sind. Aktuelle Informationen zur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]finden Sie auf der Seite zur [Windows-Automatisierungs-API: UI-Automatisierung](/windows/win32/winauto/entry-uiauto-win32).  
  
 In diesem Thema wird gezeigt, wie Steuerelementmusterobjekte aus [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-Elementen abgerufen werden.  
  
### <a name="obtain-all-control-patterns"></a>Abrufen aller Steuerelementmuster  
  
1. Rufen Sie das <xref:System.Windows.Automation.AutomationElement>-Objekt ab, an dessen Steuerelementmustern Sie interessiert sind.  
  
2. Rufen Sie <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> auf, um alle Steuerelementmuster aus dem Element abzurufen.  
  
> [!CAUTION]
> Ein Client sollte auf keinen Fall <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> verwenden. Die Leistung kann schwerwiegend beeinträchtigt werden, da diese Methode intern <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> für jedes vorhandene Steuerelementmuster aufruft. Wenn möglich sollte ein Client <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> für die gewünschten Steuerelementmuster aufrufen.  
  
### <a name="obtain-a-specific-control-pattern"></a>Abrufen eines bestimmten Steuerelementmusters  
  
1. Rufen Sie das <xref:System.Windows.Automation.AutomationElement>-Objekt ab, an dessen Steuerelementmustern Sie interessiert sind.  
  
2. Rufen Sie <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> oder <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> auf, um auf ein bestimmtes Muster abzufragen. Diese Methoden ähneln sich, wenn das Muster aber nicht gefunden wird, löst <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> eine Ausnahme aus, während <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> den Wert `false` zurückgibt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein <xref:System.Windows.Automation.AutomationElement> für ein Listenelement und aus diesem Element ein <xref:System.Windows.Automation.SelectionItemPattern> abgerufen.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Siehe auch

- [UI Automation Control Patterns for Clients](ui-automation-control-patterns-for-clients.md)
