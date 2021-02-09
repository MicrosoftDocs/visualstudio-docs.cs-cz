---
title: 'IEnumDebugFields:: resetovat | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1cbe3ecaf681a0fb88dab46b9c2dac2110b7beb4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919680"
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
