---
title: 'Idebugdocumenthelper –:: BringDocumentToTop | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.BringDocumentToTop
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::BringDocumentToTop
ms.assetid: 91bdbb05-6f79-4b07-a707-838cb75a770f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b8afe5c03153517fe8923141ca251e6390cd782
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577009"
---
# <a name="idebugdocumenthelperbringdocumenttotop"></a>IDebugDocumentHelper::BringDocumentToTop
Přinese tento dokument na začátek v uživatelském rozhraní ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT BringDocumentToTop();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda spustí ladicí program, pokud ještě není spuštěn.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugDocumentHelper – rozhraní](../../winscript/reference/idebugdocumenthelper-interface.md)