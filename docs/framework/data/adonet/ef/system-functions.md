---
title: Systemfunktionen
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 552f374bc1824a16fb323cd19abe79c1914295a7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248238"
---
# <a name="system-functions"></a>Systemfunktionen
Der .NET Framework-Datenanbieter für SQL Server (SqlClient) stellt die folgenden Systemfunktionen zur Verfügung:  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Gibt den Prüfsummenwert zurück. `CHECKSUM` wurde zum Erstellen von Hashindizes konzipiert.<br /><br /> **Argumente**<br /><br /> `value`: `Boolean`, ,`Byte` ,,`Int64`, ,`Decimal`,,, ,`String`Oder. `DateTime` `Double` `Int32` `Single` `Int16` `Binary` `Guid` Sie können einen, zwei oder drei Werte angeben.<br /><br /> **Rückgabewert**<br /><br /> Der Absolutwert des angegebenen Ausdrucks.<br /><br /> **Beispiel**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|Erzeugt das aktuelle Datum und die Uhrzeit im SQL Server-internen Format für `DateTime`-Werte mit einer Genauigkeit von 7 in SQL Server 2008 und einer Genauigkeit von 3 in SQL Server 2005.<br /><br /> **Rückgabewert**<br /><br /> Das aktuelle Systemdatum und die aktuelle Systemzeit als `DateTime`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER` `()`|Gibt den Namen des aktuellen Benutzers zurück.<br /><br /> **Rückgabewert**<br /><br /> Ein ASCII-`String`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Gibt die Anzahl von Bytes zurück, die für die Darstellung eines Ausdrucks verwendet werden.<br /><br /> **Argumente**<br /><br /> `expression`: `Boolean`, ,`Byte` ,,`Int64`, ,`String`,,, ,`Time`, ,`Binary`Oder `Single` `Decimal` `Double` `Int32` `Int16` `DateTime` `DateTimeOffset` `Guid`.<br /><br /> **Rückgabewert**<br /><br /> Die Größe von Eigenschaften als `Int32`.<br /><br /> **Beispiel**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|Gibt den Namen der Arbeitsstation zurück.<br /><br /> **Rückgabewert**<br /><br /> Ein `String` (Unicode).<br /><br /> **Beispiel**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Ermittelt, ob der eingegebene Ausdruck ein gültiges Datum ist.<br /><br /> **Argumente**<br /><br /> `expression`: `Boolean`, ,`Byte` ,,`Int64`, ,`String`,,, ,`Time`, ,`Binary`Oder `Single` `Decimal` `Double` `Int32` `Int16` `DateTime` `DateTimeOffset` `Guid`.<br /><br /> **Rückgabewert**<br /><br /> Eine `Int32`. Eins (1), wenn der eingegebene Ausdruck ein gültiges Datum ist. Andernfalls Null (0).<br /><br /> **Beispiel**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Ermittelt, ob ein Ausdruck ein gültiger numerischer Typ ist.<br /><br /> **Argumente**<br /><br /> `expression`: `Boolean`, ,`Byte` ,,`Int64`, ,`String`,,, ,`Time`, ,`Binary`Oder `Single` `Decimal` `Double` `Int32` `Int16` `DateTime` `DateTimeOffset` `Guid`.<br /><br /> **Rückgabewert**<br /><br /> Eine `Int32`. Eins (1), wenn der eingegebene Ausdruck ein gültiges Datum ist. Andernfalls Null (0).<br /><br /> **Beispiel**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|Erstellt einen eindeutigen Wert vom Typ Guid.<br /><br /> **Rückgabewert**<br /><br /> Ein `Guid`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Gibt den Datenbank-Benutzernamen zur angegebenen ID zurück.<br /><br /> **Argumente**<br /><br /> `expression`: Eine `Int32`-ID, die einem Datenbankbenutzer zugeordnet ist.<br /><br /> **Rückgabewert**<br /><br /> Ein `String` (Unicode).<br /><br /> **Beispiel**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 Weitere Informationen zu den von SqlClient unterstützten Zeichenfolgenfunktionen finden Sie in der Dokumentation für die SQL Server-Version, die im SqlClient-Anbietermanifest angegeben wurde:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[System Funktionen Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115918)|[System Funktionen Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115917)|[System Funktionen (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115919)|  
  
## <a name="see-also"></a>Siehe auch

- [Entity SQL Language (Entity SQL-Sprache)](./language-reference/entity-sql-language.md)
- [SqlClient für Entity Framework-Funktionen](sqlclient-for-ef-functions.md)
