---
description: Toto rozhraní poskytuje přístup k informacím o serveru, na kterém je spuštěný proces.
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1328a97742a4672cdc71805c4c674d66fe05e817
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154610"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Toto rozhraní poskytuje přístup k informacím o serveru, na kterém je spuštěný proces.

## <a name="syntax"></a>Syntax

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Visual Studio implementuje toto rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 K získání tohoto rozhraní z rozhraní [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) použijte [QueryInterface](/cpp/atl/queryinterface) . Volání metody [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) může také vrátit toto rozhraní. Toto rozhraní se nejčastěji používá vlastním dodavatelem portu ke spouštění programů na serveru (místní nebo vzdálené).

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod v rozhraní [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Načte název serveru.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Načte popisnou verzi názvu serveru.|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Oznamuje konkrétním ladicím modulům, aby se při spuštění těchto procesů automaticky připojil k procesům.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Načte konkrétní kód chyby, pokud se automatické připojení nezdařilo.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Vytvoří instanci ladicího stroje na serveru.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Načte příznak označující, zda je server ve stejném počítači jako volající.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Načte hodnotu, která označuje protokol, který se používá ke komunikaci se serverem.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Zakáže všechna nastavení automatického připojení pro všechny moduly ladění, které tento server ví.|

## <a name="remarks"></a>Poznámky
 Vlastní dodavatel portu obdrží rozhraní [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) pro volání [události](../../../extensibility/debugger/reference/idebugportevents2-event.md). `IDebugCoreServer3`Rozhraní lze získat z tohoto rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
