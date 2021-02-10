---
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
ms.openlocfilehash: 8529e83de0f5de3d5d202885cf37b29d21fa3e59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949529"
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
