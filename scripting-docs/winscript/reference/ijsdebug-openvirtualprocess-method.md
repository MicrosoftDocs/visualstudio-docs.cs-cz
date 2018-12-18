---
title: Ijsdebug::openvirtualprocess – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebug.OpenVirtualProcess
apilocation:
- jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5acb137337e46a6e84f7d68c9330a3ca847f2e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794361"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess – metoda
Metoda Factory používaná k vytvoření nového objektu virtuálního procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `processId`  
 [v] Id procesu připojit ladicí program na.  
  
 `runtimeJsBaseAddress`  
 [v] Základní adresa, kdy prostředí JavaScript runtime načetl do tento cílový proces.  
  
 `pDataTarget`  
 [v] Ladicí program zadaný rozhraní pro dotaz na stav procesu.  
  
 `ppProcess`  
 [out] Nový objekt procesu ladění  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Vrátí E_JsDEBUG_MISMATCHED_RUNTIME Pokud Jscript9diag a Jscript9 se neshodují.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Ijsdebug – rozhraní](../../winscript/reference/ijsdebug-interface.md)