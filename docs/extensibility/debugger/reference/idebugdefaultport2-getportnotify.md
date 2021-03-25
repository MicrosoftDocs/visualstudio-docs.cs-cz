---
description: Tato metoda načte rozhraní IDebugPortNotify2 pro tento port.
title: 'IDebugDefaultPort2:: GetPortNotify | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ed43d96a7035dbd9e75a8e64a23e556997e087c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077470"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Tato metoda načte rozhraní [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) pro tento port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Parametry
`ppPortNotify`\
mimo Objekt [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Obvykle `QueryInterface` je metoda volána na objektu implementující rozhraní [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) pro získání rozhraní [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) . Existují však situace, kdy je požadované rozhraní implementováno na jiném objektu. Tato metoda skryje tyto okolnosti a vrátí `IDebugPortNotify2` rozhraní z nejvhodnějšího objektu.

## <a name="see-also"></a>Viz také
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
