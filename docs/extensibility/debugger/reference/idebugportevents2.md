---
title: IDebugPortEvents2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725185"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Toto rozhraní upozorní naslouchací proces (obvykle správce ladění relace [SDM] nebo ladicí stroj) o vytvoření a zničení procesu a programu na konkrétním portu. Tyto informace lze použít k zobrazení přehledných procesů a programů v reálném čase, které jsou spuštěny na portu.

## <a name="syntax"></a>Syntax

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Visual Studio obvykle implementuje toto rozhraní pro příjem oznámení o vytvoření a zničení programu. Ladicí stroj může také implementovat toto rozhraní, aby naslouchalo takové události portů.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Všechna rozhraní [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) se dají dotazovat na <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> rozhraní. Pak <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> metoda pro `IDebugPortEvents2` je volána v <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> rozhraní pro získání <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> rozhraní. Nakonec <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> metoda v <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> rozhraní je volána pro odeslání událostí prostřednictvím metody [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md) .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Následující tabulka ukazuje metodu `IDebugPortEvents2` .

|Metoda|Popis|
|------------|-----------------|
|[Událost](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Odesílá události, které popisují vytvoření a zničení procesů a programů na portu.|

## <a name="remarks"></a>Poznámky
 `IDebugPortEvents2` používá model SDM také k ladění programů, které se spouštějí v procesu, který je již laděn.

 Toto rozhraní předává události portů službě SDM.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
