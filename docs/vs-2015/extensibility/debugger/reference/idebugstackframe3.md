---
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d63d4dcd6e3b7a3b81504b485ee710779cef3c13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688539"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní rozšiřuje [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) a zpracovává zachycené výjimky.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Ladicí stroj (DE) implementuje toto rozhraní u stejného objektu, který implementuje rozhraní [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pro podporu zachycených výjimek.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) `IDebugStackFrame2` Chcete-li získat toto rozhraní, zavolejte na rozhraní QueryInterface.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 Kromě metod zděděných z [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) `IDebugStackFrame3` zpřístupňuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Zpracovává výjimku pro aktuální rámec zásobníku před jakýmkoli pravidelným zpracováním výjimek.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Vrátí kontext kódu, pokud by došlo k odvíjení zásobníku.|  
  
## <a name="remarks"></a>Poznámky  
 Zachycená výjimka znamená, že ladicí program může zpracovat výjimku před všemi běžnými rutinami zpracování výjimky, které jsou volány za běhu. Zachycení výjimky v podstatě znamená, že doba běhu předstírat, že je přítomna obslužná rutina výjimky, i když není.  
  
 [InterceptCurrentException –](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) je volána během všech běžných událostí zpětného volání výjimky (jedinou výjimkou je, když ladíte kód smíšeného režimu (spravovaný a nespravovaný kód), v takovém případě nelze výjimku zachytit během zpětného volání s poslední pravděpodobností. Pokud DE neimplementuje `IDebugStackFrame3` nebo de vrátí chybu z IDebugStackFrame3:: `InterceptCurrentException` (například `E_NOTIMPL` ), pak ladicí program zpracuje výjimku normálně.  
  
 Pomocí zachycení výjimky může ladicí program umožnit uživateli provádět změny ve stavu laděného programu a poté pokračovat v provádění v místě, kde byla výjimka vyvolána.  
  
> [!NOTE]
> Zachycené výjimky jsou povoleny pouze ve spravovaném kódu, to znamená v programu, který je spuštěn pod modulem CLR (Common Language Runtime).  
  
 Ladicí stroj indikuje, že podporuje zachycení výjimek nastavením "metricExceptions" na hodnotu 1 v době běhu pomocí `SetMetric` funkce. Další informace najdete v tématech [pomocníka sady SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Pomocníci sad SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
