---
title: IDebugPortSupplier2:RemovePort | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::RemovePort
helpviewer_keywords:
- IDebugPortSupplier2::RemovePort
ms.assetid: f5c1fbf2-9084-46f2-a682-7db963928df2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9a23301395fe875efe66936d737d9b2bad0accb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724528"
---
# <a name="idebugportsupplier2removeport"></a>IDebugPortSupplier2::RemovePort
Odebere port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT RemovePort( 
   IDebugPort2* pPort
);
```

```csharp
int RemovePort( 
   IDebugPort2 pPort
);
```

## <a name="parameters"></a>Parametry
`pPort`\
[v] [Objekt IDebugPort2,](../../../extensibility/debugger/reference/idebugport2.md) který představuje port, který má být odebrán.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda odebere port z interního seznamu aktivních portů dodavatele portu.

## <a name="see-also"></a>Viz také
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
