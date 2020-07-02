---
title: 'IActiveScriptSiteDebug32:: GetDocumentContextFromPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b43b16f46cc62b6c70460d79c194b5e0d2cfede0
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835274"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
K delegování používá jazykový modul `IDebugCodeContext::GetSourceContext` .  
  
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
 pro Zdrojový obsah, který je k dispozici pro `ParseScriptText` nebo `AddScriptlet` .  
  
 `uCharacterOffset`  
 pro Posun znaku vzhledem k začátku bloku skriptu nebo skriptletu.  
  
 `uNumChars`  
 pro Počet znaků v tomto kontextu.  
  
 `ppsc`  
 mimo Kontext dokumentu odpovídající tomuto rozsahu pozice znaků.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrátí `HRESULT` . Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Jazykové moduly používají tuto metodu k delegování `IDebugCodeContext::GetSourceContext` .  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptSiteDebug32 – rozhraní](../../winscript/reference/iactivescriptsitedebug32-interface.md)