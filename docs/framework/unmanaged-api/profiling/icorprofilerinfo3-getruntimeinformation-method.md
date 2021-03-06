---
title: ICorProfilerInfo3::GetRuntimeInformation-Methode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
ms.openlocfilehash: e3d167be9a4091ae57a3283424186142e90ca7a1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868550"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation-Methode
Stellt Versionsinformationen über die Common Language Runtime (CLR) bereit, für die ein Profil erstellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a>Parameters  
 `pClrInstanceId`  
 vorgenommen Die repräsentative ID einer laufenden CLR-Instanz in einem Prozess. Dies ist das gleiche wie das `ClrInstanceID`, das vom Ereignis Ablauf Verfolgung für Windows (ETW)-Start Ereignis gemeldet wird.  
  
 `pRuntimeType`  
 vorgenommen Der Lauf Zeittyp. Dieser Parameter gibt `COR_PRF_DESKTOP_CLR` für die Desktop Version der CLR zurück, oder `COR_PRF_CORE_CLR` für die in Silverlight verwendete Core-Version der CLR.  
  
 `pMajorVersion`  
 vorgenommen Die Hauptversionsnummer der CLR.  
  
 `pMinorVersion`  
 vorgenommen Die neben Versionsnummer der CLR.  
  
 `pBuildVersion`  
 vorgenommen Die Buildversionsnummer der CLR.  
  
 `pQFEVersion`  
 vorgenommen Die Versionsnummer der CLR, die einem Software Update zugeordnet ist.  
  
 `cchVersionString`  
 in Die Länge (in Zeichen) des Puffers, auf den `szVersionString` zeigt.  
  
 `pcchVersionString`  
 vorgenommen Die Länge `szVersionString`in Zeichen.  
  
 `szVersionString`  
 vorgenommen Die CLR-Versions Zeichenfolge.  
  
## <a name="remarks"></a>Hinweise  
 Sie können für jeden Parameter NULL übergeben. `pcchVersionString` kann jedoch nur dann NULL sein, wenn `szVersionString` ebenfalls NULL ist.  
  
## <a name="requirements"></a>-Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework Versionen:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch

- [ICorProfilerInfo3-Schnittstelle](icorprofilerinfo3-interface.md)
- [Profilerstellungsschnittstellen](profiling-interfaces.md)
- [Profilerstellung](index.md)
