---
title: IHostMAlloc::DebugAlloc-Methode
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: a2a752f23ed64795f9208b9101c21bc585d5f431
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136818"
---
# <a name="ihostmallocdebugalloc-method"></a>IHostMAlloc::DebugAlloc-Methode
Fordert an, dass der Host die angegebene Arbeitsspeicher Menge aus dem Heap zuweist und zusätzlich nachverfolgt, wo der Arbeitsspeicher belegt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a>Parameter  
 `cbSize`  
 in Die Größe der aktuellen Speicher Belegungs Anforderung in Bytes.  
  
 `dwCriticalLevel`  
 in Einer der [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) -Werte, der die Auswirkung eines Zuordnungs Fehlers angibt.  
  
 `pszFileName`  
 in Die Codedatei der ausführbaren Datei, die deentschlgt wird.  
  
 `iLineNo`  
 in Die Zeilennummer in `pszFileName`, in der die Zuordnung angefordert wurde.  
  
 `ppMem`  
 vorgenommen Ein Zeiger auf den zugeordneten Arbeitsspeicher oder NULL, wenn die Anforderung nicht abgeschlossen werden konnte.  
  
## <a name="return-value"></a>Rückgabewert  
  
|HRESULT|Beschreibung|  
|-------------|-----------------|  
|S_OK|`DebugAlloc` erfolgreich zurückgegeben.|  
|HOST_E_CLRNOTAVAILABLE|Die CLR wurde nicht in einen Prozess geladen, oder die CLR befindet sich in einem Zustand, in dem Sie verwalteten Code nicht ausführen oder den-Befehl nicht erfolgreich verarbeiten kann.|  
|HOST_E_TIMEOUT|Timeout des Aufrufes.|  
|HOST_E_NOT_OWNER|Der Aufrufer ist nicht Besitzer der Sperre.|  
|HOST_E_ABANDONED|Ein Ereignis wurde abgebrochen, während ein blockierter Thread oder eine Fiber darauf wartete.|  
|E_FAIL|Ein unbekannter schwerwiegender Fehler ist aufgetreten. Wenn eine Methode E_FAIL zurückgibt, kann die CLR innerhalb des Prozesses nicht mehr verwendet werden. Nachfolgende Aufrufe von Hostingmethoden geben HOST_E_CLRNOTAVAILABLE zurück.|  
|E_OUTOFMEMORY|Zum Abschluss der Zuordnungs Anforderung war nicht genügend Arbeitsspeicher verfügbar.|  
  
## <a name="remarks"></a>Hinweise  
 Die CLR ruft einen Schnittstellen Zeiger auf eine [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) -Instanz ab, indem die [IHostMemoryManager:: createmzuzugsmethode](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) aufgerufen wird. `DebugAlloc` ermöglicht der Laufzeit, Code Dateiinformationen für die Verwendung während des Debuggens zu erhalten.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Mscoree. h  
  
 **Bibliothek:** Als Ressource in Mscoree. dll enthalten  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch

- [IHostMemoryManager-Schnittstelle](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [IHostMalloc-Schnittstelle](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
