---
title: IDebugStackFrame3 | Dokumentace Microsoftu
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
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e09851f4cfd8418db8b11a08f0ba13a5a133b94
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791940"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní rozšiřuje [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) zpracovat zachycené výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Ladicí stroj (DE) implementuje na stejný objekt, který implementuje toto rozhraní [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) rozhraní pro podporu zachycené výjimky.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Volání [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) na `IDebugStackFrame2` rozhraní k získání tohoto rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Kromě metod zděděných z [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` poskytuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Zpracovává výjimku pro aktuální rámec zásobníku před zpracování jakékoli pravidelné výjimek.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Vrátí kontext kódu, pokud dojde k odvíjení zásobníku.|  
  
## <a name="remarks"></a>Poznámky  
 Zachycené výjimky znamená, že ladicí program může zpracovat výjimku před voláním jakékoli normální obslužné rutiny jsou podle času spuštění. Zachycení výjimky v podstatě znamená, že čas spuštění předstírají, že má obslužné rutiny výjimek i v případě, že není k dispozici.  
  
 [Interceptcurrentexception –](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) je volána v průběhu všech událostí zpětného volání normální výjimkou (jedinou výjimkou je, pokud ladění ve smíšeném režimu kódu (spravovaného a nespravovaného kódu), v takovém případě nemůže být zachycena výjimka během zpětné volání poslední odpovídající). Pokud je DE neimplementuje `IDebugStackFrame3`, nebo Německo vrátí chybu z IDebugStackFrame3::`InterceptCurrentException` (například `E_NOTIMPL`), pak ladicí program bude obvykle zpracování výjimky.  
  
 Tím, že zachytává výjimku, ladicí program umožňuje uživatelům provádět změny stavu laděného programu a potom pokračovat v provádění v místě, kde byla výjimka vydána.  
  
> [!NOTE]
>  Zachycené výjimky jsou povoleny pouze ve spravovaném kódu, tedy v programu, který běží v části Common Language Runtime (CLR).  
  
 Ladicí stroj označuje, že ji podporuje prověřuje zachycovací výjimky tak, že nastavíte "metricExceptions" na hodnotu 1 za běhu pomocí `SetMetric` funkce. Další informace najdete v tématu [Pomocníci sad SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Pomocníci sad SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

