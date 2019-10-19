---
title: 'Iapplicationdebugger –:: Close | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onClose
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onClose
ms.assetid: f3d6ca9f-6697-4d02-9d1a-16e3859bf282
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e31b2a77effc729f0e7df1e36116ee554446093
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577877"
---
# <a name="iapplicationdebuggeronclose"></a>IApplicationDebugger::onClose
Zpracovává událost zavření aplikace ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onClose();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je volána, když je volána `IDebugApplication::Close`.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iapplicationdebugger –](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)