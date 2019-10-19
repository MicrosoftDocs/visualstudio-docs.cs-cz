---
title: 'IJsDebugFrame:: Getdocumentpositionwithname – – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithName
apilocation:
- jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b818ca4dc1ec4402973026668972507861c86f22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575126"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName – metoda
Vrátí aktuální pozici tohoto rámce zásobníku v dokumentu na úrovni uživatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDocumentName`  
 mimo Pro statické skripty adresa URL dokumentu. Pro dynamické skripty je vrácen název obsahující typ skriptu (například kód pro vyhodnocení, kód funkce atd.).  
  
 `pLine`  
 [out] pozice řádku na 1 v dokumentu.  
  
 `pColumn`  
 [out] pozice řádku na 1 v dokumentu.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebugFrame – rozhraní](../../winscript/reference/ijsdebugframe-interface.md)