---
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6114a31701e5abc4714f315b4e4f1ecf022c401c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163815"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní používá modul ladění (DE) k odesílání událostí ladění do Správce ladění relace (SDM).  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] implementuje toto rozhraní pro příjem událostí z ladicího stroje.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Ladicí stroj obvykle obdrží toto rozhraní, když volání SDM [připojí](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [připojí](../../../extensibility/debugger/reference/idebugengine2-attach.md)nebo [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Ladicí stroj odesílá události do modelu SDM voláním [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IDebugEventCallback2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Pošle oznámení o událostech ladění do SDM.|  
  
## <a name="remarks"></a>Poznámky  
 I když [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) a [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) určují, že přebírají `IDebugEventCallback2` rozhraní, toto není případ a ukazatel rozhraní bude vždy hodnota null. Místo toho musí ladicí stroj použít `IDebugEventCallback2` rozhraní přijaté ve volání k [připojení](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [připojení](../../../extensibility/debugger/reference/idebugengine2-attach.md)nebo [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Pokud balíček implementuje [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) ve spravovaném kódu, důrazně doporučujeme, abyste jej <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> vyvolali v různých rozhraních, která jsou předána [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Pojovat](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
