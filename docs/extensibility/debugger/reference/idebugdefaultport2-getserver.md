---
description: Tato metoda získá rozhraní serveru, na kterém je tento port zapnutý.
title: 'IDebugDefaultPort2:: GetServer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e26356b01a04d736f9131c2762c897b6ce258997
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077457"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Tato metoda získá rozhraní serveru, na kterém je tento port zapnutý.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetServer(
   IDebugCoreServer3** ppServer
);
```

```csharp
int GetServer(
   out IDebugCoreServer3 ppServer
);
```

## <a name="parameters"></a>Parametry
`ppServer`\
mimo Vrátí objekt implementující rozhraní [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) je implementováno pomocí sady Visual Studio a představuje server, na kterém je umístěn port.

## <a name="see-also"></a>Viz také
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
