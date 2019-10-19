---
title: Rozhraní Imachinedebugmanagercookie – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b39c286f389c99187b0f3250fc68af92ff5dcc8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573889"
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie – rozhraní
Podobně jako rozhraní `IMachineDebugManager` rozhraní `IMachineDebugManagerCookie` podporuje ladění souborů cookie.  
  
 Toto rozhraní (spolu s rozhraním `IDebugCookie`) umožňuje spouštění skriptů v procesu ladicího programu skriptu, aniž by vyžadovalo, aby ladicí program nadále sledoval tyto skripty.  
  
 Ladicí program skriptu volá metodu `IDebugCookie::SetDebugCookie` ve Správci ladění procesu (PDM). Pak PDM tento soubor cookie pošle spolu s jakoukoli žádostí o přidání nebo odebrání aplikace skriptu do nebo ze Správce ladění počítače (MDM) pomocí metod `IMachineDebugManagerCookie` rozhraní. MDM pak oznámí každému ladicímu programu změny, s výjimkou toho, který má tento soubor cookie.  
  
 Kromě metod zděděných z `IUnknown` rozhraní `IMachineDebugManagerCookie` zpřístupňuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Přidá aplikaci do seznamu běžící aplikace.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Vrátí enumerátor pro aktuální seznam spuštěných aplikací.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Odebere aplikaci ze seznamu běžící aplikace.|  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní imachinedebugmanager –](../../winscript/reference/imachinedebugmanager-interface.md)  
 [IDebugCookie – rozhraní](../../winscript/reference/idebugcookie-interface.md)