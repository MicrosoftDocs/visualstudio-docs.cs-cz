---
title: IDebugEngine3::LoadSymbols | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7963d39601a0d3a90ca2daa7632902d7aa506de8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730813"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Načte (podle potřeby) symboly pro všechny moduly, které jsou laděny tímto ladicím modulem.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>Parametry
 Žádné.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 To načte ladicí symboly pro všechny moduly odkazované tímto ladicím modulem. Symboly jsou načteny pouze v případě, že ještě nebyly načteny. Symboly jsou prohledávány na cestách nastavených voláním [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>Viz také
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
