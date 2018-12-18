---
title: IDebugDocumentTextEvents::onDestroy | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onDestroy
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onDestroy
ms.assetid: 1b7eb341-6bad-403f-9821-19112f8732f3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd63128fa5222d829b9f676614ffeef83922db27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794175"
---
# <a name="idebugdocumenttexteventsondestroy"></a>IDebugDocumentTextEvents::onDestroy
Určuje, že zdrojový dokument byl zničen a již není platný.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT onDestroy();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda určuje, že zdrojový dokument byl zničen a již není platný.  
  
## <a name="see-also"></a>Viz také  
 [Idebugdocumenttextevents – rozhraní](../../winscript/reference/idebugdocumenttextevents-interface.md)