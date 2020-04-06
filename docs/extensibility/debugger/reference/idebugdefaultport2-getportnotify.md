---
title: IDebugDefaultPort2::GetPortNotify | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 670dd128e6962c1e1d12f81eea03f9759fa56621
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732413"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Tato metoda získá rozhraní [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) pro tento port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Parametry
`ppPortNotify`\
[out] Objekt [IDebugPortNotify2.](../../../extensibility/debugger/reference/idebugportnotify2.md)

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Za normálních okolností `QueryInterface` je metoda volána na objekt uimplementující rozhraní [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) získat rozhraní [IDebugPortNotify2.](../../../extensibility/debugger/reference/idebugportnotify2.md) Existují však okolnosti, ve kterých je implementováno požadované rozhraní na jiný objekt. Tato metoda skryje tyto `IDebugPortNotify2` okolnosti a vrátí rozhraní z nejvhodnější objekt.

## <a name="see-also"></a>Viz také
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
