---
title: IDebugDocumentText::GetSize | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3152150c46793a71ec7a46b6ab2097efa06f6fc8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794274"
---
# <a name="idebugdocumenttextgetsize"></a>IDebugDocumentText::GetSize
Vrátí počet řádků a počet znaků v dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcNumLines`  
 [out] Počet řádků v dokumentu. Pokud tento parametr hodnotu NULL, metoda nevrací hodnotu.  
  
 `pcNumChars`  
 [out] Počet znaků v dokumentu. Pokud tento parametr hodnotu NULL, metoda nevrací hodnotu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí počet řádků a počet znaků v dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Idebugdocumenttext – rozhraní](../../winscript/reference/idebugdocumenttext-interface.md)