---
description: Testuje, zda je tento objekt odkaz s hodnotou null.
title: 'IDebugObject:: IsNullReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 844e6c92385c1aa719d3c9d0ff399db9104dccc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161508"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Testuje, zda je tento objekt odkaz s hodnotou null.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsNullReference( 
   BOOL* pfIsNull
);
```

```csharp
int IsNullReference(
   out int pfIsNull
);
```

## <a name="parameters"></a>Parametry
`pfIsNull`\
mimo Vrátí nenulovou hodnotu ( `TRUE` ), pokud je tento objekt odkaz s hodnotou null. v opačném případě vrátí hodnotu nula ( `FALSE` ).

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Nulový odkaz znamená prázdný objekt nebo objekt, který nebyl přiřazen.

## <a name="see-also"></a>Viz také
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
