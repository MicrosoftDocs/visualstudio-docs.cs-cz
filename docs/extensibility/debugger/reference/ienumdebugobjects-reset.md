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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cacc9071004ddb68993bb3d3315eb1bda3b90cbb
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224652"
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
