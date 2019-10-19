---
title: 'IJsDebug:: OpenVirtualProcess – – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 3de39beb28a68ec3b8e0d76b17a7e914a464ecfe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577749"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess – metoda
Metoda factory používaná k vytvoření nového objektu virtuálního procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `processId`  
 pro ID procesu, ke kterému se má ladicí program připojit  
  
 `runtimeJsBaseAddress`  
 pro Základní adresa, na které se načte modul runtime jazyka JavaScript do cílového procesu.  
  
 `pDataTarget`  
 pro Rozhraní dodávané ladicím programem pro dotaz na stav procesu.  
  
 `ppProcess`  
 mimo Nový objekt procesu ladění  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Vrátí E_JsDEBUG_MISMATCHED_RUNTIME, pokud Jscript9diag a jscript9 se neshodují.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebug – rozhraní](../../winscript/reference/ijsdebug-interface.md)