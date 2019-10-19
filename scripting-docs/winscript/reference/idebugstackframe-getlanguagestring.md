---
title: 'Idebugstackframe –:: GetLanguageString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetLanguageString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83abb038cd8bc018d84cd0c5ddd2a413f8a02248
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576759"
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
Vrátí krátký nebo dlouhý textový popis jazyka.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fLong`  
 pro Příznak, kde `TRUE` vrátí dlouhý popis a `FALSE` vrátí krátký popis.  
  
 `pbstrLanguage`  
 mimo Popis jazyka  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je například `fLong` `FALSE`, tato metoda poskytuje pouze název jazyka asociovaného s rámcem zásobníku. Pokud je `fLong` `TRUE`, tato metoda může poskytovat úplný popis produktu.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugStackFrame – rozhraní](../../winscript/reference/idebugstackframe-interface.md)