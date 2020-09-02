---
title: 'IDebugExpressionEvaluator2:: GetService | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729350"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Načte objekt služby s daným jedinečným identifikátorem.

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
pro Jedinečný identifikátor služby, která se má načíst

`ppService`\
mimo Vrátí objekt, který představuje službu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 To může využívat vyhodnocovací filtr výrazů třetí strany k získání služeb z jiného vyhodnocovacího filtru výrazů. Tuto metodu lze například použít k získání rozhraní pro službu Vizualizátor z výchozího vyhodnocovacího filtru výrazů. Vyhodnocení výrazů třetích stran pravděpodobně není nutné implementovat toto rozhraní.

## <a name="see-also"></a>Viz také
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
