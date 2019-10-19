---
title: 'Idebugdocumenthelper –:: AddUnicodeText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddUnicodeText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddUnicodeText
ms.assetid: f4ef648e-c55d-4ef0-8df3-e808b798d3b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5820c380c92f2c3cd95763b440d5f9755db3e717
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577058"
---
# <a name="idebugdocumenthelperaddunicodetext"></a>IDebugDocumentHelper::AddUnicodeText
Připojí řetězec Unicode na konec tohoto dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddUnicodeText(  
   LPCOLESTR  pszText  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszText`  
 pro Ukazatel na řetězec zakončený hodnotou null obsahující text.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Metoda nemohla přidat znaky.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda generuje oznámení `IDebugDocumentTextEvents`.  
  
> [!NOTE]
> Pokud je tato metoda volána po volání `AddDeferredText`, je vrácena `E_FAIL`.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní idebugdocumenthelper –](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [Idebugdocumenthelper –:: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [IDebugDocumentTextEvents – rozhraní](../../winscript/reference/idebugdocumenttextevents-interface.md)