---
title: Ijsdebugframe::getdocumentpositionwithname – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 49afb5903e190280d226a24b22dc389041861c52
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794568"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName – metoda
Vrátí aktuální pozici tento rámce zásobníku v tomto dokumentu úrovni uživatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDocumentName`  
 [out] Pro statické skripty, adresu URL dokumentu. Pro dynamické skripty je vrácen název obsahující typ skriptu (například eval kódu, funkce kódu atd.).  
  
 `pLine`  
 [out] pozice 1 na základě řádku v tomto dokumentu.  
  
 `pColumn`  
 [out] pozice 1 na základě řádku v tomto dokumentu.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Ijsdebugframe – metoda](../../winscript/reference/ijsdebugframe-interface.md)