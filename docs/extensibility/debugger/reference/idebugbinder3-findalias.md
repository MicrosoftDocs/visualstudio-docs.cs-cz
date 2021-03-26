---
description: Tato metoda vyhledá alias s daným názvem.
title: 'IDebugBinder3:: FindAlias | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9958c1c2b93d6547f1f3453bafc9e331f9061844
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089053"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Tato metoda vyhledá alias s daným názvem. Prohledají se všechny aliasy v programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametry
`pcstrName`\
pro Název hledaného aliasu.

`ppAlias`\
mimo Byl nalezen alias (pokud existuje) reprezentovaný rozhraním [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` (Pokud se alias nenalezne) nebo kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda inicializuje cílový objekt na hodnotu null před voláním; potom otestuje hodnotu null a následně určí, zda byl alias nalezen.

## <a name="see-also"></a>Viz také
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
