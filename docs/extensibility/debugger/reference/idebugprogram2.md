---
title: IDebugProgram2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 150746197be4945b012717bef08e18ea57168177
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722720"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Toto rozhraní představuje program, který je spuštěn v procesu.

## <a name="syntax"></a>Syntaxe

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) a dodavatel vlastního portu implementují toto rozhraní tak, aby představovalo program v procesu. Správce ladění relace (SDM) také implementuje toto rozhraní poskytnout informace [připojit](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Poznámky pro volající
 Událost [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) vrátí toto rozhraní pro nový program. Toto rozhraní se také používá jako parametr pro mnoho metod na více rozhraních.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugProgram2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Vytvoří vyjmenovává vlákna spuštěná v tomto programu.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Získá název programu.|
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Získá proces, který je spuštěn v tomto programu.|
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Ukončí tento program.|
|[Připojit](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Připojí se k tomuto programu.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Určuje, zda ladicí modul (DE) může odpojit od programu.|
|[Odpojit](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Odpojí ladicí program od tohoto programu.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Získá globálně jedinečný identifikátor pro tento program.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Získá vlastnosti programu.|
|[Spuštění](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Pokračuje ve spouštění tohoto programu ze zastaveného stavu. Jakýkoli předchozí stav spuštění je vymazán.|
|[Pokračovat](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Pokračuje ve spouštění tohoto programu ze zastaveného stavu. Jakýkoli předchozí stav spuštění je zachován.|
|[Krok](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Provede krok.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Požaduje, aby tento program zastavil spuštění při příštím spuštění jednoho z jeho vláken.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Získá název a identifikátor ladicí modul (DE) spuštěný tento program.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Vytvoří vyjmenovává kontexty kódu pro danou pozici ve zdrojovém souboru.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Získá bajtů paměti pro tento program.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Získá datový proud demontáže pro tento program nebo část tohoto programu.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Vytvoří výčet modulů, které tento program načetl a provádí.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Získá upravit a pokračovat (ENC) aktualizace pro tento program.<br /><br /> Vlastní ladicí modul neimplementuje tuto `E_NOTIMPL`metodu (by měl vždy vrátit).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Vytvoří vyjmenovává cesty kódu tohoto programu.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Zapíše výpis do souboru.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Poznámky
 Program je kontejner vláken spuštěný v určité architektuře za běhu, zatímco proces se skládá z jednoho nebo více programů.

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Další](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Událost](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
