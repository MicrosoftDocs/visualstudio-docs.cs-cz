---
title: 'Idebugdocumenthelper –:: AddDBCSText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDBCSText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDBCSText
ms.assetid: 5e5011b2-bbb4-491b-9a11-eb2846be44aa
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71d0b7816a0b8801c5fb4eaab9cf7808a3f3bbfe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577073"
---
# <a name="idebugdocumenthelperadddbcstext"></a>IDebugDocumentHelper::AddDBCSText
Připojí řetězec DBCS na konec tohoto dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddDBCSText(  
   LPCSTR  pszText  
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
> Pokud je tato metoda volána po volání `IDebugDocumentHelper::AddDeferredText`, je vrácena `E_FAIL`.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní idebugdocumenthelper –](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [Idebugdocumenthelper –:: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [IDebugDocumentTextEvents – rozhraní](../../winscript/reference/idebugdocumenttextevents-interface.md)