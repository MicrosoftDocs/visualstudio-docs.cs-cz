---
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1238fcbce22db3f3bc3e32019aac886c79d0c114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201025"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní představuje zarážku, která je připravená k vytvoření vazby na umístění kódu.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Ladicí stroj (DE) implementuje toto rozhraní jako součást podpory zarážek.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Volání [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) vytvoří nevyřízenou zarážku z rozhraní [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) . Volání [metody bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) vytvoří `IDebugBreakpoint2` rozhraní, které představuje vázanou zarážku v programu.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IDebugPendingBreakpoint2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Určuje, zda tato nedokončená zarážka může vytvořit vazby na umístění kódu.|  
|[Zapisovat](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Váže tuto nevyřízenou zarážku na jedno nebo více umístění kódu.|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Získá stav této nedokončené zarážky.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Získá požadavek na zarážku, který se použil k vytvoření této nedokončené zarážky.|  
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Přepíná virtualizovaný stav této nedokončené zarážky.|  
|[Povolení](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Přepne povolený stav této nedokončené zarážky.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Nastaví nebo změní podmínku přidruženou k této nedokončené zarážce.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Nastaví nebo změní počet průchodů přidružených k této nedokončené zarážce.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Vytvoří výčet všech zarážek vázaných z této nedokončené zarážky.|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Vytvoří výčet všech zarážek s chybami, které byly výsledkem této nedokončené zarážky.|  
|[Odstranit](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Odstraní tuto nevyřízenou zarážku a všechny zarážky, které jsou z něho svázané.|  
  
## <a name="remarks"></a>Poznámky  
 `IDebugPendingBreakpoint2` lze si představit jako poskytovatel všech potřebných informací potřebných k navázání zarážky na kód, který lze použít na jeden nebo více programů.  
  
 Nevyřízená zarážka může potenciálně vytvořit více než jednu vázanou zarážku. Například zarážka v šabloně stylu C++ může vytvořit vázanou zarážku pro každou jedinečnou instanci této šablony.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
