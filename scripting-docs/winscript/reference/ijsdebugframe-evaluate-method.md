---
title: Ijsdebugframe::evaluate – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38e826048e85456ca63e069de67701b1fc3e9f04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794388"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate – metoda
Vyhodnotí výraz v kontextu této rámce zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pExpressionText`  
 [v] Výraz k vyhodnocení.  
  
 `ppDebugProperty`  
 [out] Objekt reprezentující prohlížeč vlastností.  
  
 `pError`  
 [out] Chybová zpráva, pokud dojde k chybě.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Vrátí následující: S_OK: vyhodnocení úspěšné, * ppDebugProperty obsahuje výsledek vyhodnocení. S_FALSE: Vyhodnocení vyvolá chybu (nebo vyhodnocení operace není podporována), \*pError obsahuje chybovou zprávu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Ijsdebugframe – metoda](../../winscript/reference/ijsdebugframe-interface.md)