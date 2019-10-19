---
title: 'Idebugstackframesnifferex –:: EnumStackFramesEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a4062e7c0a9b3a82578daffa2ab7ef7e9ba614d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576709"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Vrátí enumerátor rámců zásobníku pro aktuální vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSpMin`  
 pro Dolní limit adres pro vytváření výčtu rámců zásobníku.  
  
 `ppedsf`  
 mimo Enumerátor rámců zásobníku pro aktuální vlákno.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Enumerátor rámce zásobníku vrátí snímky začínající v horní části zásobníku s naposledy přesunutým snímkem. Enumerátor obsahuje pouze rámce zásobníku s adresami, které jsou větší nebo rovny `dwSpMin`.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugStackFrameSnifferEx – rozhraní](../../winscript/reference/idebugstackframesnifferex-interface.md)