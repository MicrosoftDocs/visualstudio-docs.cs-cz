---
title: Požadovaná rozhraní dodavatele portu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 485c295e7258f09aaf4114d5945f8136057447e6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782801"
---
# <a name="required-port-supplier-interfaces"></a>Požadovaná rozhraní dodavatele portu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Musí implementovat dodavatele portu [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) rozhraní.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Protože dodavatele portu poskytuje porty, musí je také implementovat. Proto musí implementovat rozhraní následující:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Popisuje, port a můžete zobrazit výčet všechny procesy spuštěné na portu.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Umožňuje spouštění a ukončování procesů na portu.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Poskytuje mechanismus pro programy spuštěné v rámci kontextu tento port oznámit ho program uzel vytváření a zničení. Další informace najdete v tématu [uzly programů](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Poskytuje bod připojení pro [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Operace dodavatele portu  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) jímky obdrží oznámení při zpracování a programy jsou vytvořeno a zničeno na portu. Port je vyžadován pro odeslání [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) při vytvoření procesu a [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) při zničení proces na portu. Port je také potřeba odeslat [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) při vytvoření programu v jazyce a [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) při je program zničeny v procesu spuštěného na portu.  
  
 Port obvykle odešle programu vytvořit a zničit událostí v reakci [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) a [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) metody, v uvedeném pořadí.  
  
 Protože portu můžete spustit a ukončit procesy fyzické a logické programy, tato rozhraní musí být také implementováno pomocí ladicího stroje:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Popisuje proces fyzické. Minimálně musí implementovat následující metody:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Poskytuje způsob, jakým SDM připojit a samotné odpojit od procesu.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Popisuje logické programu. Minimálně musí implementovat následující metody:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Poskytuje způsob, jakým SDM připojit k tomuto programu.  
  
## <a name="see-also"></a>Viz také  
 [Implementace dodavatele portu](../../extensibility/debugger/implementing-a-port-supplier.md)

