---
title: Ijsdebugframe::getstackrange – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cce4d4542f4f76657475636ad6d8e430e1909181
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794514"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange – metoda
Vrátí absolutní adresu rozsahu logické rámce zásobníku JavaScript.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStart`  
 [out] Většina ukazatel zásobníku rámečku dolů.  
  
 `pEnd`  
 [out] Horní většina ukazatel skládání rámečku.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je užitečná pro piecing společně trasování prokládaná zásobníku shromážděná z více moduly runtime. Start a end ukazatel zásobníku může zahrnovat víc rámce zásobníku fyzického počítače (pro interpretovaný rámce JavaScript runtime). Spustit > ukončení s růstem zásobníku od velmi nízkou adresu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Ijsdebugframe – metoda](../../winscript/reference/ijsdebugframe-interface.md)