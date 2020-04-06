---
title: IDebugCoreServer3 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d110e66e937249fdee34f424d4f68a9b914113d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732817"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Toto rozhraní poskytuje přístup k informacím o serveru, na který je proces spuštěn.

## <a name="syntax"></a>Syntaxe

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Visual Studio implementuje toto rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pomocí [rozhraní QueryInterface](/cpp/atl/queryinterface) získáte toto rozhraní z rozhraní [IDebugCoreServer2.](../../../extensibility/debugger/reference/idebugcoreserver2.md) Volání [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) můžete také vrátit toto rozhraní. Toto rozhraní používá nejčastěji dodavatel vlastního portu ke spuštění programů na serveru (místní nebo vzdálené).

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod v rozhraní [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Načte název serveru.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Načte popisnou verzi názvu serveru.|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Říká, že konkrétní ladicí motory se mají automaticky připojit k procesům při spuštění těchto procesů.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Načte konkrétní kód chyby při selhání automatického připojení.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Vytvoří instanci ladicího modulu na serveru.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Načte příznak označující, zda je server ve stejném počítači jako volající.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Načte hodnotu označující protokol používaný ke komunikaci se serverem.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Zakáže všechna nastavení automatického připojení pro všechny ladicí moduly, o kterých tento server ví.|

## <a name="remarks"></a>Poznámky
 Dodavatel vlastního portu obdrží rozhraní [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) při volání [události](../../../extensibility/debugger/reference/idebugportevents2-event.md). Rozhraní `IDebugCoreServer3` lze získat z tohoto rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
