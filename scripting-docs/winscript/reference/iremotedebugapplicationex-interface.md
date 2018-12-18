---
title: Iremotedebugapplicationex – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3360cea0d1649348a795356ad827b32b6f8ebc19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794973"
---
# <a name="iremotedebugapplicationex-interface"></a>IRemoteDebugApplicationEx – rozhraní
Představuje běžící aplikaci. Nemusí se tak, aby odpovídaly procesu operačního systému. Ladicí program obvykle cílí aplikace pro ladění. Správce ladění procesu obvykle implementuje objekt aplikace.  
  
 Kromě metod zděděno z `IUnknown`, `IRemoteDebugApplicationEx` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Vrátí Identifikátor procesu pro hostitelskou aplikaci.|  
|GetHostMachineName|Vrátí název počítače, který hostitelskou aplikaci běží na.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Nastavuje jazyk pro lokalizaci ladicí program.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Ladicí program v režimu krokování vynutí.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Odvolá příkaz break.|  
|SetProxyBlanketAndAddRef|Aktualizuje informace o zabezpečení COM na proxy server pro objekt ladicí program k zajištění kompatibility s vzdáleného ladění z operačního systému Windows 95.|  
|ReleaseFromSetProxyBlanket|Addref – vydání z SetProxyBlanketAndAddRef.|