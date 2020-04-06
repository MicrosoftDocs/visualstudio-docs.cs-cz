---
title: IDebugMemoryContext2::Přidat | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a21fa2ec6d48bb1d6bf17bbc0d2ebf0d90a25a9f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727479"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Přidá zadanou hodnotu do aktuálního kontextu a vrátí nový kontext.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametry
`dwCount`\
[v] Hodnota, která má být přidana k aktuálnímu kontextu.

`ppMemCxt`\
[out] Vrátí nový objekt [IDebugMemoryContext2.](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Kontext paměti je adresa, takže přidání hodnoty do adresy vytvoří novou adresu, která vyžaduje nové kontextové rozhraní.

 Tato metoda musí vždy vytvořit nový kontext, i v případě, že výsledná adresa je mimo paměťový prostor přidružený k tomuto kontextu. Jedinou výjimkou je, pokud žádná paměť může být přidělena pro nový kontext nebo pokud `ppMemCxt` je hodnota null (což je chyba).

## <a name="see-also"></a>Viz také
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
