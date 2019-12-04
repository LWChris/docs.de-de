---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643850"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="2b662-101">SerializableAttribute aus einigen Windows Forms-Typen entfernt</span><span class="sxs-lookup"><span data-stu-id="2b662-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="2b662-102"><xref:System.SerializableAttribute> wurde aus einigen Windows Forms-Klassen ohne bekannte Szenarios für binäre Serialisierung entfernt.</span><span class="sxs-lookup"><span data-stu-id="2b662-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2b662-103">Änderungsbeschreibung</span><span class="sxs-lookup"><span data-stu-id="2b662-103">Change description</span></span>

<span data-ttu-id="2b662-104">Die folgenden Typen enthalten in .NET Framework das Attribut <xref:System.SerializableAttribute>, das in .NET Core entfernt wurde:</span><span class="sxs-lookup"><span data-stu-id="2b662-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

<span data-ttu-id="2b662-105">In der Vergangenheit bereitete dieser Serialisierungsmechanismus schwerwiegende Wartungs- und Sicherheitsprobleme.</span><span class="sxs-lookup"><span data-stu-id="2b662-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="2b662-106">Die Beibehaltung von `SerializableAttribute` für Typen bedeutet, dass diese Typen auf Serialisierungsänderungen zwischen Versionen und auf potenzielle Serialisierungsänderungen zwischen Frameworks geprüft werden müssen.</span><span class="sxs-lookup"><span data-stu-id="2b662-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="2b662-107">Dies erschwert die Weiterentwicklung dieser Typen und verteuert die Beibehaltung.</span><span class="sxs-lookup"><span data-stu-id="2b662-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="2b662-108">Da es für diese Typen keine bekannten Serialisierungsszenarios gibt, sind die Auswirkungen minimal, wenn das Attribut entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="2b662-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="2b662-109">Weitere Informationen finden Sie unter [Binäre Serialisierung](~/docs/standard/serialization/binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="2b662-109">For more information, see [Binary serialization](~/docs/standard/serialization/binary-serialization.md).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2b662-110">Eingeführt in Version</span><span class="sxs-lookup"><span data-stu-id="2b662-110">Version introduced</span></span>

<span data-ttu-id="2b662-111">3.0 Vorschau 9</span><span class="sxs-lookup"><span data-stu-id="2b662-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2b662-112">Empfohlene Maßnahme</span><span class="sxs-lookup"><span data-stu-id="2b662-112">Recommended action</span></span>

<span data-ttu-id="2b662-113">Aktualisieren Sie jeden Code, der von diesen als serialisierbar markierten Typen abhängig ist.</span><span class="sxs-lookup"><span data-stu-id="2b662-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="2b662-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="2b662-114">Category</span></span>

<span data-ttu-id="2b662-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2b662-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2b662-116">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="2b662-116">Affected APIs</span></span>

- <span data-ttu-id="2b662-117">Keine</span><span class="sxs-lookup"><span data-stu-id="2b662-117">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->