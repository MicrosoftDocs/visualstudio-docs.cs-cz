---
title: IDebugMemoryContext2::Odečíst | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c858beb8c3f9f587633dbae8b3b1fe73fd789663
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727445"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Odečte zadanou hodnotu od aktuálního kontextu a vrátí nový kontext.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Subtract( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Subtract(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametry
`dwCount`\
[v] Počet bajtů paměti k snížení.

`ppMemCxt`\
[out] Vrátí nový objekt [IDebugMemoryContext2.](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Kontext paměti je adresa, takže odečtením hodnoty od adresy vznikne nová adresa, která vyžaduje nové kontextové rozhraní.

 Tato metoda musí vždy vytvořit nový kontext, i v případě, že výsledná adresa je mimo paměťový prostor přidružený k tomuto kontextu. Jedinou výjimkou je, pokud žádná paměť může být přidělena pro nový kontext nebo pokud `ppMemCxt` je hodnota null (což je chyba).

## <a name="see-also"></a>Viz také
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
