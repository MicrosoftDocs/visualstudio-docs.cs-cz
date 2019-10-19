---
title: 'Imachinedebugmanager –:: AddApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::AddApplication
ms.assetid: 7cd591b6-718c-4e77-acb7-a6dd147ddf57
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ff617ac96c0eb3498b796d4f7fe49f95e1cc96
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573958"
---
# <a name="imachinedebugmanageraddapplication"></a>IMachineDebugManager::AddApplication
Přidá aplikaci do seznamu běžící aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pda`  
 pro Aplikace do seznamu běžící aplikace  
  
 `pdwAppCookie`  
 mimo Soubor cookie, který se používá k odebrání aplikace ze Správce ladění počítače.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je volána správcem ladění procesu vždy, když je volána `IProcessDebugManager::AddApplication`.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní imachinedebugmanager –](../../winscript/reference/imachinedebugmanager-interface.md)  
 [Imachinedebugmanager –:: RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)    
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)