---
title: 'Vorgehensweise: Anfügen an Textdateien'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 97bcb5c511452e418df010f12d4b63f04251d021
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348871"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a>Vorgehensweise: Anfügen an Textdateien in Visual Basic

Die <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>-Methode kann zum Anfügen an eine Textdatei verwendet werden. Dazu müssen Sie den Parameter `append` auf `True` festlegen.  
  
### <a name="to-append-to-a-text-file"></a>Anfügen an eine Textdatei  
  
- Verwenden Sie die `WriteAllText`-Methode, geben Sie die Zieldatei und die Zeichenfolge an, die angefügt werden sollen, und legen Sie den `append`-Parameter auf `True` fest.  
  
     Dieses Beispiel schreibt die Zeichenfolge `"This is a test string."` in die Datei namens `Testfile.txt`.  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a>Stabile Programmierung  

 Die folgenden Bedingungen können einen Ausnahmefehler verursachen:  
  
- Der Pfad ist aus einem der folgenden Gründe ungültig: Er ist eine Zeichenfolge der Länge 0, er enthält nur Leerzeichen, er enthält ungültige Zeichen, oder er ist ein Gerätepfad (beginnt mit \\\\.\\) (<xref:System.ArgumentException>).  
  
- Der Pfad ist ungültig, da er `Nothing` ist (<xref:System.ArgumentNullException>).  
  
- `File` verweist auf einen Pfad, der nicht vorhanden ist (<xref:System.IO.FileNotFoundException> oder<xref:System.IO.DirectoryNotFoundException>).  
  
- Die Datei wird von einem anderen Prozess verwendet, oder ein E/A-Fehler tritt auf (<xref:System.IO.IOException>).  
  
- Der Pfad überschreitet die im System definierte maximale Länge (<xref:System.IO.PathTooLongException>).  
  
- Der Pfad eines Datei- oder Verzeichnisnamens enthält einen Doppelpunkt (:) oder hat ein ungültiges Format (<xref:System.NotSupportedException>).  
  
- Dem Benutzer fehlen die erforderlichen Berechtigungen zum Anzeigen des Pfades (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Schreiben in Dateien](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
