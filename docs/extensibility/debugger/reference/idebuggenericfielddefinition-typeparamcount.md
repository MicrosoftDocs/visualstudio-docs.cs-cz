---
description: Načte počet parametrů typu, které jsou spojeny s obecným polem.
title: 'IDebugGenericFieldDefinition:: TypeParamCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeParamCount
- IDebugGenericFieldDefinition::TypeParamCount
ms.assetid: d41dd5ea-aa25-4bf3-bcfd-e0bf451ead49
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a50f258fe3febdf7c1dd680ea6b731e756abf7e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063393"
---
# <a name="idebuggenericfielddefinitiontypeparamcount"></a>IDebugGenericFieldDefinition::TypeParamCount
Načte počet parametrů typu, které jsou spojeny s obecným polem.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT TypeParamCount(
   ULONG32* pcParams
);
```

```csharp
int TypeParamCount(
   ref uint pcParams
);
```

## <a name="parameters"></a>Parametry
`pcParams`\
[in, out] Počet parametrů typu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud seznam \<T> , tato metoda vrátí 1 a, pokud list \<T1,T2> , vrátí tato metoda 2. Tato metoda vrátí hodnotu 0, pokud nejsou zadány parametry typu.

## <a name="see-also"></a>Viz také
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
