---
title: IDebugPortSupplier2:AddPort | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00954ceaa0ddd750a3d08e372d1edaa1905f01c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724734"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Přidá port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT AddPort( 
   IDebugPortRequest2* pRequest,
   IDebugPort2**       ppPort
);
```

```csharp
int AddPort( 
   IDebugPortRequest2 pRequest,
   out IDebugPort2    ppPort
);
```

## <a name="parameters"></a>Parametry
`pRequest`\
[v] [Objekt IDebugPortRequest2,](../../../extensibility/debugger/reference/idebugportrequest2.md) který popisuje port, který má být přidán.

`ppPort`\
[out] Vrátí objekt [IDebugPort2,](../../../extensibility/debugger/reference/idebugport2.md) který představuje port.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda ve skutečnosti vytvoří požadovaný port a také jej přidá do interního seznamu aktivních portů dodavatele portu. [Metoda CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) může být volána jako první, aby se zabránilo možným časově náročným zpožděním.

## <a name="see-also"></a>Viz také
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
