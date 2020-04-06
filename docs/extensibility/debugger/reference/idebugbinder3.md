---
title: IDebugBinder3 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa85872337fdc1f7519d0de98cffe1436ef41c67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735665"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní poskytuje přístup k typům, aliasům a vlastním službám vizualizéru.

## <a name="syntax"></a>Syntaxe

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul implementuje toto rozhraní pro podporu aliasů, vlastních služeb vizualizéru a přístupu k informacím o typu objektu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Rozhraní [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) získá toto rozhraní pomocí [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod poskytovaných rozhraním [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) toto rozhraní implementuje následující:

|Metoda|Popis|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Načte objekt paměti představující paměť, ke které je tento objekt vázán.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Načte výjimku přidruženou k tomuto objektu (pokud existuje),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Načte alias s jeho názvem,|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Načte pole všech aliasů pro tento objekt,|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Získá počet typů argumentů přidružených k tomuto objektu,|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Načte seznam typů argumentů přidružených k tomuto objektu.|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Získá rozhraní ke službě vizualizéru,|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Převede umístění objektu nebo adresu 64bitové paměti na kontext paměti.|

## <a name="requirements"></a>Požadavky
 Záhlaví: ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
