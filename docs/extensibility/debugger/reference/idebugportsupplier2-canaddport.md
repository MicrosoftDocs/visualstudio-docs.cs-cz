---
description: Ověřuje, že dodavatel portu může přidávat nové porty.
title: 'IDebugPortSupplier2:: CanAddPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad704eda53807d344b23736d2d9b55e172c36468
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072205"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Ověřuje, že dodavatel portu může přidávat nové porty.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Návratová hodnota
 Pokud je možné přidat port, `S_OK` v opačném případě vrátí k označení, že nelze `S_FALSE` do tohoto dodavatele portu přidat žádné porty.

## <a name="remarks"></a>Poznámky
 Tuto metodu volejte před voláním metody [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) , protože druhá metoda vytvoří port a také ho přidá, což může být časově náročná operace.

## <a name="see-also"></a>Viz také
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
