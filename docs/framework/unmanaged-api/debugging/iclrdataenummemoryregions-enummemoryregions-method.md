---
title: ICLRDataEnumMemoryRegions::EnumMemoryRegions-Methode
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
ms.openlocfilehash: f2b2bbe8bcecf71f6d3016fb35dfbf5ba1353aea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785641"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a>ICLRDataEnumMemoryRegions::EnumMemoryRegions-Methode
Listet angegebene Speicherbereiche auf.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `callback`  
 in Ein Zeiger auf eine [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) -Instanz, die von dieser Methode für jeden aufgezählten Speicherbereich aufgerufen wird, um den Debugger über das Ergebnis zu benachrichtigen.  
  
 Die Enumeration der Speicherbereiche wird auch dann fortgesetzt, wenn der Rückruf auf einen Fehler hinweist.  
  
 `miniDumpFlags`  
 in Nicht verwendet.  
  
 `clrFlags`  
 in Ein Wert der [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) -Enumeration, der die aufzuzählenden Speicherbereiche angibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode verwendet die angegebene [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) -Instanz, um den Aufrufer über Ergebnisse zu benachrichtigen.  
  
## <a name="requirements"></a>-Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Clrdata. idl, Clrdata. h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework Versionen:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch

- [ICLRDataEnumMemoryRegions-Schnittstelle](iclrdataenummemoryregions-interface.md)
