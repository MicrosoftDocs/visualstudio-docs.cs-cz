---
title: Rozhraní Iactivescriptprofilercallback – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ae520dcb36e00dfaba8702db6294a5a47484b0a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571710"
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback – rozhraní
Poskytuje metody, které skriptovací stroj používá k oznamování objektu profileru, když dojde k událostem. Toto rozhraní je implementováno pomocí objektu profileru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Volá se, aby se inicializoval objekt profileru, když se v skriptovacím modulu spustí profilace.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Volá se, aby se uvolnil a uvolnil objekt profileru, když se profilování zastaví na skriptovacím stroji.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Upozorní objekt profileru, že skriptovací stroj zkompiluje skript.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Upozorní objekt profileru, že skriptovací stroj zaznamenal funkci při kompilování skriptu.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Upozorní objekt profileru, že skriptovací stroj provede volání funkce, která není volána do model DOM (Document Object Model) (DOM).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Upozorní objekt profileru, že skriptovací modul dokončil provádění volání funkce, které není voláním do modelu DOM.|  
  
## <a name="remarks"></a>Poznámky  
 Oznámení volání funkcí do model DOM (Document Object Model) (DOM) je poskytováno [rozhraním iactivescriptprofilercallback2 –](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
> Chcete-li přidat možnost spustit a zastavit profilování při spuštění skriptu, zavolejte následující metody. Pomocí těchto metod můžete získat kompletní zásobník volání, pokud při spuštění nebo zastavení profilování běží [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
> 
> - Voláním [iactivescriptprofilercontrol2 –:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) upozorněte profileru, že jste spustili profilaci.  
>   - Zavolejte [iactivescriptprofilercontrol2 –::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) pro upozorňování profileru, že brzy zastavíte profilaci.  
  
## <a name="see-also"></a>Viz také:  
 [Rozhraní profileru aktivních skriptů](../../winscript/reference/active-script-profiler-interfaces.md)