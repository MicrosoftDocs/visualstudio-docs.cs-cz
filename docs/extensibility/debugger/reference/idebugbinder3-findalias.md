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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db4d5cad6d0c2990141e0dd3a824425b8b53145b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167721"
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
