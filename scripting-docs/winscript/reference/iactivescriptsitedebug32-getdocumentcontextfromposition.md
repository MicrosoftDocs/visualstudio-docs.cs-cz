---
title: 'IActiveScriptSiteDebug32:: GetDocumentContextFromPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 7acbe2a5741fa94ac42470a85803d1720e0a8fa1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574851"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
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
 [IActiveScriptSiteDebug32 – rozhraní](../../winscript/reference/iactivescriptsitedebug32-interface.md)