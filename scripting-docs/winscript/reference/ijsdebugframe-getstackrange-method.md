---
title: 'IJsDebugFrame:: Getstackrange – – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d1ac3cbee9d16296632477f4128ec36370ab0d4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574044"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange – metoda
Vrátí absolutní rozsah adres rámce logického zásobníku JavaScriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStart`  
 mimo Dolní největší ukazatel zásobníku rámečku.  
  
 `pEnd`  
 mimo Horní největší ukazatel stacku rámečku.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je užitečná pro piecing společně prokládaných trasování zásobníku shromážděných z více modulů runtime. Koncový bod zásobníku může zahrnovat několik snímků zásobníku fyzického počítače (pro interpretované snímky běhového prostředí JavaScript). Začněte > končit, protože zásobník roste od vysoké po nízkou adresu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebugFrame – rozhraní](../../winscript/reference/ijsdebugframe-interface.md)