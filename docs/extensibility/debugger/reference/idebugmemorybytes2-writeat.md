---
description: Zapíše zadaný počet bajtů paměti, který začíná na zadané adrese.
title: 'IDebugMemoryBytes2:: WriteAt | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64e8aed5586dc6e2abf33b540654dcd24437e746
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076807"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Zapíše zadaný počet bajtů paměti, který začíná na zadané adrese.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WriteAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory
);
```

```csharp
int WriteAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory
);
```

## <a name="parameters"></a>Parametry
`pStartContext`\
pro Objekt [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , který určuje, kde začít zapisovat bajty.

`dwCount`\
pro Počet bajtů, které mají být zapsány.

`rgbMemory`\
pro Bajty pro zápis. Předpokládá se, že u tohoto pole je `dwCount` Velikost aspoň bajtů.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí, `S_OK` jinak vrátí, `S_FALSE` Pokud ne všechny bajty by se daly zapsat, nebo vrátí chybový kód (obvykle `E_FAIL` ).

## <a name="remarks"></a>Poznámky
 Pokud počáteční adresa není v okně paměti reprezentované tímto objektem [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) , nedojde k žádnému psaní a vrátí se chybový kód `E_FAIL` , a to i v případě, že se hodnota pro zápis překrývá do paměťového prostoru.

## <a name="see-also"></a>Viz také
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
