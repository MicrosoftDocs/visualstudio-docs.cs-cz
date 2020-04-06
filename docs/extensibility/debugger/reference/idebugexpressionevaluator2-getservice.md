---
title: IDebugExpressionEvaluator2::GetService | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5428606ad54c7938037c3ffecf04f1cfe41787c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729350"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Načte objekt služby s jeho jedinečným identifikátorem.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

## <a name="parameters"></a>Parametry
`uid`\
[v] Jedinečný identifikátor služby, kterou chcete načíst.

`ppService`\
[out] Vrátí objekt, který představuje službu.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 To může být spotřebována vyhodnocení výrazu třetí strany získat služby od jiného vyhodnocení výrazu. Tato metoda může být například použita k získání rozhraní pro službu vizualizéru od výchozího vyhodnocení výrazu. Vyhodnocení výrazů třetích stran je nepravděpodobné, že bude nutné implementovat toto rozhraní.

## <a name="see-also"></a>Viz také
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
