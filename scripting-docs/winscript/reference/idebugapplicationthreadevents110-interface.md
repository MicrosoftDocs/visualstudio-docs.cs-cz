---
title: Idebugapplicationthreadevents110 – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aaf312b1730696b812172aeea175619e911d03a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794034"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 – rozhraní
Přidá další vlákno události. Tyto události jsou pouze místní. To znamená, můžete se přihlásíte k nim pouze v procesu, ve ladit, pomocí [IConnectionPoint –](http://go.microsoft.com/fwlink/?LinkId=232738) poradit a unadvise metody na objekty vláken aplikace PDM (objekty, které implementují [idebugapplicationthread – Rozhraní](../../winscript/reference/idebugapplicationthread-interface.md)). K nim dojde na vlákno, které pocházejí z.  
  
> [!IMPORTANT]
>  Toto rozhraní je implementováno komponentou PDM verze 11.0 nebo novější. Nachází se v souboru activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IDebugActivationThreadEvents110` Rozhraní poskytuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Idebugapplicationthreadevents110 –:: OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Volání do vlákno pomocí PDM vlákno přepínání zahájení.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Vlákno obnovuje z zarážku a bude active ještě jednou.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Vlákno je pozastavení pro zarážku a dokáže zpracovat volání, které vyžadují vlákno plně pozastaví.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Volání do vlákno pomocí PDM vlákno přepínání byla dokončena.|