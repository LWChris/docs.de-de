---
title: 'Vorgehensweise: Überprüfen des Verbindungsstatus'
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: 89ef431759dac25bd213fd954db0712ad95434b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345881"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a>Vorgehensweise: Überprüfen des Verbindungsstatus in Visual Basic

Die <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>-Eigenschaft kann verwendet werden, um zu ermitteln, ob der Computer über eine funktionierende Netzwerk- oder Internetverbindung verfügt.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a>So überprüfen Sie, ob ein Computer über eine funktionierende Verbindung verfügt  
  
- Bestimmen Sie, ob die `IsAvailable`-Eigenschaft `True` oder `False` ist. Im folgende Code wird der Status der Eigenschaft überprüft und ausgegeben:  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     Dieses Codebeispiel ist auch als IntelliSense-Codeausschnitt verfügbar. In der Codeausschnittauswahl ist er unter **Konnektivität und Netzwerk** zu finden. Weitere Informationen finden Sie unter [Codeausschnitte](/visualstudio/ide/code-snippets).  
  
## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
