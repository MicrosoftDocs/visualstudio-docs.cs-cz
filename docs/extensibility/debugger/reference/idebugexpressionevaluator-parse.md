---
description: Tato metoda převede řetězec výrazu na analyzovaný výraz.
title: IDebugExpressionEvaluator::P Arse | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 560274fa9364e86cbb689af2234f72397f0560fc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092160"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Tato metoda převede řetězec výrazu na analyzovaný výraz.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Parse( 
   LPCOLESTR                upstrExpression,
   PARSEFLAGS               dwFlags,
   UINT                     nRadix,
   BSTR*                    pbstrError,
   UINT*                    pichError,
   IDebugParsedExpression** ppParsedExpression
);
```

```csharp
int Parse(
   string                     upstrExpression,
   enum_PARSEFLAGS            dwFlags,
   uint                       nRadix,
   out string                 pbstrError,
   out uint                   pichError,
   out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Parametry
`upstrExpression`\
pro Řetězec výrazu, který se má analyzovat.

`dwFlags`\
pro Kolekce konstant [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) , které určují, jak má být výraz analyzován.

`nRadix`\
pro Číselná soustava, která se má použít k interpretaci jakýchkoli číselných informací.

`pbstrError`\
mimo Vrátí chybu jako text čitelný lidmi.

`pichError`\
mimo Vrátí pozici znaku začátku chyby v řetězci výrazu.

`ppParsedExpression`\
mimo Vrátí analyzovaný výraz v objektu [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda vytvoří analyzovaný výraz, nikoli skutečnou hodnotu. Analyzovaný výraz je připravený k vyhodnocení, tj., který je převeden na hodnotu.

## <a name="see-also"></a>Viz také
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
