---
title: 'Gewusst wie: Erstellen eines WindowsPrincipal-Objekts'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
ms.openlocfilehash: d409c0e9a2a6564e5fb16e4e2c72ab661ae2d5ce
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706161"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Gewusst wie: Erstellen eines WindowsPrincipal-Objekts
Es gibt zwei Möglichkeiten, ein <xref:System.Security.Principal.WindowsPrincipal>-Objekt zu erstellen. Diese hängen davon ab, ob Code eine rollenbasierte Validierung mehrfach oder nur einmal ausführen muss.  
  
 Wenn Code eine rollenbasierte Validierung mehrfach ausführen muss, verursacht die erste der folgenden Methoden einen geringeren Mehraufwand. Wenn Code eine rollenbasierte Validierung nur einmal ausführen muss, können Sie ein <xref:System.Security.Principal.WindowsPrincipal>-Objekt mit dem zweiten der folgenden Verfahren erstellen.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>So erstellen Sie ein WindowsPrincipal-Objekt für eine mehrfache Validierung  
  
1. Rufen Sie die <xref:System.AppDomain.SetPrincipalPolicy%2A>-Methode für das <xref:System.AppDomain>-Objekt auf, das von der statischen <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType>-Eigenschaft zurückgegeben wird, wobei Sie der Methode einen <xref:System.Security.Principal.PrincipalPolicy>-Enumerationswert übergeben, der die neue Richtlinie angibt. Unterstützte Werte sind <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> und <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>. Im folgenden Code wird dieser Methodenaufruf veranschaulicht.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. Wenn die Richtlinie festgelegt ist, rufen Sie mit der <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType>-Eigenschaft den Prinzipal ab, der den aktuellen Windows-Benutzer kapselt. Da die Eigenschaft den Rückgabetyp <xref:System.Security.Principal.IPrincipal> hat, müssen Sie das Ergebnis in einen <xref:System.Security.Principal.WindowsPrincipal>-Typ umwandeln. Im folgenden Code wird ein neues <xref:System.Security.Principal.WindowsPrincipal>-Objekt mit dem Wert des Prinzipals initialisiert, der dem aktuellen Thread zugeordnet ist.  
  
    ```csharp  
    WindowsPrincipal myPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3. Nachdem das Principal-Objekt erstellt wurde, können Sie es mit einer von mehreren Methoden überprüfen.  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>So erstellen Sie ein WindowsPrincipal-Objekt für eine einzelne Validierung  
  
1. Initialisieren Sie ein neues <xref:System.Security.Principal.WindowsIdentity>-Objekt, indem Sie die statische <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType>-Methode aufrufen. Diese fragt das aktuelle Windows-Konto ab und legt die Informationen über dieses Konto in dem neu erstellten Identitätsobjekt ab. Der folgende Code erstellt ein neues <xref:System.Security.Principal.WindowsIdentity>-Objekt und initialisiert es mit dem aktuellen authentifizierten Benutzer.  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. Erstellen Sie ein neues <xref:System.Security.Principal.WindowsPrincipal>-Objekt, und übergeben Sie an dieses den Wert des im vorherigen Schritt erstellten <xref:System.Security.Principal.WindowsIdentity>-Objekts.  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. Nachdem das Principal-Objekt erstellt wurde, können Sie es mit einer von mehreren Methoden überprüfen.  
  
## <a name="see-also"></a>Siehe auch

- [Principal- und Identitätsobjekte](../../../docs/standard/security/principal-and-identity-objects.md)
