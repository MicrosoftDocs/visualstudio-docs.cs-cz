---
title: VSPerfCLREnv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
ms.assetid: 4bc9dd6e-379c-4930-9bba-59a4faa93303
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ff359904b2b4d8b10dbc180f076606651028e80
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741507"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vsperfclrenv – nástroj slouží k nastavení proměnné prostředí, které je potřeba Profilovat aplikace rozhraní .NET Framework. Používá následující syntaxi:  
  
```  
VsPerfCLREnv [/option]  
```  
  
 Možnost, kterou zvolíte, závisí na, která ze tří typů profilace můžete použít: vzorkování, instrumentace, nebo globální. Možnost samostatného je nutný pro zahrnutí dat interakce vrstev v dat profilování. Syntaxe pro jednotlivé možnosti je popsána v následujících tabulkách.  
  
> [!NOTE]
>  Po dokončení profilace, spuštěná **VSPerfCLREnv** s **/ off** nebo **/globaloff** k odstranění proměnné prostředí pro profilování. Další informace najdete v tématu Možnosti vsperfclrenv – odstranit nastavení prostředí je vidět tady.  
  
 **Vsperfclrenv – možnosti pro zahrnutí dat interakce vrstev**  
  
> [!WARNING]
>  Profilování interakce vrstev lze shromažďovat pomocí sady [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] nebo [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Nicméně data profilace interakce vrstev lze zobrazit pouze v [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] a [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 Profilování interakce vrstev poskytuje další informace o dotazech technologie ADO.NET v víceúrovňových aplikací. Data se shromažďují pouze pro synchronní volání. Data interakce lze přidat k libovolné metodě profilování pomocí Profilování.  
  
 **InteractionOn** a **GlobalInteractionOn** možnosti Povolit shromažďování dat interakce vrstev. Po nastavení vsperfclrenv – proměnná prostředí, které je potřeba profil aplikace, musí být nastavena možnost interakce.  
  
 Následující příklad obsahuje dat interakce vrstev během spuštění profilování, která používá metody odběru vzorků:  
  
```  
VSPerfCLREnv /SampleOn  
VSPerfCLREnv /InteractionOn  
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe  
```  
  
 Následující příklad obsahuje dat interakce vrstev během spuštění profilování služby Windows:  
  
```  
VSPerfCLREnv /GlobalSampleOn  
VSPerfCLREnv /GlobalInteractionOn  
REM Restart the computer and start the service  
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp   
VSPerfCmd /Attach:MyService.exe  
```  
  
 **Vsperfclrenv – možnosti pro zpracování profilace instrumentace**  
  
 Následující tabulka popisuje možnosti vsperfclrenv – profilace instrumentace:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**TraceOn**|Umožňuje profilování pomocí metody instrumentace. Nepovolíte přidělení paměti pro profilaci nebo shromažďovat data o životním cyklu objektu.|  
|**TraceGC**|Umožňuje profilace přidělování paměti pomocí metody instrumentace. Nepovolí shromažďování data o životním cyklu objektu.|  
|**TraceGCLife**|Umožňuje přidělení paměti, profilování a shromažďovat data o životním cyklu objektu pomocí metody instrumentace.|  
  
 **Vsperfclrenv – možnosti pro profilaci vzorkování procesu**  
  
 Následující tabulka popisuje vsperfclrenv – možnosti pro profilaci vzorkování:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**SampleOn**|Umožňuje profilování pomocí metody vzorkování. Nepovolíte přidělení paměti pro profilaci nebo shromažďovat data o životním cyklu objektu.|  
|**SampleGC**|Umožňuje profilace přidělování paměti pomocí metody vzorkování. Nepovolí shromažďování data o životním cyklu objektu.|  
|**SampleGCLife**|Umožňuje profilace přidělování paměti pomocí metody vzorkování. Taky umožňuje shromažďování data o životním cyklu objektu.|  
|**SampleLineOff**|Zakáže kolekci .NET úrovně řádku dat profilování.|  
  
 **Vsperfclrenv – možnosti pro globální profilace**  
  
 Chcete-li Profilovat spravované služby, jako a webové aplikace ASP.NET, který je spuštěn v operačním systému místo spuštění uživatelem, pomocí možností globální profilace možnosti VSPerfCLREnv. Následující tabulka popisuje globální verze možnosti VSPerfCLREnv. Tyto možnosti nastavit příslušné proměnné prostředí v registru.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**GlobalTraceOn**|Povolí globální profilace pomocí metody instrumentace. Shromažďovat události přidělení paměti nebo data o životním cyklu objektu.|  
|**GlobalTraceGC**|Umožňuje profilace přidělování globální paměti pomocí metody instrumentace. Nepovolí shromažďování data o životním cyklu objektu.|  
|**GlobalTraceGCLife**|Umožňuje profilace přidělování globální paměti pomocí metody instrumentace. Také umožňuje shromažďování data o životním cyklu objektu.|  
|**GlobalSampleOn**|Povolí globální profilace pomocí metody vzorkování. Povolit shromažďování údajů o události přidělení paměti nebo data o životním cyklu objektu.|  
|**GlobalSampleGC**|Umožňuje profilace přidělování globální paměti pomocí metody vzorkování. Nepovolí shromažďování data o životním cyklu objektu.|  
|**GlobalSampleGCLife**|Umožňuje profilace přidělování globální paměti pomocí metody vzorkování. Taky umožňuje shromažďování data o životním cyklu objektu.|  
  
 **Vsperfclrenv – možnosti odstranit nastavení prostředí**  
  
 Po dokončení profilace spravované aplikace, použijte jednu z následujících možností odstranění proměnné prostředí, které byly přidány pomocí VSPerfCLREnv. Následující tabulka popisuje, jak odstranit i standardní a globální proměnné:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Vypnout**|Vymaže proměnné prostředí pro profilování standardní .NET. Tuto možnost použijte, pokud neglobální vsperfclrenv – možnosti byly použity k nastavení proměnných prostředí profilování.|  
|**GlobalOff**|Vymaže proměnné prostředí pro profilování globální .NET. Tuto možnost použijte v případě spuštění aplikace podle operačního systému a ne profileru.|  
  
## <a name="remarks"></a>Poznámky  
 Tyto možnosti se nevyžadují pro profilaci spravované aplikace, pokud je aplikace spuštěna s použitím Průzkumníka výkonu v rozhraní IDE. Prohlížeč výkonu nastaví všechny požadované prostředí nastavení za vás.  
  
 Pokud během profilování nebyl nastaven správné prostředí, upozornění je hlášeno během analýzy a spravované funkce, nebude správně přeložit názvy.  
  
## <a name="see-also"></a>Viz také  
 [Profilace prostřednictvím příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)



