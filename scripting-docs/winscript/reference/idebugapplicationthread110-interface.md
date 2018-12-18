---
title: Idebugapplicationthread110 – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aee30ae68319810f58bf31f8d0eb32cf8f30d34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794058"
---
# <a name="idebugapplicationthread110-interface"></a>IDebugApplicationThread110 – rozhraní
Poskytuje další funkce pro [idebugapplicationthread – rozhraní](../../winscript/reference/idebugapplicationthread-interface.md) rozhraní.  
  
> [!IMPORTANT]
>  Toto rozhraní je implementováno komponentou PDM verze 11.0 nebo novější. Nachází se v souboru activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IDebugApplicationThread110` Rozhraní poskytuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Provede asynchronní volání na hlavní vlákno.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Počet počet požadavků na přístup z více vláken z vlákna PDM přepínání mechanismy se právě zpracovává. Obvykle 0 nebo 1, ale je možné, že to být vyšší, pokud jedno vlákno volání spuštění zpracování, ale aktivuje synchronní volání mimo vlákna nebo jinak pozastaví vlákno (například podle aktivuje událost IDebugApplicationEvents, což je vydané pro ladicí program přístup z více vláken)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) byla volána na tento přístup z více vláken a zatím není dokončený.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Tento přístup z více vláken je ve stavu, který může zpracovat volání provedená pomocí PDM vlákno přepínání mechanismy (například SynchronousCallInThread).|