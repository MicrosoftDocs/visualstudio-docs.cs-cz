---
title: Rozhraní Idebugapplicationthreadevents110 – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 5dd666d825c40155675714f5945209f22198993c
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984393"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 – rozhraní
Přidá další události vlákna. Tyto události jsou pouze místní. To znamená, že se můžete přihlásit k odběru pouze v laděném procesu pomocí [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) Advise a Unadvise pro objekty vláken PDM aplikace (objekty, které implementují [rozhraní idebugapplicationthread –](../../winscript/reference/idebugapplicationthread-interface.md)). Vyskytují se ve vláknu, ze kterého pocházejí.  
  
> [!IMPORTANT]
> Toto rozhraní je implementováno komponentou PDM verze 11.0 nebo novější. Nachází se v souboru activdbg100.h.  
  
## <a name="methods"></a>Metody  
 Rozhraní `IDebugActivationThreadEvents110` zpřístupňuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Bylo zahájeno volání do vlákna pomocí přepínání vlákna PDM.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Vlákno se obnovuje ze zarážky a bude opět aktivní.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Vlákno se pozastavuje pro zarážku a může zpracovávat volání, která vyžadují úplné pozastavení vlákna.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Volání do vlákna pomocí přepínání vlákna PDM bylo dokončeno.|