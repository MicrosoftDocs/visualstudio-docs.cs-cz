---
title: IDebugObject2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e468b5a282ffb5466d57a3c9b1a37aa3ae8643ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726071"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní poskytuje další informace o objektu.

## <a name="syntax"></a>Syntaxe

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocení výrazu implementuje toto rozhraní nabídnout podporu pro aliasy a přístup k informacím o objektu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Rozhraní [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) může získat toto rozhraní pomocí [queryinterface](/cpp/atl/queryinterface). Také [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) vrátí toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod v rozhraní [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) rozhraní `IDebugObject2` implementuje následující:

|Metoda|Popis|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Získá pole nebo proměnnou (pokud existuje), které mohou být podporu vlastnost reprezentované tímto objektem.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Získá objekt spravovaného kódu představující hodnotu tohoto objektu.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Vytvoří jedinečné ID pro tento objekt nebo vrátí existující alias.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Získá alias přidružený k tomuto objektu, pokud existuje.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Získá typ tohoto objektu.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Určuje, zda tento objekt představuje uživatelská data.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Určuje, zda stav Upravit a Pokračovat již není platný.<br /><br /> Vyhodnocení vlastního výrazu neimplementuje tuto metodu (by měl vždy vrátit). `E_NOTIMPL`|

## <a name="remarks"></a>Poznámky
 Viz [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) pro diskusi o aliasy.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
