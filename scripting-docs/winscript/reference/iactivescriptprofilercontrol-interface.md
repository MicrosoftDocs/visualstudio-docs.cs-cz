---
title: Rozhraní IActiveScriptProfilerControl | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef127e3a4463d112b9ea424702fb2650c80cce7d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571596"
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl – rozhraní
Implementuje skriptovací modul, který podporuje profilování. Obvykle objekt, který implementuje `IActiveScriptProfilerControl`, implementuje také rozhraní [IActiveScript](../../winscript/reference/iactivescript.md) . V tomto případě můžete získat popisovač rozhraní `IActiveScriptProfilerControl` voláním metody `IUnknown::QueryInterface` objektu. Rozhraní poskytuje nezbytné metody pro zastavení a spuštění profilování v skriptovacím stroji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Spustí profilování v skriptovacím stroji.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Nastaví masku události profileru v skriptovacím stroji.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Zastaví profilování v skriptovacím stroji.|  
  
## <a name="see-also"></a>Viz také:  
 [Rozhraní profileru aktivních skriptů](../../winscript/reference/active-script-profiler-interfaces.md)