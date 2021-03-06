---
description: Toto rozhraní umožňuje volajícímu určit, jestli dodavatel portu může chránit porty (jejich zápisem na disk) mezi voláními ladicího programu a následným získáním seznamu těchto zachovaných portů.
title: IDebugPortSupplier3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa17984c9b7f3e87d4a7118188ecc6ca79c5deef
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071932"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Toto rozhraní umožňuje volajícímu určit, jestli dodavatel portu může chránit porty (jejich zápisem na disk) mezi voláními ladicího programu a následným získáním seznamu těchto zachovaných portů.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní dodavatel portu implementuje toto rozhraní pro podporu trvalého nebo ukládání informací o portech na disk. Toto rozhraní musí být implementováno na stejném objektu jako rozhraní [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) .

## <a name="notes-for-callers"></a>Poznámky pro volající
 [](/cpp/atl/queryinterface) `IDebugPortSupplier2` Chcete-li získat toto rozhraní, zavolejte na rozhraní QueryInterface.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod zděděných z rozhraní [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) toto rozhraní podporuje následující:

|Metoda|Popis|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Vrátí, zda dodavatel portu může zachovat porty (jejich zápisem na disk) mezi voláními ladicího programu.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Vrátí objekt, který lze použít k zobrazení výčtu všech portů zapsaných na disk tímto dodavatelem portu.|

## <a name="remarks"></a>Poznámky
 Pokud dodavatel portu může zachovat porty mezi voláními, musí implementovat toto rozhraní. Porty by se měly načíst při vytváření instance dodavatele portu a při zničení dodavatele portu zapsat na disk.

 Ladicí stroj obvykle nekomunikuje s dodavatelem portu a nebude ho používat pro toto rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
