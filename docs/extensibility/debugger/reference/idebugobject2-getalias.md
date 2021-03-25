---
description: Získá alias přidružený k tomuto objektu, pokud existuje.
title: 'IDebugObject2:: getjiné | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c2cbf4a84af4001519617a7e6306c4139e763aea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053786"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Získá alias přidružený k tomuto objektu, pokud existuje.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametry
`ppAlias`\
mimo Vrátí objekt [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) , který představuje alias pro tento objekt. v opačném případě vrátí hodnotu null.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Alias pro objekt je vytvořen s voláním metody [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) .

## <a name="see-also"></a>Viz také
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
