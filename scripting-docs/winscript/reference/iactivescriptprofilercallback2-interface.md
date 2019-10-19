---
title: Rozhraní Iactivescriptprofilercallback2 – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25f9616497192659df67feedfe16bd9ea0c5e3b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577305"
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2 – rozhraní
Poskytuje metody, které skriptovací stroj používá k oznamování objektu profileru, když dojde k události model DOM (Document Object Model) (DOM). Toto rozhraní je implementováno pomocí objektu profileru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Upozorní objekt profileru na to, že skriptovací stroj spustí volání funkce modelu DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Upozorní objekt profileru, že skriptovací modul dokončil běh volání funkce DOM.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `IActiveScriptProfilerCallback2` nejprve vydaná s Internet Explorerem 9.  
  
 Oznámení o voláních funkcí, která nejsou volána do modelu DOM, jsou poskytována [rozhraním iactivescriptprofilercallback –](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
> Chcete-li přidat možnost spustit a zastavit profilování při spuštění skriptu, zavolejte následující metody. Pomocí těchto metod můžete získat kompletní zásobník volání, pokud při spuštění nebo zastavení profilování běží [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
> 
> - Voláním [iactivescriptprofilercontrol2 –:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) upozorněte profileru, že jste spustili profilaci.  
>   - Zavolejte [iactivescriptprofilercontrol2 –::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) pro upozorňování profileru, že brzy zastavíte profilaci.  
  
## <a name="see-also"></a>Viz také:  
 [Rozhraní profileru aktivních skriptů](../../winscript/reference/active-script-profiler-interfaces.md)