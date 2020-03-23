---
title: VSPerfCLREnv | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2163ebb9b363de8ee638998dbe56fd76f5a891c8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779906"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

Nástroj VSPerfCLREnv se používá k nastavení proměnných prostředí, které jsou nutné k profilování aplikace rozhraní .NET Framework. Používá následující syntaxi:

```cmd
VsPerfCLREnv [/option]
```

Možnost, kterou zvolíte, závisí na tom, které ze tří typů profilování používáte: vzorkování, instrumentace nebo globální. Samostatná možnost je nutné zahrnout data interakce vrstvy v datech profilování. Syntaxe pro každou možnost je popsána v následujících tabulkách.

> [!NOTE]
> Po dokončení profilování spusťte **VSPerfCLREnv** s možností **/off** nebo **/globaloff** k odstranění proměnných prostředí nezbytných pro profilování. Další informace naleznete v tématu VSPerfCLREnv Možnosti odstranit nastavení prostředí zde.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>Možnosti VSPerfCLREnv pro zahrnutí dat interakce s vrstvou

> [!WARNING]
> Profilování interakce úrovně lze shromažďovat pomocí libovolné edice sady Visual Studio. Data profilování interakce vrstvy však lze zobrazit pouze v sadě Visual Studio Enterprise.

Profilování interakce vrstvy poskytuje další informace o ADO.NET dotazech v aplikacích s více vrstvami. Data jsou shromažďována pouze pro synchronní volání funkcí. Data interakce lze přidat do libovolného profilování spustit pomocí libovolné metody profilování.

**Interna** a **GlobalInteractionOn** možnosti umožňují shromažďování dat interakce vrstvy. Možnost interakce musí být nastavena po nastavení proměnné prostředí VSPerfCLREnv, která je vyžadována pro profil ování aplikace.

Následující příklad zahrnuje data interakce vrstvy v profilovacím běhu, který používá metodu vzorkování:

```cmd
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

Následující příklad zahrnuje data interakce vrstvy v profilovacím spuštění služby systému Windows:

```cmd
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>Možnosti VSPerfCLREnv pro profilování procesní instrumentace

Následující tabulka popisuje možnosti VSPerfCLREnv pro profilování instrumentace:

|Možnost|Popis|
|------------|-----------------|
|**Traceon**|Umožňuje profilování pomocí metody instrumentace. Neumožňuje profilování přidělení paměti nebo shromažďování dat životnosti objektu.|
|**TraceGC**|Umožňuje profilování přidělení paměti pomocí metody instrumentace. Neumožňuje shromažďování dat životnosti objektu.|
|**TraceGCLife**|Umožňuje profilování přidělení paměti a shromažďování dat životnosti objektu pomocí metody instrumentace.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>Možnosti VSPerfCLREnv pro profilování vzorkování procesů

Následující tabulka popisuje možnosti VSPerfCLREnv pro profilování vzorkování:

|Možnost|Popis|
|------------|-----------------|
|**Sampleon**|Umožňuje profilování pomocí metody vzorkování. Neumožňuje profilování přidělení paměti nebo shromažďování dat životnosti objektu.|
|**SampleGC**|Umožňuje profilování přidělení paměti pomocí metody vzorkování. Neumožňuje shromažďování dat životnosti objektu.|
|**SampleGCLife**|Umožňuje profilování přidělení paměti pomocí metody vzorkování. Také umožňuje shromažďování dat životnosti objektu.|
|**Odběr vzorkuLineOff**|Zakáže shromažďování dat profilování na úrovni řádku .NET.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>Možnosti VSPerfCLREnv pro globální profilování

Chcete-li profilovat spravovanou službu, například a ASP.NET webové aplikace, která je spuštěna operačním systémem namísto spuštění uživatelem, použijte možnosti pro globální profilování možností VSPerfCLREnv. Následující tabulka popisuje globální verze možností VSPerfCLREnv. Tyto možnosti nastavit příslušné proměnné prostředí v registru.

|Možnost|Popis|
|------------|-----------------|
|**GlobálníTraceon**|Umožňuje globální profilování pomocí metody instrumentace. Neshromažďuje události přidělení paměti nebo data životnosti objektu.|
|**GlobálníTraceGC**|Umožňuje profilování globálního přidělení paměti pomocí metody instrumentace. Neumožňuje shromažďování dat životnosti objektu.|
|**GlobálníTraceGCLife**|Umožňuje profilování globálního přidělení paměti pomocí metody instrumentace. Také umožňuje shromažďování dat životnost objektu.|
|**Globální sampleon**|Umožňuje globální profilování pomocí metody vzorkování. Neumožňuje shromažďování událostí přidělení paměti nebo dat životnosti objektu.|
|**GlobalSampleGC**|Umožňuje profilování globálního přidělení paměti pomocí metody vzorkování. Neumožňuje shromažďování dat životnosti objektu.|
|**GlobalSampleGCLife**|Umožňuje profilování globálního přidělení paměti pomocí metody vzorkování. Také umožňuje shromažďování dat životnosti objektu.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>Možnosti VSPerfCLREnv pro odstranění nastavení prostředí

 Po dokončení profilování spravované aplikace použijte jednu z následujících možností k odstranění proměnných prostředí, které byly přidány vSPerfCLREnv. Následující tabulka popisuje, jak odstranit standardní i globální proměnné prostředí:

|Možnost|Popis|
|------------|-----------------|
|**Vypnuto**|Odstraní proměnné prostředí pro standardní profilování .NET. Tuto možnost použijte, pokud byly k nastavení proměnných prostředí profileru použity neglobální možnosti VSPerfClrEnv.|
|**GlobalOff**|Odstraní proměnné prostředí pro globální profilování .NET. Tuto možnost použijte, pokud byla aplikace spuštěna operačním systémem a nikoli profilerem.|

## <a name="remarks"></a>Poznámky

Tyto možnosti nejsou vyžadovány pro profilování spravované aplikace, pokud je aplikace spuštěna pomocí Průzkumníka výkonu v rozhraní IDE. Průzkumník výkonu nastaví všechna požadovaná nastavení prostředí za vás.

Pokud nebylo během profilování nastaveno správné prostředí, během analýzy se zobrazí upozornění a názvy spravovaných funkcí nebudou správně vyřešeny.

## <a name="see-also"></a>Viz také

[Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
