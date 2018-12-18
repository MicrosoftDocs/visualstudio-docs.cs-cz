---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cc599480b148e85dd8d70c45282ef52d08b8eabf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121954"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Toto rozhraní zasílá modul ladění (DE) zadaný pro relaci ladění správce (SDM) při vytváření vlastnosti, která je přidružena k určité dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 DE implementuje toto rozhraní informuje, zda byl vytvořen vlastnost. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) rozhraní musí být implementována pro stejný objekt jako toto rozhraní. Používá SDM [QueryInterface](/cpp/atl/queryinterface) k přístupu `IDebugEvent2` rozhraní. Toto rozhraní je implementováno, pokud je DE vytvořil vlastnost přidružený ke skriptu, který byl načteny nebo vytvořili, a pokud skriptu je potřeba se zobrazí v prostředí IDE.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 DE vytvoří a odešle tento objekt událostí do sestavy, kterou vytvořil vlastnost. Událost je odeslána pomocí [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkce zpětného volání, který poskytl SDM při připojení k programu laděné.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 V následující tabulce jsou uvedeny metodě `IDebugPropertyCreateEvent2` rozhraní.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Získá novou vlastnost.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud vlastnost obsahuje konkrétní dokument nebo skript s ním spojená, DE můžete odeslat tuto událost SDM za účelem aktualizace **dokumentů skriptu** okno s název dokumentu. Zavolá SDM [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) s argumentem `guidDocument` načíst `VARIANT` obsahující [IUnknown](/cpp/atl/iunknown) ukazatel. Zavolá SDM [QueryInterface](/cpp/atl/queryinterface) na tento ukazatel načíst [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) rozhraní, které se používá k aktualizaci **dokumentů skriptu** okno.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)