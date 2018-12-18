---
title: IEnumDebugProcesses2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5fdc8d37700edb2776c905c45ddd97496228faf9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125711"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Toto rozhraní zobrazí procesů spuštěných na portu ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Vlastní port dodavatele implementuje toto rozhraní, které poskytují seznam procesů spuštěných na portu.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Visual Studio volání [enumprocesses –](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) k získání tohoto rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IEnumDebugProcesses2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Načte zadaný počet procesů v posloupnosti výčtu.|  
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Přeskočí zadaný počet procesů v posloupnosti výčtu.|  
|[Resetování](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Návrat na začátek v sekvenci výčtu.|  
|[klonování](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Vytvoří enumerátor, který obsahuje stav výčtu jako aktuální enumerátor.|  
|[GetCount –](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Získá počet procesů v enumerátor.|  
  
## <a name="remarks"></a>Poznámky  
 Visual Studio použije k naplnění toto rozhraní **procesy** okno.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)