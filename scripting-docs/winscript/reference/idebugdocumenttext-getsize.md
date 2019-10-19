---
title: 'IDebugDocumentText –:: GetSize | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetSize
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetSize
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef6f75b396dddec80fb2ae89c71f8579ce3c29b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572090"
---
# <a name="idebugdocumenttextgetsize"></a>IDebugDocumentText::GetSize
Vrátí počet řádků v dokumentu a počet znaků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcNumLines`  
 mimo Počet řádků v dokumentu Pokud má tento parametr hodnotu NULL, metoda nevrátí hodnotu.  
  
 `pcNumChars`  
 mimo Počet znaků v dokumentu. Pokud má tento parametr hodnotu NULL, metoda nevrátí hodnotu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí počet řádků a počet znaků v dokumentu.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugDocumentText – rozhraní](../../winscript/reference/idebugdocumenttext-interface.md)