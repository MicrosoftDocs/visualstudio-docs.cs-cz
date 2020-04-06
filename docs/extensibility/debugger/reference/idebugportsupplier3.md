---
title: IDebugPortSupplier3 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f015c21f71f064f2302660ebc75ef00a245348c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724437"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Toto rozhraní umožňuje volajícímu určit, zda dodavatel portu můžete zachovat porty (zápisem na disk) mezi vyvolání ladicího programu a potom získat seznam těchto zachovaných portů.

## <a name="syntax"></a>Syntaxe

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní dodavatel portu implementuje toto rozhraní pro podporu uchování nebo ukládání informací o portu na disk. Toto rozhraní musí být implementováno na stejném objektu jako rozhraní [IDebugPortSupplier2.](../../../extensibility/debugger/reference/idebugportsupplier2.md)

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [QueryInterface](/cpp/atl/queryinterface) `IDebugPortSupplier2` na rozhraní získat toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod zděděných z rozhraní [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) toto rozhraní podporuje následující:

|Metoda|Popis|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Vrátí, zda dodavatel portu může zachovat porty (zápisem na disk) mezi vyvolání ladicího programu.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Vrátí objekt, který lze použít k výčtu prostřednictvím všech portů, které byly zapsány na disk tímto dodavatelem portu.|

## <a name="remarks"></a>Poznámky
 Pokud dodavatel portu může zachovat porty přes vyvolání, měl by implementovat toto rozhraní. Porty by měly být načteny při vytvoření instance dodavatele portu a zapsány na disk při zničení dodavatele portu.

 Ladicí modul obvykle nespolupracuje s dodavatelem portu a nebude mít žádné využití pro toto rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
