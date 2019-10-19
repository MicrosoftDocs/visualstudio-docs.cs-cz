---
title: 'IDebugSyncOperation –:: InProgressAbort | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 40974c738c071e52648297ac90a0ab89d9681435
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576672"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Zruší probíhající operaci v jiném vlákně.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_NOTIMPL`|Operaci nelze zrušit.|  
|`E_ABORT`|Operaci nešlo dokončit.|  
  
## <a name="remarks"></a>Poznámky  
 Správce procesu ladění volá tuto metodu z vlákna ladicího programu pro zrušení operace, která probíhá v jiném vlákně.  
  
 Pokud metoda `InProgressAbort` nemůže operaci dokončit, vrátí `E_ABORT` co nejrychleji. Tato metoda může vracet `E_NOTIMPL`, pokud operaci nelze zrušit.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugSyncOperation – rozhraní](../../winscript/reference/idebugsyncoperation-interface.md)