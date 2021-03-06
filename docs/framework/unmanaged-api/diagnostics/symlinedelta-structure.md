---
title: SYMLINEDELTA-Struktur
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
ms.openlocfilehash: a1e83e4b8cb6603029f3b42b1a3b9ba4810c9039
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438015"
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA-Struktur
Stellt Informationen für den Symbol Handler über Methoden bereit, die aufgrund von Änderungen verschoben wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|`mdMethod`|Das Metadatentoken der Methode.|  
|`delta`|Die Anzahl der Zeilen, die die Methode verschoben wurde.|  
  
## <a name="requirements"></a>Voraussetzungen  
 **Header:** Corsym. idl  
  
## <a name="see-also"></a>Siehe auch

- [Diagnosesymbolspeicher-Strukturen](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
