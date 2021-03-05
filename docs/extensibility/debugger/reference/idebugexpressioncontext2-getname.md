---
description: Načte název kontextu vyhodnocení.
title: 'IDebugExpressionContext2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d43af7eeb733aca978a4c3b09fd4f97ca828fe5a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152646"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
Načte název kontextu vyhodnocení.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parametry
`pbstrName`\
mimo Vrátí název kontextu vyhodnocení.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Název je popis tohoto kontextu vyhodnocení. Obvykle je to něco, co lze analyzovat pomocí vyhodnocovacího filtru výrazů, který odkazuje na tento přesný kontext vyhodnocení. Například v jazyce C++ je název následující:

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>Viz také
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
