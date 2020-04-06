---
title: IDebugFirewallConfigurationCallback2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 635771fc87326b28566058a43d4922b131ae1975
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728709"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Povolí ladicí modul, který používá [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] DCOM požádat uživatelské ho uživatelského zařízení, aby se ujistil, že brána firewall nebude blokovat vzdálené ladění.

## <a name="syntax"></a>Syntaxe

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Implementována objektem portu správce ladění relace.

## <a name="methods"></a>Metody
 V následující tabulce jsou `IDebugFirewallConfigurationCallback2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Požaduje, aby brána firewall neblokovala vzdálené ladění.|

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
