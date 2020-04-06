---
title: IDebugModOpt::GetModOpts | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ab870db3ae3517b60bebd4815e4530f6035b327
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727048"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Načte seznam volitelných modifikátorů.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetModOpts(
   ULONG  celt,
   BSTR*  rgelt,
   ULONG* pceltFetched
);
```

```csharp
int GetModOpts(
   uint         celt,
   out string[] rgelt,
   ref uint     pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
[v] Počet prvků, které mají být vráceny.

`rgelt`\
[out] Vrátí pole, které obsahuje možnosti.

`pceltFetched`\
[dovnitř, ven] Počet prvků vrácených `rgelt` v poli.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
