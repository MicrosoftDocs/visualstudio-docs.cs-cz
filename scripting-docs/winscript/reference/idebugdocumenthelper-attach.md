---
title: 'Idebugdocumenthelper –:: Attach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Attach
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3400a5bf6cd3e4a9726fdf4b2f20bbf43b9fc989
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577036"
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
Přidá tento dokument do stromu dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pddhParent`  
 pro Strom dokumentů, do kterého bude tento dokument přidán. Může mít hodnotu NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda přidá tento dokument do stromu dokumentu pomocí `pddhParent` jako nadřazeného objektu. Pokud je `pddhParent` `NULL`, bude dokument nejvyšší úrovně.  
  
## <a name="see-also"></a>Viz také:  
 [Idebugdocumenthelper –::D etach](../../winscript/reference/idebugdocumenthelper-detach.md)    
 [IDebugDocumentHelper – rozhraní](../../winscript/reference/idebugdocumenthelper-interface.md)