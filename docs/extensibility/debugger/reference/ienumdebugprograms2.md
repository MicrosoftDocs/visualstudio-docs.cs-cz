---
title: IEnumDebugPrograms2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1717397d9ff073642c7b6bc25ad85babe76d684c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715572"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Toto rozhraní vyjmenovává programy spuštěné v aktuální relaci ladění.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní poskytnout seznam programů, které jsou laděny DE.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Visual Studio volá [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) získat toto rozhraní. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) není používán Visual Studio.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IEnumDebugPrograms2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Načte zadaný počet programů v pořadí výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Přeskočí zadaný počet programů v pořadí výčtu.|
|[Resetovat](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Obnoví pořadí výčtu na začátek.|
|[Klonování](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Vytvoří čítač výčtu, který obsahuje stejný stav výčtu jako aktuální čítač výčtu.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Získá počet programů v čítači výčtu.|

## <a name="remarks"></a>Poznámky
 Visual Studio používá toto rozhraní k:

- Naplnit **okno Moduly** (voláním [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) a potom [voláním EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) v každém programu).

- Naplnit **připojit k procesu** seznamu (voláním `IDebugProcess2::EnumPrograms` a voláním [QueryInterface](/cpp/atl/queryinterface) na každém rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) získat rozhraní [IDebugEngineProgram2).](../../../extensibility/debugger/reference/idebugengineprogram2.md)

- Generovat seznam DEs, které mohou ladit každý program v procesu (pomocí [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

- Použít upravit a pokračovat (ENC) aktualizace pro každý program (voláním IDebugProcess2::EnumPrograms a pak volání [GetENCUpdate).](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
