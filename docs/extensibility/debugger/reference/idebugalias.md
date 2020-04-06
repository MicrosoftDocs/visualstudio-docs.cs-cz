---
title: IDebugAlias | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2ceb87277460f65e52c35f02e7fbbd01da1101a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736514"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Představuje číselný alias proměnné. Alias je jednoduše jiný název proměnné.

## <a name="syntax"></a>Syntaxe

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocení výrazu (EE) implementuje toto rozhraní pro podporu číselných aliasů pro proměnné.

## <a name="notes-for-callers"></a>Poznámky pro volající
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) vytvoří alias pro určitý objekt. Chcete-li vyhledat aliasy, použijte [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) nebo [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Následující metody jsou definovány `IDebugAlias` v rozhraní.

|Metoda|Popis|
|------------|-----------------|
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Získá objekt, na který odkazuje tento alias.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Získá název aliasu.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Načte `ICorDebugValue` rozhraní, které poskytuje přístup k informacím spravovaného kódu o tomto objektu (pouze spravovaný kód).|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Označí tento alias jako již používaný.|

## <a name="remarks"></a>Poznámky
 Alias je desetinné číslo ve formě řetězce následované znakem #, například 1001#.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
