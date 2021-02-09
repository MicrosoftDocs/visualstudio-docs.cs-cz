---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d25068b71689ffbc9e472addbd6ca3663db267c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891277"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Určuje protokol, který se používá ke komunikaci mezi ladicím serverem a ladicím balíčkem (DE).

## <a name="syntax"></a>Syntax

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Pole
`CONNECTION_NONE`\
Na serveru se neudělalo žádné připojení.

`CONNECTION_UNKNOWN`\
Připojení bylo vytvořeno, ale je neznámého typu.

`CONNECTION_LOCAL`\
Připojení je místní server.

`CONNECTION_PIPE`\
Připojení je prostřednictvím pojmenovaného kanálu.

`CONNECTION_TCPIP`\
Připojení používá protokol TCP/IP.

`CONNECTION_HTTP`\
Připojení používá protokol HTTP (prostřednictvím webového serveru).

`CONNECTION_OTHER`\
Byl vytvořen nějaký jiný typ připojení (Tato hodnota se aktuálně nepoužívá).

## <a name="remarks"></a>Poznámky
Tyto hodnoty jsou vráceny metodou [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
