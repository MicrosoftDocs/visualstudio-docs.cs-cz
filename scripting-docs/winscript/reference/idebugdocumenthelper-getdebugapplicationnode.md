---
title: IDebugDocumentHelper::GetDebugApplicationNode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.GetDebugApplicationNode
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::GetDebugApplicationNode
ms.assetid: ecd18803-beb4-4ac2-9702-cc9e8a12c395
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27d1fb09698cffa4826ab35b36e3ae315a12ba74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793965"
---
# <a name="idebugdocumenthelpergetdebugapplicationnode"></a>IDebugDocumentHelper::GetDebugApplicationNode
Vrátí uzlu ladění aplikace odpovídající do tohoto dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDebugApplicationNode(  
   IDebugApplicationNode**  ppdan  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppdan`  
 [out] Ladění aplikace uzlu odpovídající do tohoto dokumentu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Vrátí uzlu ladění aplikace odpovídající do tohoto dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Idebugdocumenthelper – rozhraní](../../winscript/reference/idebugdocumenthelper-interface.md)