---
title: VSPerfCLREnv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: afee2c56a7f29d50f46c7cbb734bc0297223845c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64829035"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj VSPerfCLREnv slouží k nastavení proměnných prostředí, které jsou požadovány pro profilování aplikace .NET Framework. Používá následující syntaxi:  
  
```  
VsPerfCLREnv [/option]  
```  
  
 Možnost, kterou zvolíte, závisí na tom, jaké tři typy profilování používáte: vzorkování, instrumentace nebo globální. Pro zahrnutí dat interakce vrstev do dat profilace se vyžaduje samostatná možnost. Syntaxe pro každou možnost je popsána v následujících tabulkách.  
  
> [!NOTE]
> Po dokončení profilace spusťte **VSPerfCLREnv** pomocí možnosti **/off.** nebo **/globaloff** a odstraňte tak proměnné prostředí potřebné pro profilaci. Další informace najdete v tématu možnosti VSPerfCLREnv odstranění nastavení prostředí, které jsou tady uvedené.  
  
 **VSPerfCLREnv možnosti pro zahrnutí dat interakce vrstev**  
  
> [!WARNING]
> Profilování interakce vrstev lze shromažďovat pomocí sady [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] nebo [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Data profilování interakce vrstev ale můžete zobrazit jenom v [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] a [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] .  
  
 Profilace interakce vrstev poskytuje další informace o dotazech ADO.NET ve vícevrstvých aplikacích. Data jsou shromažďována pouze pro volání synchronních funkcí. Data interakce je možné přidat do libovolného profilování spouštěného pomocí libovolné metody profilace.  
  
 Možnosti **InteractionOn** a **GlobalInteractionOn** umožňují shromažďování dat interakce vrstev. Možnost interakce musí být nastavena po nastavení proměnné prostředí VSPerfCLREnv, která je vyžadována pro profilování aplikace.  
  
 Následující příklad obsahuje data interakce vrstev v běhu profilování, které používá metodu vzorkování:  
  
```  
VSPerfCLREnv /SampleOn  
VSPerfCLREnv /InteractionOn  
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe  
```  
  
 Následující příklad obsahuje data interakce vrstev při spuštění profilování pro službu systému Windows:  
  
```  
VSPerfCLREnv /GlobalSampleOn  
VSPerfCLREnv /GlobalInteractionOn  
REM Restart the computer and start the service  
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp   
VSPerfCmd /Attach:MyService.exe  
```  
  
 **VSPerfCLREnv možnosti pro profilaci instrumentace procesu**  
  
 Následující tabulka popisuje možnosti VSPerfCLREnv pro profilaci instrumentace:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**TraceOn**|Povoluje profilaci pomocí metody instrumentace. Nepovoluje profilaci přidělení paměti ani shromažďování dat o životnosti objektů.|  
|**TraceGC**|Povolí profilaci přidělení paměti pomocí metody instrumentace. Nepovoluje shromažďování dat o životnosti objektů.|  
|**TraceGCLife**|Umožňuje profilaci přidělení paměti a shromažďování dat o životnosti objektů pomocí metody instrumentace.|  
  
 **VSPerfCLREnv možnosti pro profilování vzorkování procesu**  
  
 Následující tabulka popisuje možnosti VSPerfCLREnv pro profilaci vzorkování:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**SampleOn**|Povoluje profilaci pomocí metody vzorkování. Nepovoluje profilaci přidělení paměti ani shromažďování dat o životnosti objektů.|  
|**SampleGC**|Povolí profilaci přidělení paměti pomocí metody vzorkování. Nepovoluje shromažďování dat o životnosti objektů.|  
|**SampleGCLife**|Povolí profilaci přidělení paměti pomocí metody vzorkování. Také umožňuje shromažďovat data o životnosti objektů.|  
|**SampleLineOff**|Zakáže shromažďování dat profilace na úrovni řádků .NET.|  
  
 **VSPerfCLREnv možnosti pro globální profilaci**  
  
 Chcete-li profilovat spravovanou službu, jako je například a ASP.NET webová aplikace, která je spuštěna operačním systémem, místo spuštění uživatelem, použijte možnosti pro globální profilaci možností VSPerfCLREnv. V následující tabulce jsou popsány globální verze VSPerfCLREnv možností. Tyto možnosti nastaví příslušné proměnné prostředí v registru.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**GlobalTraceOn**|Umožňuje globální profilaci pomocí metody instrumentace. Neshromažďuje události přidělení paměti nebo data o životnosti objektů.|  
|**GlobalTraceGC**|Povoluje profilaci globálních přidělení paměti pomocí metody instrumentace. Nepovoluje shromažďování dat o životnosti objektů.|  
|**GlobalTraceGCLife**|Povoluje profilaci globálních přidělení paměti pomocí metody instrumentace. Také umožňuje shromažďování dat o životnosti objektů.|  
|**GlobalSampleOn**|Umožňuje globální profilaci pomocí metody vzorkování. Nepovoluje shromažďování událostí přidělení paměti nebo dat o životnosti objektů.|  
|**GlobalSampleGC**|Povoluje profilaci globálních přidělení paměti pomocí metody vzorkování. Nepovoluje shromažďování dat o životnosti objektů.|  
|**GlobalSampleGCLife**|Povoluje profilaci globálních přidělení paměti pomocí metody vzorkování. Také umožňuje shromažďovat data o životnosti objektů.|  
  
 **VSPerfCLREnv možnosti odstranění nastavení prostředí**  
  
 Po dokončení profilace spravované aplikace použijte jednu z následujících možností k odstranění proměnných prostředí, které byly přidány pomocí VSPerfCLREnv. Následující tabulka popisuje, jak odstranit standardní i globální proměnné prostředí:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Vypnuto**|Odstraní proměnné prostředí pro profilování Standard .NET. Tuto možnost použijte, pokud se při nastavení proměnných prostředí profileru použily možnosti, které nejsou globální VSPerfClrEnv.|  
|**GlobalOff**|Odstraní proměnné prostředí pro globální profilaci .NET. Tuto možnost použijte, pokud aplikace byla spuštěna v operačním systému, nikoli v profileru.|  
  
## <a name="remarks"></a>Poznámky  
 Tyto možnosti nejsou požadovány pro profilování spravované aplikace, pokud je aplikace spuštěna pomocí Prohlížeč výkonu v integrovaném vývojovém prostředí (IDE). Prohlížeč výkonu nastaví všechna požadovaná nastavení prostředí.  
  
 Pokud během profilace nebylo nastaveno správné prostředí, během analýzy se zobrazí upozornění a názvy spravovaných funkcí nebudou správně vyřešeny.  
  
## <a name="see-also"></a>Viz také  
 [Profilace prostřednictvím příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
