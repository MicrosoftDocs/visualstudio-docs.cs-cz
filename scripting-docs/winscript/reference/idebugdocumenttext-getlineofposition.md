---
title: 'IDebugDocumentText –:: GetLineOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetLineOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetLineOfPosition
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8ce32e46c42ee864a88e169a79539efb8b05633
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572123"
---
# <a name="idebugdocumenttextgetlineofposition"></a>IDebugDocumentText::GetLineOfPosition
Vrátí číslo řádku a volitelně posun znaku v rámci řádku, který odpovídá dané pozici znaku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cCharacterPosition`  
 pro Počáteční umístění rozsahu pozice znaku  
  
 `pcLineNumber`  
 mimo Číslo řádku v rozsahu.  
  
 `pcCharacterOffsetInLine`  
 [in, out] Posun znaku rozsahu v rámci řádku `pcLineNumber`. Pokud je tento parametr `NULL`, metoda nevrátí hodnotu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí číslo řádku a volitelně posun znaku v řádku, který odpovídá dané pozici znaku.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugDocumentText – rozhraní](../../winscript/reference/idebugdocumenttext-interface.md)