---
description: Vrátí další sadu prvků ze výčtu kontextů kódu.
title: 'IEnumDebugCodeContexts2:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Next
helpviewer_keywords:
- IEnumDebugCodeContexts2::Next
ms.assetid: 0d8aa2db-0994-4166-b364-2e25d936fffc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c3ded045b0b2b8b1d7d84ce0240322e16f2db97f
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222624"
---
# <a name="ienumdebugcodecontexts2next"></a>IEnumDebugCodeContexts2::Next
Vrátí další sadu prvků z výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next(
   ULONG                celt,
   IDebugCodeContext2** rgelt,
   ULONG*               pceltFetched
);
```

```csharp
int Next(
   uint                 celt,
   IDebugCodeContext2[] rgelt,
   ref uint             pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
pro Počet prvků, které mají být načteny. Určuje také maximální velikost `rgelt` pole.

`rgelt`\
[in, out] Pole [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) prvků, které se mají vyplnit

`pceltFetched`\
mimo Vrátí počet prvků, které jsou ve skutečnosti vráceny v `rgelt` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud je možné vrátit méně než požadovaný počet prvků. v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
