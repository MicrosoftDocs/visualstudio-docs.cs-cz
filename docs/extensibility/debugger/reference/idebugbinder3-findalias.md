---
title: IDebugBinder3::FindAlias | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a697e39d21b1c25a98c09ad6cc4837cca7a293
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735863"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Tato metoda vyhledá alias, daný název. Tím se prohledají všechny aliasy v programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametry
`pcstrName`\
[v] Název aliasu, který chcete najít.

`ppAlias`\
[out] Alias nalezen (pokud existuje) reprezentované [rozhraníM IDebugAlias.](../../../extensibility/debugger/reference/idebugalias.md)

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném `S_FALSE` případě vrátí (pokud alias nebyl nalezen) nebo kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda inicializuje cílový objekt na hodnotu null před voláním; pak testuje hodnotu null později k určení, zda byl nalezen alias.

## <a name="see-also"></a>Viz také
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
