---
title: IDebugProgram2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722720"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Toto rozhraní představuje program, který je spuštěn v procesu.

## <a name="syntax"></a>Syntax

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Modul ladění (DE) a vlastní dodavatel portu implementují toto rozhraní tak, aby představovalo program v procesu. Správce ladění relace (SDM) implementuje také toto rozhraní, aby poskytovalo informace, které se mají [připojit](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Poznámky pro volající
 Událost [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) vrací toto rozhraní pro nový program. Toto rozhraní se používá také jako parametr pro mnoho metod na více rozhraních.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugProgram2` .

|Metoda|Popis|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Vytvoří výčet vláken, která jsou spuštěna v rámci tohoto programu.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Získá název programu.|
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Získá proces, ve kterém je tento program spuštěn.|
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md) (Ukončení)|Ukončí program.|
|[Připojit](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Připojí se k tomuto programu.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Určuje, zda se může ladicí stroj (DE) odpojit od programu.|
|[Odpojit](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Odpojí ladicí program od tohoto programu.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Získá globálně jedinečný identifikátor pro tento program.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Získá vlastnosti programu.|
|[Spuštění](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Pokračuje v běhu tohoto programu ze stavu Zastaveno. Jakýkoli předchozí stav spuštění je vymazán.|
|[Pokračovat](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Pokračuje v běhu tohoto programu ze stavu Zastaveno. Veškerý předchozí stav spuštění se zachová.|
|[Krok](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Provede krok.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Požaduje, aby tento program zastavil provádění při příštím spuštění kódu v jednom z jeho vláken.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Získá název a identifikátor ladicího modulu (DE), který spouští tento program.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Vytvoří výčet kontextů kódu pro danou pozici ve zdrojovém souboru.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Získá bajty paměti pro tento program.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Získá datový proud zpětného překladu pro tento program nebo část tohoto programu.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Vytvoří výčet modulů, které tento program načetl a provádí.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Získá aktualizaci úpravy a pokračování (ENC) pro tento program.<br /><br /> Vlastní ladicí stroj neimplementuje tuto metodu (měla by vždycky vracet `E_NOTIMPL` ).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Vytvoří výčet cest k kódu tohoto programu.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Zapíše výpis do souboru.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Poznámky
 Program je kontejner vláken spuštěný v určité architektuře run-time, zatímco proces se skládá z jednoho nebo více programů.

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Další](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Událost](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
