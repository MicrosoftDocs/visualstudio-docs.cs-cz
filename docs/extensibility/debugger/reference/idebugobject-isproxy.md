---
description: Určuje, zda je objekt transparentním proxy serverem.
title: IDebugObject::-proxy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c9cc2bc45a1e4cfe3e71f07bd2305aa0c7f1fde8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161488"
---
# <a name="idebugobjectisproxy"></a>IDebugObject::IsProxy
Určuje, zda je objekt transparentním proxy serverem.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsProxy (
   BOOL* pfIsProxy
);
```

```csharp
int IsProxy (
   out bool pfIsProxy
);
```

## <a name="parameters"></a>Parametry
`pfIsProxy`\
[out] `TRUE` Pokud je objekt transparentní proxy; v opačném případě `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je implementována pomocí výchozího ladicího stroje jazyka C++.

## <a name="see-also"></a>Viz také
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
