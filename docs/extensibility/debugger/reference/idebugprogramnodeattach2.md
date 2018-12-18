---
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a83f5635dfacb638a2e76054dc5ed4e887e2a3cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120686"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Umožňuje programu uzlu upozornit pokus o připojení k programu přidružené.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto rozhraní je implementováno u stejné třídy, který implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) rozhraní příjem oznámení připojit operace vyžaduje, aby a pro poskytování příležitost ke zrušení operace připojení.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Získat voláním toto rozhraní `QueryInterface` metoda v [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objektu. [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metoda musí být volána před provedením [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metoda umožnit uzlu program příležitost k zastavení procesu připojování.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Toto rozhraní implementuje následující metodu:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Připojí k přidružený program nebo odkládat údaje proces připojit [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metoda.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je upřednostňovaný alternativa k nepoužívané [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) metoda. Všechny moduly ladění jsou vždycky načtená `CoCreateInstance` fungovat, to znamená, jsou vytvořeny instance mimo Adresní prostor laděné programu.  
  
 Pokud předchozí provádění `IDebugProgramNode2::Attach_V7` metoda jednoduše při nastavování `GUID` programu probíhá ladění, pak pouze [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) musí být implementována metoda.  
  
 Pokud předchozí provádění `IDebugProgramNode2::Attach_V7` metodu použít rozhraní zpětné volání, která byla poskytována a této funkce musí být přesunul na implementaci pro [připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md) metoda a `IDebugProgramNodeAttach2` rozhraní nemá musí být implementována.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Připojení](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)