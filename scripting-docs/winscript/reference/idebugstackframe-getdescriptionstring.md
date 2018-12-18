---
title: IDebugStackFrame::GetDescriptionString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: cdc77aa2ef2f9d7c95b0b82d5195a6a73524f055
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794964"
---
# <a name="idebugstackframegetdescriptionstring"></a>IDebugStackFrame::GetDescriptionString
Vrátí kratší nebo dlouho textový popis rámce zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fLong`  
 [v] Příznak, kde `TRUE` vrátí dlouhý popis a `FALSE` vrátí krátký popis.  
  
 `pbstrDescription`  
 [out] Popis rámce zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Obvykle Pokud `fLong` je `FALSE`, tato metoda poskytuje pouze název funkce související s rámce zásobníku. Když `fLong` je `TRUE`, tato metoda může taky poskytnout tyto parametry a další relevantní informace.  
  
## <a name="see-also"></a>Viz také  
 [Idebugstackframe – rozhraní](../../winscript/reference/idebugstackframe-interface.md)