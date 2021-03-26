---
description: Toto rozhraní vypíše programy běžící v aktuální relaci ladění.
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d7f9a981146d5e024333f17557f4fdbc3d35bc05
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082930"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Toto rozhraní vypíše programy běžící v aktuální relaci ladění.

## <a name="syntax"></a>Syntax

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Modul ladění (DE) implementuje toto rozhraní k poskytnutí seznamu programů, které jsou laděny pomocí příkazu DE.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Visual Studio volá [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) k získání tohoto rozhraní. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) se nepoužívá v aplikaci Visual Studio.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IEnumDebugPrograms2` .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Načte zadaný počet programů v sekvenci výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Přeskočí zadaný počet programů v sekvenci výčtu.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Obnoví posloupnost výčtu na začátek.|
|[Klonovat](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Získá počet programů v enumerátoru.|

## <a name="remarks"></a>Poznámky
 Visual Studio používá toto rozhraní pro:

- Naplňte okno **moduly** (voláním [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) a potom zavoláte [enummodules –](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) na každý program).

- Naplňte seznam **připojit k procesu** (voláním `IDebugProcess2::EnumPrograms` a pak voláním [QueryInterface](/cpp/atl/queryinterface) na každém rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , abyste získali rozhraní [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) ).

- Vygeneruje seznam DEs, který může ladit jednotlivé programy v procesu (pomocí [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

- Použijte úpravy a pokračování (ENC) pro každý program (voláním IDebugProcess2:: EnumPrograms a následným voláním [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
