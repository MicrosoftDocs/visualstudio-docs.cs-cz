---
description: Nastaví hodnotu objektu z po sobě jdoucí řady bajtů.
title: 'IDebugObject:: SetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63d75eae9c7966bfc5e7fceea0512db0fa174066
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054098"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Nastaví hodnotu objektu z po sobě jdoucí řady bajtů.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

## <a name="parameters"></a>Parametry
`pValue`\
pro Pole bajtů představující novou hodnotu.

`nSize`\
pro Velikost hodnoty v bajtech

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Hodnoty v poli jsou zkopírovány do tohoto objektu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) a nahradí všechny existující hodnoty. Velikost nové hodnoty může být větší nebo menší než stávající hodnota. `IDebugObject`Nemůže se jednat o odkaz s hodnotou null.

## <a name="see-also"></a>Viz také
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
