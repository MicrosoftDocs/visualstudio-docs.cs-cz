---
title: IEnumDebugModules2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 612285aa4d5a249c0f922ccae88d98a7df83187b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716444"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Toto rozhraní obsahuje výčet seznamu modulů.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní představující seznam modulů načtených pro program.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Visual Studio volá [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) získat toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IEnumDebugModules2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Načte zadaný počet modulů v pořadí výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Přeskočí zadaný počet modulů v pořadí výčtu.|
|[Resetovat](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Obnoví pořadí výčtu na začátek.|
|[Klonování](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Vytvoří čítač výčtu, který obsahuje stejný stav výčtu jako aktuální čítač výčtu.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Získá počet modulů.|

## <a name="remarks"></a>Poznámky
 Visual Studio používá toto rozhraní především k aktualizaci okna **Moduly.**

 Pro účely ladění v sadě Visual Studio je program logickou posloupností pokynů kódu, které mohou překročit hranice modulu, proto je potřeba seznam modulů pro jedno rozhraní [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md) První modul v seznamu obvykle obsahuje počáteční vstupní bod pro přidružený program.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
