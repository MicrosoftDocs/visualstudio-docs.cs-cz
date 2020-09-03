---
title: 'IDebugPortSupplier2:: CanAddPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5d0c67d62f57076f29f2c2ef60d456f517ae97fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724746"
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
