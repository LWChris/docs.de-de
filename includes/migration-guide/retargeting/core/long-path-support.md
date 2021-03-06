---
ms.openlocfilehash: f672645fb98f511f7e1326c9c584b287a0fae7dc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859369"
---
### <a name="long-path-support"></a>Unterstützung für lange Pfade

|   |   |
|---|---|
|Details|Für Apps mit der Zielplattform .NET Framework 4.6.2 und höher werden lange Pfade (bis zu 32.000 Zeichen) unterstützt, und die Beschränkung auf 260 Zeichen (oder <code>MAX_PATH</code>) für die Pfadlänge wurde aufgehoben. Bei Apps, die neu kompiliert werden, um .NET Framework 4.6.2 als Zielplattform zu verwenden, lösen Codepfade, die zuvor aufgrund der Überschreitung der Pfadlänge von 260 Zeichen <xref:System.IO.PathTooLongException?displayProperty=name> ausgelöst haben, nun unter den folgenden Bedingungen <xref:System.IO.PathTooLongException?displayProperty=name> aus:<ul><li>Die Zahl der Pfadzeichen überschreitet <xref:System.Int16.MaxValue> (32.767).</li><li>Das Betriebssystem gibt <code>COR_E_PATHTOOLONG</code> oder einen dazu äquivalenten Wert zurück.</li></ul>Bei Apps mit der Zielplattform .NET Framework 4.6.1 und früheren Versionen löst die Laufzeit automatisch eine <xref:System.IO.PathTooLongException?displayProperty=name> aus, wenn ein Pfad die Länge von 260 Zeichen überschreitet.|
|Vorschlag|Für Apps mit der Zielplattform .NET Framework 4.6.2 können Sie sich gegen die Unterstützung von langen Pfaden entscheiden, wenn sie nicht erwünscht ist, indem Sie Folgendes dem Abschnitt <code>&lt;runtime&gt;</code> Ihrer <code>app.config</code>-Datei hinzufügen:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Sie können bei Anwendungen, die für frühere Versionen von .NET Framework vorgesehen sind, aber in .NET Framework 4.6.2 oder höher ausgeführt werden, lange Pfade unterstützen, indem Sie dem Abschnitt <code>&lt;runtime&gt;</code> der <code>app.config</code>-Datei Folgendes hinzufügen:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Bereich|Gering|
|Version|4.6.2|
|Typ|Neuzuweisung|

