---
description: Tato metoda načte seznam aliasů z programu.
title: 'IDebugBinder3:: GetAllAliases | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16a9d41280a9ff97072390a0cd2e687ee24e1d83
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102174044"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Tato metoda načte seznam aliasů z programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>Parametry
`uRequest`\
pro Maximální počet aliasů, které se mají vrátit (určuje délku pole předaného `ppAliases` ).

`ppAliases`\
[in, out] Pole, které se má vyplnit aliasy (Pokud se jedná o hodnotu null a `uRequest` je 0, vrátí se počet aliasů, které mohou být vráceny `puFetched` ).

`puFetched`\
mimo Vrátí počet získaných aliasů.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
