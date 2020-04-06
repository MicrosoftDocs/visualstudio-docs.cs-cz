---
title: IEnumDebugPortSuppliers2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de0bfc5b387df9b347e4a58d97601a5e1e70f1a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715937"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Toto rozhraní vyjmenovává dodavatele portů.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Visual Studio implementuje toto rozhraní představující seznam dodavatelů portů.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Chcete-li získat seznam dodavatelů portů, zavolejte na [dodavatele enumPortSuppliers.](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IEnumDebugPortSuppliers2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Načte zadaný počet dodavatelů portů v pořadí výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Přeskočí zadaný počet dodavatelů portů v pořadí výčtu.|
|[Resetovat](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Obnoví pořadí výčtu na začátek.|
|[Klonování](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Vytvoří čítač výčtu, který obsahuje stejný stav výčtu jako aktuální čítač výčtu.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Získá počet dodavatelů portů v čítači výčtu.|

## <a name="remarks"></a>Poznámky
 Ladicí modul obecně není nutné získat toto rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
