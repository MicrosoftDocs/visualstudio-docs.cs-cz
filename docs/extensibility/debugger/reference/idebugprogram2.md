---
title: IDebugProgram2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 392d9bd350d6207e6725c31c659a6edf1518a807
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122597"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Toto rozhraní představuje program, který běží v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Modul ladění (DE) a vlastní port dodavatele implementovat toto rozhraní představují program v procesu. Správce ladicí relace (SDM) také implementuje toto rozhraní poskytovat informace o [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) událostí vrátí toto rozhraní pro nový program. Toto rozhraní je také použít jako parametr pro mnoho způsobů na více rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDebugProgram2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Enumthreads –](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Vytvoří výčet vláken, které jsou spuštěny v této aplikaci.|  
|[GetName –](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Získá název programu.|  
|[Getprocess –](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Získá proces, který tento program je spuštěn v.|  
|[Ukončení](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Ukončí tento program.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Připojí se k tomuto programu.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Určuje, pokud modul ladění (DE), můžete odpojení od programu.|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Umožňuje odpojit ladicí program z tohoto programu.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Získá globálně jedinečný identifikátor pro tento program.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Získá programu vlastnosti.|  
|[Spuštění](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Dál spuštěním tohoto programu z zastaveném stavu. Všechny předchozí provádění stav je vymazán.|  
|[Pokračovat](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Dál spuštěním tohoto programu z zastaveném stavu. Všechny předchozí stav spuštění je zachovaná.|  
|[Krok](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Provede krok.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Požadavky, že tento program zastavit provádění další čas jeden z jeho vlákna spustí kód.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Získá název a identifikátor ladění modulu (DE), spuštěním tohoto programu.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Vytvoří výčet kontexty kód pro dané pozici ve zdrojovém souboru.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Získá počet bajtů paměti pro tento program.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Získá datový proud zpětný překlad pro tento program nebo její část tohoto programu.|  
|[Enummodules –](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Vytvoří výčet moduly, které tento program načetl a je prováděna.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Získá aktualizace upravit a pokračovat (ŠIF) pro tento program.<br /><br /> Modul vlastní ladění neimplementuje tuto metodu (vždy by měla vrátit `E_NOTIMPL`).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Vytvoří výčet cesty kódu tohoto programu.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Výpis zapisuje do souboru.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Poznámky  
 Program je spuštěn v konkrétní architektuře běhu a proces se skládá z jednoho nebo více programů kontejner přístup z více vláken.  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Další](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Události](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Připojení](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)