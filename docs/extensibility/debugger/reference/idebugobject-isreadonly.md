---
description: Určuje, zda je tento objekt určen jen pro čtení.
title: 'IDebugObject:: IsReadOnly | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d99cf51ba5415631b2e8e66c36b459297a8fcb6e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161475"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Určuje, zda je tento objekt určen jen pro čtení.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

## <a name="parameters"></a>Parametry
`pfIsReadOnly`\
mimo Vrátí nenulovou hodnotu ( `TRUE` ), pokud je tento objekt jen pro čtení; v opačném případě vrátí hodnotu nula ( `FALSE` ).

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Po vytvoření objektu jen pro čtení nemůže být jeho hodnota změněna.

## <a name="see-also"></a>Viz také
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
