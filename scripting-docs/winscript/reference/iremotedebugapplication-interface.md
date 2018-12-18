---
title: Iremotedebugapplication – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea91afdc44b70a91846d7b1a3dc4c017c0c4c80e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795033"
---
# <a name="iremotedebugapplication-interface"></a>IRemoteDebugApplication – rozhraní
Představuje běžící aplikaci. Nemusí se tak, aby odpovídaly o proces operačního systému. Ladicí program obvykle cílí aplikace pro ladění. Správce ladění procesu obvykle implementuje objekt aplikace.  
  
 Kromě metod zděděno z `IUnknown`, `IRemoteDebugApplication` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Pokračuje v aplikaci, která je aktuálně v zarážky.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Způsobí, že aplikace pro přerušení ladicího při nejbližší příležitosti.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Ladicí program se připojí k této aplikaci.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Odpojí aktuální ladicí program z aplikace.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Vrátí aktuální ladicí program připojené k aplikaci.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Poskytuje mechanismus pro ladicí program IDE, spuštěná out-of-process do aplikace, k vytváření objektů v aplikačním procesu.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Určuje, zda je aplikace reaguje.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Zobrazí všechna vlákna známé jako přidružená k aplikaci.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Vrací název tohoto uzlu aplikace.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Vrátí uzlu aplikace, pod kterým jsou přidány všechny uzly, které jsou přidružené k aplikaci.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Vytvoří výčet kontexty globálním výrazu pro všechny jazyky, které jsou spuštěné v této aplikaci.|