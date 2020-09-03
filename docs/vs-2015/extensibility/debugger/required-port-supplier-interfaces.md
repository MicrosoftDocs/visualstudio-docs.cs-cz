---
title: Požadovaná rozhraní dodavatele portu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a065389a6b9b67b8bce82394569ce65afb0f8d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821436"
---
# <a name="required-port-supplier-interfaces"></a>Požadovaná rozhraní dodavatele portu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dodavatel portu musí implementovat rozhraní [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) . [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Vzhledem k tomu, že dodavatel portu dodává porty, musí je také implementovat. Proto musí implementovat následující rozhraní:  
  
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Popisuje port a může vytvořit výčet všech procesů spuštěných na portu.  
  
- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Umožňuje spouštění a ukončování procesů na portu.  
  
- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Poskytuje mechanismus pro programy běžící v kontextu tohoto portu, které upozorňují na vytvoření a zničení uzlu programu. Další informace najdete v tématu [uzly programu](../../extensibility/debugger/program-nodes.md).  
  
- `IConnectionPointContainer`  
  
     Poskytuje bod připojení pro [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Operace dodavatele portu  
 Jímka [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) přijímá oznámení v případě, že proces a programy jsou vytvářeny a zničeny na portu. Port se vyžaduje k odeslání [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) při vytvoření procesu a [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) při zničení procesu na portu. Port je také vyžadován k odeslání [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) při vytvoření programu a [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) , když je program zničen v procesu spuštěném na portu.  
  
 Port obvykle odesílá programu události vytváření a zničení v reakci na metody [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) a [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , v uvedeném pořadí.  
  
 Vzhledem k tomu, že port může spustit a ukončit jak fyzické procesy, tak i logické programy, musí být tato rozhraní implementována i ladicím modulem:  
  
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
  Popisuje fyzický proces. Musí být implementovány alespoň následující metody:  

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  

  - [GetProcessId –](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
    Poskytuje způsob, jak se SDM připojí a odpojí od procesu.  
  
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
  Popisuje logický program. Musí být implementovány alespoň následující metody:  

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Poskytuje způsob, jak se modelu SDM připojit k tomuto programu.  
  
## <a name="see-also"></a>Viz také  
 [Implementace dodavatele portu](../../extensibility/debugger/implementing-a-port-supplier.md)
