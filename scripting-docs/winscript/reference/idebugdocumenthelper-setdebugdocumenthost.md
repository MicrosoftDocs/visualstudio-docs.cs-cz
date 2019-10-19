---
title: 'Idebugdocumenthelper –:: SetDebugDocumentHost | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDebugDocumentHost
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDebugDocumentHost
ms.assetid: b26a03c3-8a3f-47b0-b916-4c65d5500f10
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b32d14f3a7d65bee7bdb587a35dfe05bb06f5e1e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574646"
---
# <a name="idebugdocumenthelpersetdebugdocumenthost"></a>IDebugDocumentHelper::SetDebugDocumentHost
Nastaví `IDebugDocumentHost` pro tento dokument.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetDebugDocumentHost(  
   IDebugDocumentHost*  pddh  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pddh`  
 pro Hostitel dokumentu ladění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `IDebugDocumentHost` se používá pro barevné zvýrazňování syntaxe inteligentního hostitele, načítání odloženého textu a vrácení řídicích objektů pro nově vytvořené kontexty dokumentů.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní idebugdocumenthelper –](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHost – rozhraní](../../winscript/reference/idebugdocumenthost-interface.md)