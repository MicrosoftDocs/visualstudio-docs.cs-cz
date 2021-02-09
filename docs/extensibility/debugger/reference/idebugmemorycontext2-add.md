---
title: 'IDebugMemoryContext2:: Add | Microsoft Docs'
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ddba5665ead15bb623193412bafa7d6eaa8aa16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851215"
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
pro Hodnota, která má být přidána do aktuálního kontextu.

`ppMemCxt`\
mimo Vrátí nový objekt [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Kontext paměti je adresa, takže když přidáte hodnotu na adresu, vytvoří se nová adresa, která vyžaduje nové kontextové rozhraní.

 Tato metoda musí vždy vytvořit nový kontext, a to i v případě, že Výsledná adresa je mimo prostor paměti přidružené k tomuto kontextu. Jedinou výjimkou je, že není možné přidělit paměť pro nový kontext nebo pokud `ppMemCxt` je hodnota null (což je chyba).

## <a name="see-also"></a>Viz také
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
