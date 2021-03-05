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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f6a586c7e7cac1a4ef034b7941840db59d376180
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152491"
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
