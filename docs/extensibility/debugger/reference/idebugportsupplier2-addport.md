---
description: Přidá port.
title: 'IDebugPortSupplier2:: AddPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c2b9c4c7c5378670c87926e76d185d54448a244
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072192"
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
pro Objekt [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) , který popisuje port, který má být přidán.

`ppPort`\
mimo Vrátí objekt [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , který představuje port.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda ve skutečnosti vytvoří požadovaný port a zároveň ho přidá do interního seznamu aktivních portů dodavatele portu. Metoda [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) může být volána jako první, aby se předešlo možným prodlevám při časově náročném času.

## <a name="see-also"></a>Viz také
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
