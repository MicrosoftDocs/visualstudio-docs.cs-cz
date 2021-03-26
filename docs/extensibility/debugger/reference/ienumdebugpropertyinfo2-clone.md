---
description: Vrátí kopii aktuálního DEBUG_PROPERTY_INFO výčtu jako samostatný objekt.
title: 'IEnumDebugPropertyInfo2:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::Clone
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Clone
ms.assetid: 0ede1667-1071-4aa4-b887-260ea103d724
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79f5ffd45799b8c2c2ed1642004c26889b26c172
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082917"
---
# <a name="ienumdebugpropertyinfo2clone"></a>IEnumDebugPropertyInfo2::Clone
Vrátí kopii aktuálního výčtu jako samostatný objekt.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Clone(
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
mimo Vrátí kopii tohoto výčtu jako samostatný objekt.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Kopie výčtu má stejný stav jako původní v době volání této metody. Stavy kopie a původní jsou ale oddělené a dají se změnit jednotlivě.

## <a name="see-also"></a>Viz také
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
