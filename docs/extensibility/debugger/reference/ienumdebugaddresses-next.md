---
title: 'IEnumDebugAddresses:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Next
helpviewer_keywords:
- IEnumDebugAddresses::Next method
ms.assetid: 941e4be7-858d-433a-9259-18d0d017be9e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88deefddc5b479d7173c4de1c574c4da92631e97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717633"
---
# <a name="ienumdebugaddressesnext"></a>IEnumDebugAddresses::Next
Tato metoda vrací další sadu prvků z výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugAddress** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugAddress[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
pro Počet prvků, které mají být načteny. Určuje také maximální velikost `rgelt` pole.

`rgelt`\
[in, out] Pole [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) prvků, které se mají vyplnit

`pceltFetched`\
mimo Vrátí počet prvků, které jsou ve skutečnosti vráceny v `rgelt` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud je možné vrátit méně než požadovaný počet prvků. v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
