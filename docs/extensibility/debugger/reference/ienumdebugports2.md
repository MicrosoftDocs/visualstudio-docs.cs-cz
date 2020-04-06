---
title: IEnumDebugPorts2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3cc46ef8abb6ef1fbb8f072d97b0fc4a537af1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716099"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Toto rozhraní vyjmenovává porty dodavatele počítače nebo portu.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní dodavatel portu implementuje toto rozhraní představující seznam portů vytvořených dodavatelem. Visual Studio implementuje toto rozhraní na podporu vlastního dodavatele portu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) získat toto rozhraní představující seznam portů vytvořených dodavatelem portu. Volání [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) získat toto rozhraní představující seznam portů, které byly uloženy na disk.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IEnumDebugPorts2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Načte zadaný počet portů v pořadí výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Přeskočí zadaný počet portů v pořadí výčtu.|
|[Resetovat](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Obnoví pořadí výčtu na začátek.|
|[Klonování](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Vytvoří čítač výčtu, který obsahuje stejný stav výčtu jako aktuální čítač výčtu.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Získá počet portů v čítači výčtu.|

## <a name="remarks"></a>Poznámky
 Visual Studio používá toto rozhraní k naplnění seznamu portů používaných pro připojení k procesům.

 Ladicí modul obvykle nepoužívá toto rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
