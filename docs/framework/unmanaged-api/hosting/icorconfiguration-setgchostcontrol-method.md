---
title: ICorConfiguration::SetGCHostControl-Methode
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
ms.openlocfilehash: 5a32fb0480e76f47495590a29c329f54722e2dee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127778"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a>ICorConfiguration::SetGCHostControl-Methode
Legt die Rückruf Schnittstelle fest, die vom Garbage Collector verwendet werden soll, um den Host zum Ändern der Grenzwerte für den virtuellen Arbeitsspeicher anzufordern.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a>Parameter  
 `pGCHostControl`  
 in Ein Zeiger auf ein [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) -Objekt, das dem Garbage Collector ermöglicht, den Host zum Ändern der Grenzwerte für den virtuellen Arbeitsspeicher anzufordern.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Mscoree. h  
  
 **Bibliothek:** Als Ressource in Mscoree. dll enthalten  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch

- [ICorConfiguration-Schnittstelle](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
