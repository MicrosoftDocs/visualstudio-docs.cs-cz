---
description: Tato metoda obnoví výčet na první prvek IDebugObject.
title: 'IEnumDebugObjects:: resetovat | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 193f0f2f793c1ca1ee1af208105be33754a1effa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083047"
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
Tato metoda obnoví výčet na první prvek.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>Parametry
 Žádné

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Po volání této metody bude další volání funkce [Next](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) vracet první prvek výčtu.

## <a name="see-also"></a>Viz také
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [Další](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)
