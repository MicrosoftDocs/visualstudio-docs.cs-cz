---
description: Umožňuje ladicímu stroji, který používá model DCOM k vyžádání uživatelského rozhraní sady Visual Studio, aby se zajistilo, že brána firewall neblokuje vzdálené ladění.
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf8659a1bc4af55a9809a3c85548b971a7193b26
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166525"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Umožňuje ladicímu stroji, který používá model DCOM k vyžádání [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uživatelského rozhraní, aby se zajistilo, že brána firewall nebude blokovat vzdálené ladění.

## <a name="syntax"></a>Syntax

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Implementováno objektem portu Správce ladění relace.

## <a name="methods"></a>Metody
 V následující tabulce jsou uvedeny metody `IDebugFirewallConfigurationCallback2` .

|Metoda|Popis|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Požaduje, aby brána firewall neblokovala vzdálené ladění.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
