---
description: Označí tento alias k odebrání.
title: IDebugAlias::Da | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: efca2b2bedc531fa241d8cfe6cfe8cd3527a7b40
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143919"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Označí tento alias k odebrání.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

## <a name="parameters"></a>Parametry
 Žádné

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Po zavolání této metody alias již není k dispozici.

## <a name="see-also"></a>Viz také
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
