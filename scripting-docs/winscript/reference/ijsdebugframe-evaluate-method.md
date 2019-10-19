---
title: 'IJsDebugFrame:: Evaluate – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 6227b97c1fd5fae32db3e13ef72751726c36b043
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573501"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate – metoda
Vyhodnotit výraz v kontextu tohoto rámce zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pExpressionText`  
 pro Výraz, který se má vyhodnotit  
  
 `ppDebugProperty`  
 mimo Objekt reprezentující prohlížeč vlastností.  
  
 `pError`  
 mimo Chybová zpráva, pokud dojde k chybě.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Vrátí následující: S_OK: vyhodnocení je úspěšné, * ppDebugProperty obsahuje výsledek vyhodnocení. S_FALSE: vyhodnocení vyvolá chybu (nebo operace vyhodnocení není podporována), \*pError obsahuje chybovou zprávu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebugFrame – rozhraní](../../winscript/reference/ijsdebugframe-interface.md)