---
title: 'Idebugstackframe –:: GetDescriptionString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetDescriptionString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetDescriptionString
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7eb29574d240a02073721046cec65bdf483b3eb0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576750"
---
# <a name="idebugstackframegetdescriptionstring"></a>IDebugStackFrame::GetDescriptionString
Vrátí krátký nebo dlouhý textový popis rámce zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fLong`  
 pro Příznak, kde `TRUE` vrátí dlouhý popis a `FALSE` vrátí krátký popis.  
  
 `pbstrDescription`  
 mimo Popis rámce zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je například `fLong` `FALSE`, tato metoda poskytuje pouze název funkce asociované s rámcem zásobníku. Pokud je `fLong` `TRUE`, může tato metoda také poskytnout parametry funkce a další relevantní informace.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugStackFrame – rozhraní](../../winscript/reference/idebugstackframe-interface.md)