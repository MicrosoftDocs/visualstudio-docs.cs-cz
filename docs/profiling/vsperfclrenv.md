---
title: Vsperfclrenv – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5623cfc9d6f72805e4ced489ef7a786aaad155e6
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34446228"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

Vsperfclrenv – nástroj slouží k nastavení proměnných prostředí, které jsou nutné k profilu aplikace rozhraní .NET Framework. Používá následující syntaxi:

```cmd
VsPerfCLREnv [/option]
```

Možnost, který zvolíte, závisí na které ze tří typů profilace můžete použít: vzorkování, instrumentace, nebo globální. Samostatnou možností je potřeba zahrnout dat interakce vrstev data profilování. Syntaxe pro jednotlivé možnosti je popsané v následujících tabulkách.

> [!NOTE]
> Po dokončení profilování, spusťte **vsperfclrenv –** s **/ vypnuto** nebo **/globaloff** možnost ke smazání potřebné pro profilace proměnné prostředí. Další informace najdete v tématu Možnosti vsperfclrenv – odstranit nastavení prostředí zobrazeny zde.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>Vsperfclrenv – možnosti včetně dat sledování interakce vrstev

> [!WARNING]
> Profilace interakce vrstvy můžete shromáždit pomocí libovolná edice sady Visual Studio. Data profilace sledováním interakce vrstev však lze zobrazit pouze ve Visual Studio Enterprise.

Profilace interakce vrstvy poskytuje další informace o dotazech ADO.NET ve víceúrovňových aplikací. Data jsou shromažďována jenom pro funkce synchronní volání. Interakce data lze přidat do jakékoli profilování spustit pomocí libovolné metody profilování.

**InteractionOn** a **GlobalInteractionOn** možnosti Povolit shromažďování dat interakce vrstev. Po nastavení vsperfclrenv – proměnná prostředí, které je třeba, aby profil aplikace, musí být nastavena možnost interakce.

Následující příklad obsahuje dat interakce vrstev v profilaci spuštění, které používá metody vzorkování:

```cmd
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

Následující příklad obsahuje dat interakce vrstev při vytváření profilů spuštění pro službu systému Windows:

```cmd
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp 
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>Vsperfclrenv – možnosti pro proces profilace instrumentace

Následující tabulka popisuje možnosti vsperfclrenv – profilace instrumentace:

|Možnost|Popis|
|------------|-----------------|
|**TraceOn**|Povolí použití profilů pomocí metody instrumentace. Přidělení paměti profilace nebo shromažďování životnosti objektů není povolen.|
|**TraceGC**|Umožňuje pomocí metody instrumentace profilace přidělení paměti. Neumožňuje shromažďování životnosti objektů.|
|**TraceGCLife**|Umožňuje přidělení paměti profilace a shromažďování životnosti objektů pomocí metody instrumentace.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>Vsperfclrenv – možnosti pro proces profilace se vzorkováním

Následující tabulka popisuje možnosti vsperfclrenv – profilace se vzorkováním:

|Možnost|Popis|
|------------|-----------------|
|**SampleOn**|Povolí použití profilů pomocí metody vzorkování. Přidělení paměti profilace nebo shromažďování životnosti objektů není povolen.|
|**SampleGC**|Umožňuje pomocí metody vzorkování profilace přidělení paměti. Neumožňuje shromažďování životnosti objektů.|
|**SampleGCLife**|Umožňuje pomocí metody vzorkování profilace přidělení paměti. Taky umožňuje shromažďování životnosti objektů.|
|**SampleLineOff**|Zakáže kolekce .NET úrovni řádků profilace data.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>Vsperfclrenv – možnosti pro globální profilace

Do profilu, jako spravované služby a webové aplikace ASP.NET, který je spuštěn v operačním systému místo spuštění uživatelem, použijte možnosti pro globální profilace vsperfclrenv – možnosti. Následující tabulka popisuje globálního verzích vsperfclrenv – možnosti. Tyto možnosti nastavit příslušné proměnné prostředí v registru.

|Možnost|Popis|
|------------|-----------------|
|**GlobalTraceOn**|Povolí globální profilace pomocí metody instrumentace. Neshromažďuje události přidělení paměti nebo životnosti objektů.|
|**GlobalTraceGC**|Povolí globální paměť přidělení profilace pomocí metody instrumentace. Neumožňuje shromažďování životnosti objektů.|
|**GlobalTraceGCLife**|Povolí globální paměť přidělení profilace pomocí metody instrumentace. Taky umožňuje kolekce životnosti objektů.|
|**GlobalSampleOn**|Povolí globální profilace pomocí metody vzorkování. Neumožňuje shromažďování událostí přidělení paměti nebo životnosti objektů.|
|**GlobalSampleGC**|Povolí globální paměť přidělení profilace pomocí metody vzorkování. Neumožňuje shromažďování životnosti objektů.|
|**GlobalSampleGCLife**|Povolí globální paměť přidělení profilace pomocí metody vzorkování. Taky umožňuje shromažďování životnosti objektů.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>Vsperfclrenv – možnosti odstranit nastavení prostředí

 Po skončení profilace spravované aplikace, použijte jednu z následujících možností odstranit proměnných prostředí, které byly přidány pomocí vsperfclrenv –. Následující tabulka popisuje, jak odstranit obě prostředí standardní a globální proměnné:

|Možnost|Popis|
|------------|-----------------|
|**Vypnout**|Odstraní proměnných prostředí pro standardní profilace rozhraní .NET. Tuto možnost použijte, když neglobální vsperfclrenv – možnosti jste použili k nastavení profileru proměnných prostředí.|
|**GlobalOff**|Odstraní proměnných prostředí pro globální profilace rozhraní .NET. Tuto možnost použijte, když byla aplikace spuštěna operační systém a není profileru.|

## <a name="remarks"></a>Poznámky

Tyto možnosti se nevyžadují profilace spravované aplikace, pokud je aplikace spuštěna pomocí Průzkumníku výkonu v prostředí IDE. Prohlížeč výkonu nastaví všechny požadované prostředí nastavení za vás.

Pokud během profilace nebyl nastaven správný prostředí, upozornění je zaznamenána během analýzy a spravovaná funkce, které názvy nebudou správně rozpoznány.

## <a name="see-also"></a>Viz také

[Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)