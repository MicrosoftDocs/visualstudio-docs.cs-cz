---
title: Ijsdebugdatatarget::gettlsvalue – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetTlsValue
apilocation:
- jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4205adfb24a1a64d4e90f3fdcaf5a5ecbc4028de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794517"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue – metoda
Pro vlákno laděné načte hodnotu ve slotu přístup z více vláken místní úložiště (TLS) pro zadaný index TLS.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadId`  
 [v] Spouštění v tento cílový proces ke čtení z vlákna.  
  
 `tlsIndex`  
 [v] Protokol TLS index, který byl přidělen při volání funkce TlsAlloc tento cílový proces.  
  
 `pValue`  
 [out] Hodnotu ukazatele proměnlivé velikosti, která byla uložená ve vlákně na TLS slotu. Pokud je cílový vlákno 32-bit, bude horní 32 bity tuto hodnotu nula.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Každé vlákno procesů má svůj vlastní slotu pro každý index TLS.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Ijsdebugdatatarget – rozhraní](../../winscript/reference/ijsdebugdatatarget-interface.md)