---
title: 'IDebugDocumentText –:: GetContextOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetContextOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetContextOfPosition
ms.assetid: 86560853-d9b1-499a-a1b5-ea06aa1f1f5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6a35a85a6e4761e1bd0db67caafd0913e7e28a3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572142"
---
# <a name="idebugdocumenttextgetcontextofposition"></a>IDebugDocumentText::GetContextOfPosition
Vytvoří objekt kontextu dokumentu odpovídající zadanému rozsahu pozice znaku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetContextOfPosition(  
   ULONG                    cCharacterPosition,  
   ULONG                    cNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cCharacterPosition`  
 pro Počáteční umístění rozsahu pozice znaku  
  
 `cNumChars`  
 pro Počet znaků v rozsahu.  
  
 `ppsc`  
 mimo Objekt kontextu dokumentu, který odpovídá zadanému rozsahu pozice znaku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří objekt kontextu dokumentu odpovídající zadanému rozsahu pozice znaku.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugDocumentText – rozhraní](../../winscript/reference/idebugdocumenttext-interface.md)