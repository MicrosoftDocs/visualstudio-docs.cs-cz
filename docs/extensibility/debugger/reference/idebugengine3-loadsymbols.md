---
description: Načte (v případě potřeby) symboly pro všechny moduly laděné tímto modulem ladění.
title: 'IDebugEngine3:: LoadSymbols | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4b4f210ef07ad10b35251582dd8a3c0fe3b0685
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153804"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Načte (v případě potřeby) symboly pro všechny moduly laděné tímto modulem ladění.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>Parametry
 Žádné

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Načte symboly ladění pro všechny moduly, na které odkazuje tento modul ladění. Symboly jsou načteny pouze v případě, že ještě nejsou načteny. Symboly jsou prohledány na cesty nastavené voláním [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>Viz také
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
