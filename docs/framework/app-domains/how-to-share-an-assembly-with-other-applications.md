---
title: 'Vorgehensweise: Verwenden einer Assembly mit anderen Anwendungen'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b1ef195458dd2de95eeb5e25089339e55d9e3fbb
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972882"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a>Vorgehensweise: Verwenden einer Assembly mit anderen Anwendungen
Assemblys können sowohl privat als auch freigegeben sein: Standardmäßig bestehen die meisten einfachen Programme aus einer privaten Assembly, da sie nicht für den Gebrauch durch andere Anwendungen vorgesehen sind.  

Wenn Sie eine Assembly mit anderen Anwendungen verwenden möchten, muss diese in den [globalen Assemblycache](gac.md) eingefügt werden.  
  
So nutzen Sie eine Assembly mit anderen Anwendungen:
  
1. Erstellen Ihrer Assembly. Weitere Informationen finden Sie unter [Erstellen von Assemblys](../../standard/assembly/create.md).  
  
2. Weisen Sie Ihrer Assembly einen starken Namen zu. Weitere Informationen finden Sie unter [Vorgehensweise: Signieren einer Assembly mit einem starken Namen](../../standard/assembly/sign-strong-name.md).  
  
3. Weisen Sie Ihrer Assembly Versionsinformationen zu. Weitere Informationen dazu finden Sie unter [Versionsverwaltung für Assemblys](../../standard/assembly/versioning.md).  
  
4. Fügen Sie Ihre Assembly in den globalen Assemblycache ein. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren einer Assembly im globalen Assemblycache](install-assembly-into-gac.md).  
  
5. Greifen Sie über andere Anwendungen auf die Typen in der Assembly zu. Weitere Informationen finden Sie unter [Vorgehensweise: Verweisen auf eine Assembly mit starkem Namen](../../standard/assembly/reference-strong-named.md).  
  
## <a name="see-also"></a>Siehe auch

- [C#-Programmierhandbuch](../../../api/index.md)
- [Programmierkonzepte (Visual Basic)](../../../api/index.md)
- [Programmieren mit Assemblys](../../standard/assembly/program.md)
