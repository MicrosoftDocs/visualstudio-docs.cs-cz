---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1e95996a0548dcf81957dad60c3e6f73b3424c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135628"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Toto rozhraní zobrazí aplikace spuštěné v aktuální relaci ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Modul ladění (DE) implementuje toto rozhraní, které poskytují seznam programů programem DE.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Visual Studio volání [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) k získání tohoto rozhraní. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) nepoužívá Visual Studio.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IEnumDebugPrograms2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Načte zadaný počet programy v posloupnosti výčtu.|  
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Přeskočí zadaný počet programy v posloupnosti výčtu.|  
|[Resetování](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Návrat na začátek v sekvenci výčtu.|  
|[klonování](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Vytvoří enumerátor, který obsahuje stav výčtu jako aktuální enumerátor.|  
|[GetCount –](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Získá počet programů v enumerátor.|  
  
## <a name="remarks"></a>Poznámky  
 Visual Studio použije tohoto rozhraní:  
  
-   Naplnění **moduly** okno (voláním [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) a pak volání [enummodules –](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) na každý program).  
  
-   Naplnění **připojit k procesu** seznamu (voláním `IDebugProcess2::EnumPrograms` a pak volání [QueryInterface](/cpp/atl/queryinterface) na každém [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) rozhraní získat [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) rozhraní).  
  
-   Vygenerovat seznam DEs, který můžete ladit každý program v procesu (pomocí [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
-   Použití aktualizací upravit a pokračovat (ŠIF) pro každý program (voláním IDebugProcess2::EnumPrograms a pak volání [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)