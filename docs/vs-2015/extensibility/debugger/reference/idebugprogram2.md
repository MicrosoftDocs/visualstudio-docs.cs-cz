---
title: IDebugProgram2 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0f89f024f0542b8cb20cfbf531fe9f7cf3da561
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741082"
---
# <a name="idebugprogram2"></a>IDebugProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní představuje program, který běží v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Ladicí stroj (DE) a vlastní port dodavatele implementovat toto rozhraní k reprezentaci programu v procesu. Správce ladění relace (SDM) také implementuje toto rozhraní poskytnout informace o [připojit](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) událost vrátí toto rozhraní pro nový program. Toto rozhraní je také použít jako parametr pro mnoho metod na více rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 V následující tabulce jsou uvedeny metody objektu `IDebugProgram2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Vytvoří výčet vlákna, které jsou spuštěny v rámci tohoto programu.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Získá název programu.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Získá, na kterém tento program běží v procesu.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Tento program se ukončí.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Připojí se k tomuto programu.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Určuje, pokud ladicí stroj (DE) můžete odpojit od programu.|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Odpojí ladicí program z tohoto programu.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Získá globálně jedinečný identifikátor pro tento program.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Získá programu vlastnosti.|  
|[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Dál spuštěním tohoto programu v zastaveném stavu. Všechny předchozí stav spuštění je zrušeno.|  
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Dál spuštěním tohoto programu v zastaveném stavu. Všechny předchozí stav spuštění se zachová.|  
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Provádí se krok.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Požadavky, že tento program zastavit provádění na další čas, po jednu z jeho kód spuštění vlákna.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Získá název a identifikátor ladicího stroje (DE) spuštění tohoto programu.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Vytvoří výčet kontexty kód pro danou pozici ve zdrojovém souboru.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Získá počet bajtů paměti pro tento program.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Získá datový proud zpětný překlad pro tento program nebo součástí tohoto programu.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Vytvoří výčet moduly, které tento program načetl a provádí.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Získá aktualizace upravit a pokračovat (ENC) pro tento program.<br /><br /> Tuto metodu není možné implementovat pomocí vlastního ladicího stroje (vždy by měl vrátit `E_NOTIMPL`).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Vytvoří výčet cest kódu tohoto programu.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Výpis zapíše do souboru.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Poznámky  
 Program je kontejner vlákna spuštěná v konkrétní za běhu architektury, zatímco proces se skládá z jednoho nebo více programů.  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Další](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Události](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Připojení](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)

