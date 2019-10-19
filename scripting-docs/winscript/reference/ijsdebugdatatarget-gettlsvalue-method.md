---
title: 'IJsDebugDataTarget:: Gettlsvalue – – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: eecf9acf370656d5310a03d68ed74e10671a0bc2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577607"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue – metoda
Pro vlákno, které je laděno, načte hodnotu z slotu thread local Storage (TLS) pro zadaný index TLS.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadId`  
 pro Vlákno spuštěné v cílovém procesu, ze kterého se má číst.  
  
 `tlsIndex`  
 pro Index TLS, který byl přidělen v případě, že cílový proces volal funkci TlsAlloc.  
  
 `pValue`  
 mimo Hodnota velikosti ukazatele, která byla uložena ve slotu TLS vlákna. Pokud je cílové vlákno 32-bit, horní 32-bitů této hodnoty bude nula.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Každé vlákno procesu má vlastní slot pro každý index TLS.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebugDataTarget – rozhraní](../../winscript/reference/ijsdebugdatatarget-interface.md)