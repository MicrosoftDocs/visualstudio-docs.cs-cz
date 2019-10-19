---
title: Rozhraní Imachinedebugmanager – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManager interface
ms.assetid: 0b7133bb-5a52-4036-b4db-d69260790db7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d491b03ba04d346e3a14a08d5e2b6b9d34c7d97
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573924"
---
# <a name="imachinedebugmanager-interface"></a>IMachineDebugManager – rozhraní
Primární rozhraní pro správce ladění počítače. Toto rozhraní je podobné rozhraní `IMachineDebugManagerCookie`.  
  
 Kromě metod zděděných z `IUnknown` rozhraní `IMachineDebugManager` zpřístupňuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IMachineDebugManager::AddApplication](../../winscript/reference/imachinedebugmanager-addapplication.md)|Přidá aplikaci do seznamu běžící aplikace.|  
|[IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)|Odebere aplikaci ze seznamu běžící aplikace.|  
|[IMachineDebugManager::EnumApplications](../../winscript/reference/imachinedebugmanager-enumapplications.md)|Vrátí enumerátor pro aktuální seznam spuštěných aplikací.|  
  
## <a name="see-also"></a>Viz také:  
 [IMachineDebugManagerCookie – rozhraní](../../winscript/reference/imachinedebugmanagercookie-interface.md)