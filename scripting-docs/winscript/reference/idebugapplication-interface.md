---
title: Idebugapplication – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07964292785634212099a0bfcf8174ebb55e8713
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794385"
---
# <a name="idebugapplication-interface"></a>IDebugApplication – rozhraní
Zpřístupní bez vzdáleného ladění metody pro použití strojů jazyka a hostitele.  
  
 Kromě metod zděděno z `IRemoteDebugApplication`, `IDebugApplication` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Nastaví název aplikace.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Oznámí správci ladění procesu, že modul jazyka v režimu krokování se vrátit do jeho volajícího.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Způsobí, že daný řetězec, který má být zobrazeny v ladicím programu IDE.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Spustí výchozí program pro ladění IDE a připojí na relaci ladění aplikace, pokud již není připojen.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Způsobí, že aktuální vlákno blokování a odešle oznámení bod přerušení ladicího programu IDE.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Způsobí, že tuto aplikaci chcete uvolnit všechny odkazy a zadejte neaktivním stavu.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Vrátí aktuální rozdělení příznaky pro aplikaci.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Vrátí vlákno spojené s aktuálně spuštěných vláken.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Poskytuje asynchronní přístup k dané ladění synchronní operace.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Přidá zprostředkovatele enumerátor rámce zásobníku do této aplikace.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Odebere poskytovatele enumerátor rámce zásobníku z této aplikace.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Určuje, zda aktuální vlákno spuštěných vláken ladicí program.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Poskytuje mechanismus pro volajícího, aby spuštění kódu v vlákno ladicí program.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Vytvoří nový uzel aplikace, který je přidružen konkrétní dokumentu zprostředkovatele.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Aktivuje obecné událost do ladicího programu `IApplicationDebugger` rozhraní.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Způsobí, že aktuální vlákno blokování a odešle oznámení chyby ladicího programu IDE.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Určuje, zda je zaregistrován ladicí program za běhu (JIT).|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Určuje, zda je zaregistrován ladicí program JIT vlečný hostitelům automatické ladění.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Přidá zprostředkovatele kontextu globálním výrazu do této aplikace.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Kontext zprostředkovatele globálním výrazu odebere z této aplikace.|