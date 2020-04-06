---
title: IDebugPointerObject | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b28189b3f0a07a27f5e4478f64963a63d634db5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725488"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní představuje objekt ukazatele.

## <a name="syntax"></a>Syntaxe

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocení výrazu implementuje toto rozhraní představují objekt ukazatele.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Rozhraní [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) můžete získat toto rozhraní `IDebugObject` pomocí [QueryInterface,](/cpp/atl/queryinterface) pokud představuje ukazatel.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod zděděných z [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)rozhraní `IDebugPointerObject` zveřejňuje následující metody.

|Metoda|Popis|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Získá objekt, na který odkazuje rozhraní.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Získá hodnotu, na kterou rozhraní odkazuje jako řada po sobě jdoucích bajtů.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Nastaví hodnotu, na kterou rozhraní odkazuje z řady po sobě jdoucích bajtů.|

## <a name="remarks"></a>Poznámky
 Vyhodnocení výrazu používá toto rozhraní k reprezentaci ukazatele ve stromu analýzy.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
