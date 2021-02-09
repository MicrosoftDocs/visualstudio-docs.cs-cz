---
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 673e4a4f18488b973984319310c139e104524a47
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901895"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní poskytuje přístup k typům, aliasům a vlastním službám Vizualizátoru.

## <a name="syntax"></a>Syntax

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj implementuje toto rozhraní pro podporu aliasů, vlastních služeb Vizualizátoru a přístupu k informacím o typu objektu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Rozhraní [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) získává toto rozhraní pomocí [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod poskytovaných rozhraním [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) implementuje toto rozhraní následující:

|Metoda|Popis|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Načte objekt paměti představující paměť, do které je objekt svázán.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Načte výjimku přidruženou k tomuto objektu (pokud existuje),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Načte alias daného názvu,|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Načte pole všech aliasů pro tento objekt.|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Získá počet typů argumentů přidružených k tomuto objektu,|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Načte seznam typů argumentů přidružených k tomuto objektu.|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Získá rozhraní ke službě Vizualizátoru,|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Převede buď umístění objektu, nebo 64 adresu paměti na kontext paměti.|

## <a name="requirements"></a>Požadavky
 Záhlaví: ee. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
