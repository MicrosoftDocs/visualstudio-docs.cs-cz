---
title: Iactivescriptprofilercontrol – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d598302ae78ca0b2a1e7c1f94c949800378a2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793494"
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl – rozhraní
Implementované skriptovací stroj, který podporuje vytváření profilů. Obvykle objekt, který implementuje `IActiveScriptProfilerControl` také implementuje [IActiveScript –](../../winscript/reference/iactivescript.md) rozhraní. V takovém případě můžete získat popisovač pro `IActiveScriptProfilerControl` rozhraní voláním `IUnknown::QueryInterface` metoda v objektu. Rozhraní poskytuje nezbytné metody pro ukončení a opětovném spuštění profilace na skriptovacího stroje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Spustí se profilace na skriptovacího stroje.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Nastaví profileru maska událostí v skriptovacího stroje.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Zastaví profilace na skriptovacího stroje.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní profileru aktivních skriptů](../../winscript/reference/active-script-profiler-interfaces.md)