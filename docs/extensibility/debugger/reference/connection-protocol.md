---
title: CONNECTION_PROTOCOL | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ac287462149a20f52a1affdeab7fa6b8333711
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737647"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Označuje protokol používaný ke komunikaci mezi ladicím serverem a ladicím balíčkem (DE).

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Fields (Pole)
`CONNECTION_NONE`\
K serveru nebylo provedeno žádné připojení.

`CONNECTION_UNKNOWN`\
Bylo nastojeno připojení, ale je neznámého typu.

`CONNECTION_LOCAL`\
Připojení je k místnímu serveru.

`CONNECTION_PIPE`\
Připojení je prostřednictvím pojmenovaného kanálu.

`CONNECTION_TCPIP`\
Připojení používá protokol TCP/IP.

`CONNECTION_HTTP`\
Připojení používá protokol HTTP (prostřednictvím webového serveru).

`CONNECTION_OTHER`\
Byl navázán jiný typ připojení (tato hodnota není aktuálně používána).

## <a name="remarks"></a>Poznámky
Tyto hodnoty jsou vráceny z [Metody GetConnectionProtocol.](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
