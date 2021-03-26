---
description: Načte objekt služby s daným jedinečným identifikátorem.
title: 'IDebugExpressionEvaluator2:: GetService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a9c595d2a3a4551920e17a9ad8d8a13b5ae4ab0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092004"
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
