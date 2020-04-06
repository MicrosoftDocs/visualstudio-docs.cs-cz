---
title: IDebugPortEvents2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c611eb531bdabb633b11ac2e8ca2d0d11f52005
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725185"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Toto rozhraní upozorní naslouchací proces (obvykle správce ladění relace [SDM] nebo ladicí modul) na vytváření a zničení programu na konkrétním portu. Tyto informace lze použít k zobrazení procesů a programů spuštěných na portu v reálném čase.

## <a name="syntax"></a>Syntaxe

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Visual Studio obvykle implementuje toto rozhraní přijímat oznámení o vytváření a zničení programu. Ladicí modul může také implementovat toto rozhraní pro naslouchání pro tyto události portu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Všechna rozhraní [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) mohou být <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> dotazována na rozhraní. Pak <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> metoda `IDebugPortEvents2` pro je <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> volána v <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> rozhraní získat rozhraní. Nakonec <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> je volána <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> metoda v rozhraní k odeslání událostí prostřednictvím [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md) metoda.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce je `IDebugPortEvents2`uvedena metoda .

|Metoda|Popis|
|------------|-----------------|
|[Událost](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Odešle události, které popisují vytváření a ničení procesů a programů na portu.|

## <a name="remarks"></a>Poznámky
 `IDebugPortEvents2`je také používán SDM k ladění programů, které běží v procesu, který je již laděn.

 Události portu jsou předány SDM tímto rozhraním.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
