---
title: 'IDebugDocumentTextExternalAuthor –:: NotifyChanged | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.NotifyChanged
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::NotifyChanged
ms.assetid: f0de7984-3a15-49e2-bd29-f768f34d2a4d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad02db80bd24a8a5ba96abaa61e85be9d69e553e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575946"
---
# <a name="idebugdocumenttextexternalauthornotifychanged"></a>IDebugDocumentTextExternalAuthor::NotifyChanged
Upozorňuje hostitele, že se změnil zdroj dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT NotifyChanged();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je volána externím editorem po úpravě a uložení dokumentu ladicího programu založeného na souboru pro oznamování hostitele, že došlo ke změně zdroje dokumentu. Hostitel pak aktualizuje dokument ze zdrojového souboru.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugDocumentTextExternalAuthor – rozhraní](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)