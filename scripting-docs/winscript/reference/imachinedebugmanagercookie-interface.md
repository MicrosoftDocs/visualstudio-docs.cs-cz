---
title: Imachinedebugmanagercookie – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a03b959a7eb09f3b85530bbba07d1d2dc7f8948a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795039"
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie – rozhraní
Podobně jako `IMachineDebugManager` rozhraní, `IMachineDebugManagerCookie` rozhraní podporuje ladění.  
  
 Toto rozhraní (spolu s `IDebugCookie` rozhraní) povolí spuštění v ladicí proces skript bez nutnosti, že tyto skripty udržování přehledu o ladicího programu skriptů.  
  
 Ladicí program skript volá `IDebugCookie::SetDebugCookie` metoda na v procesu ladění Manager (PDM). Poté, PDM odešle tento soubor cookie spolu s žádnou žádostí, které chcete přidat nebo odebrat aplikace skriptu do nebo z počítače ladění Manager (MDM), pomocí metody `IMachineDebugManagerCookie` rozhraní. MDM poté oznámí všechny ladicí program změny, s výjimkou takový, který má tento soubor cookie.  
  
 Kromě metod zděděno z `IUnknown`, `IMachineDebugManagerCookie` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Přidá aplikaci do spuštění seznam aplikací.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Vrátí enumerátor aktuálního seznamu spuštěných aplikací.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Odebere aplikaci ze spuštění seznam aplikací.|  
  
## <a name="see-also"></a>Viz také  
 [Imachinedebugmanager – rozhraní](../../winscript/reference/imachinedebugmanager-interface.md)   
 [Idebugcookie – rozhraní](../../winscript/reference/idebugcookie-interface.md)