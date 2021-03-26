---
description: Tato metoda obnoví výčet polí na první prvek.
title: 'IEnumDebugFields:: resetovat | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2edf4751151779297d6ff8ed9ffa930cc7bf3868
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086537"
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
Tato metoda obnoví výčet na první prvek.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

#### <a name="parameters"></a>Parametry
 Žádné

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Po volání této metody bude další volání funkce [Next](../../../extensibility/debugger/reference/ienumdebugfields-next.md) vracet první prvek výčtu.

## <a name="see-also"></a>Viz také
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [Další](../../../extensibility/debugger/reference/ienumdebugfields-next.md)
