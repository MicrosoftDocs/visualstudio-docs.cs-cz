---
title: IDebugDocumentTextAuthor::ReplaceText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextAuthor.ReplaceText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextAuthor::ReplaceText
ms.assetid: f89304e6-5be0-45a5-947d-2c59c3c0a05e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aa7ef34d035ad89a096414c285b4f66a4f4fa1e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794163"
---
# <a name="idebugdocumenttextauthorreplacetext"></a>IDebugDocumentTextAuthor::ReplaceText
Nahradí text v dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ReplaceText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToReplace,  
   OLECHAR  pcharText[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cCharacterPosition`  
 [v] Spusťte umístění rozsahu znak nahradit.  
  
 `cNumToReplace`  
 [v] Počet znaků, který má nahradit.  
  
 `pcharText[]`  
 [v] Vyrovnávací paměť obsahující nové znaky k nahrazení původní znaků.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda nahradí text v dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Idebugdocumenttextauthor – rozhraní](../../winscript/reference/idebugdocumenttextauthor-interface.md)