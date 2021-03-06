---
description: Načte reprezentace rozsahu fyzických adres spojených s rámcem zásobníku, která je závislá na počítači.
title: 'IDebugStackFrame2:: GetPhysicalStackRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7612267a428986ac67a02934f8cbdec38dcb736a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053331"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Načte reprezentace rozsahu fyzických adres spojených s rámcem zásobníku, která je závislá na počítači.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>Parametry
`paddrMin`\
mimo Vrátí nejnižší fyzickou adresu přidruženou k tomuto snímku zásobníku.

`paddrMax`\
mimo Vrátí nejvyšší fyzickou adresu přidruženou k tomuto snímku zásobníku.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Informace vrácené touto metodou jsou používány správcem ladění relace (SDM) k řazení rámců zásobníku.

 Předpokládá se, že zásobník volání roste, to znamená, že nové rámce zásobníku jsou přidány ve stále nižších adresách paměti. Architektura run-time musí poskytovat fyzické rozsahy zásobníku, které odpovídají tomuto předpokladu.

## <a name="see-also"></a>Viz také
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
