---
title: 'IProcessDebugManager –:: CreateDebugDocumentHelper | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.CreateDebugDocumentHelper
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::CreateDebugDocumentHelper
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a009fa5174ab897116c02b91e376e2dc41d67600
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577096"
---
# <a name="iprocessdebugmanagercreatedebugdocumenthelper"></a>IProcessDebugManager::CreateDebugDocumentHelper
Vytvoří novou nápovědu k dokumentu ladění pro tuto aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `punkOuter`  
 pro Pokud je vrácený objekt agregovaný, `punkOuter` je ukazatel rozhraní na řídící `IUnknown`. V opačném případě se jedná o ukazatel s hodnotou null.  
  
 `pddh`  
 mimo Objekt pomocníka dokumentu ladění pro tuto aplikaci.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří novou nápovědu k dokumentu ladění pro tuto aplikaci.  
  
## <a name="see-also"></a>Viz také:  
 [IProcessDebugManager – rozhraní](../../winscript/reference/iprocessdebugmanager-interface.md)