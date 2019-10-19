---
title: 'Iactivescriptsitedebug –:: GetDocumentContextFromPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetDocumentContextFromPosition
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61bc36b98fee31ced1f3e8e00d084b5dabcd2124
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570169"
---
# <a name="iactivescriptsitedebuggetdocumentcontextfromposition"></a>IActiveScriptSiteDebug::GetDocumentContextFromPosition
Používá se v jazykovém modulu k delegování `IDebugCodeContext::GetSourceContext`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSourceContext`  
 pro Zdrojový obsah, jak je uveden `ParseScriptText` nebo `AddScriptlet`.  
  
 `uCharacterOffset`  
 pro Posun znaku vzhledem k začátku bloku skriptu nebo skriptletu.  
  
 `uNumChars`  
 pro Počet znaků v tomto kontextu.  
  
 `ppsc`  
 mimo Kontext dokumentu odpovídající tomuto rozsahu pozice znaků.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Jazykové moduly používají tuto metodu k delegování `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptSiteDebug – rozhraní](../../winscript/reference/iactivescriptsitedebug-interface.md)