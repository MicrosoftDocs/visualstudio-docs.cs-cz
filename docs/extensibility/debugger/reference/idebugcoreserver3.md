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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ab605db6a49b8b7cc9893692ff1bb9e6da15171f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088143"
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
