---
title: IDebugSyncOperation::InProgressAbort | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1df0b0ca1d775d4d99e1da5f88a207bd4f78f99b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794631"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Zruší probíhá operace na jiné vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_NOTIMPL`|Operaci nelze zrušit.|  
|`E_ABORT`|Operaci nelze dokončit.|  
  
## <a name="remarks"></a>Poznámky  
 Správce ladění proces volá tuto metodu z vlákna ladicí program zrušit operaci, která je v průběhu v jiné vlákno.  
  
 Pokud `InProgressAbort` metoda nemůže dokončit operaci, vrátí `E_ABORT` co nejdříve. Tato metoda může vrátit `E_NOTIMPL` Pokud operaci nelze zrušit.  
  
## <a name="see-also"></a>Viz také  
 [Idebugsyncoperation – rozhraní](../../winscript/reference/idebugsyncoperation-interface.md)