---
title: 'Idebugdocumenthost –:: OnCreateDocumentContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.OnCreateDocumentContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::OnCreateDocumentContext
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fdfa64f66288cba47dec7c498db15238e55f954
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569120"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
Upozorňuje hostitele na vytvoření nového kontextu dokumentu a umožňuje hostiteli volitelně vrátit řízení neznámé pro nový kontext.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppunkOuter`  
 mimo Objekt, který řídí nový kontext.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_NOTIMPL`|Hostitel neposkytuje řídicí objekt.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda umožňuje hostiteli přidat novou funkci kontextů dokumentů poskytovaných pomocníkem. Tato metoda může vracet **E_NOTIMPL** nebo vnější objekt null. v takovém případě volající zodpovídá za vytvoření kontextu.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugDocumentHost – rozhraní](../../winscript/reference/idebugdocumenthost-interface.md)