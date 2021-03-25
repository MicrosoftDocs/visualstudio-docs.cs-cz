---
description: Obnoví výčet dodavatelů portů na první prvek.
title: 'IEnumDebugPortSuppliers2:: resetovat | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::Next
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Next
ms.assetid: f69cbacf-da9d-4b22-b8a2-abd9b8c131f2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db9496aec53516b1ddb201c75226b06573781570
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061638"
---
# <a name="ienumdebugportsuppliers2reset"></a>IEnumDebugPortSuppliers2::Reset
Obnoví výčet na první prvek.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Po volání této metody vrátí další volání metody [Next](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md) první prvek výčtu.

## <a name="see-also"></a>Viz také
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
