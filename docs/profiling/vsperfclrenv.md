---
title: VSPerfCLREnv | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779906"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

Nástroj VSPerfCLREnv slouží k nastavení proměnných prostředí, které jsou požadovány pro profilování aplikace .NET Framework. Používá následující syntaxi:

```cmd
VsPerfCLREnv [/option]
```

Možnost, kterou zvolíte, závisí na tom, jaké tři typy profilování používáte: vzorkování, instrumentace nebo globální. Pro zahrnutí dat interakce vrstev do dat profilace se vyžaduje samostatná možnost. Syntaxe pro každou možnost je popsána v následujících tabulkách.

> [!NOTE]
> Po dokončení profilace spusťte **VSPerfCLREnv** pomocí možnosti **/off.** nebo **/globaloff** a odstraňte tak proměnné prostředí potřebné pro profilaci. Další informace najdete v tématu možnosti VSPerfCLREnv odstranění nastavení prostředí, které jsou tady uvedené.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>VSPerfCLREnv možnosti pro zahrnutí dat interakce vrstev

> [!WARNING]
> Profilace interakce vrstev se dá shromáždit pomocí libovolné edice sady Visual Studio. Data profilování interakce vrstev ale můžete zobrazit jenom v Visual Studio Enterprise.

Profilace interakce vrstev poskytuje další informace o dotazech ADO.NET ve vícevrstvých aplikacích. Data jsou shromažďována pouze pro volání synchronních funkcí. Data interakce je možné přidat do libovolného profilování spouštěného pomocí libovolné metody profilace.

Možnosti **InteractionOn** a **GlobalInteractionOn** umožňují shromažďování dat interakce vrstev. Možnost interakce musí být nastavena po nastavení proměnné prostředí VSPerfCLREnv, která je vyžadována pro profilování aplikace.

Následující příklad obsahuje data interakce vrstev v běhu profilování, které používá metodu vzorkování:

```cmd
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

Následující příklad obsahuje data interakce vrstev při spuštění profilování pro službu systému Windows:

```cmd
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>VSPerfCLREnv možnosti pro profilaci instrumentace procesu

Následující tabulka popisuje možnosti VSPerfCLREnv pro profilaci instrumentace:

|Možnost|Popis|
|------------|-----------------|
|**TraceOn**|Povoluje profilaci pomocí metody instrumentace. Nepovoluje profilaci přidělení paměti ani shromažďování dat o životnosti objektů.|
|**TraceGC**|Povolí profilaci přidělení paměti pomocí metody instrumentace. Nepovoluje shromažďování dat o životnosti objektů.|
|**TraceGCLife**|Umožňuje profilaci přidělení paměti a shromažďování dat o životnosti objektů pomocí metody instrumentace.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>VSPerfCLREnv možnosti pro profilování vzorkování procesu

Následující tabulka popisuje možnosti VSPerfCLREnv pro profilaci vzorkování:

|Možnost|Popis|
|------------|-----------------|
|**SampleOn**|Povoluje profilaci pomocí metody vzorkování. Nepovoluje profilaci přidělení paměti ani shromažďování dat o životnosti objektů.|
|**SampleGC**|Povolí profilaci přidělení paměti pomocí metody vzorkování. Nepovoluje shromažďování dat o životnosti objektů.|
|**SampleGCLife**|Povolí profilaci přidělení paměti pomocí metody vzorkování. Také umožňuje shromažďovat data o životnosti objektů.|
|**SampleLineOff**|Zakáže shromažďování dat profilace na úrovni řádků .NET.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>VSPerfCLREnv možnosti pro globální profilaci

Chcete-li profilovat spravovanou službu, jako je například a ASP.NET webová aplikace, která je spuštěna operačním systémem, místo spuštění uživatelem, použijte možnosti pro globální profilaci možností VSPerfCLREnv. V následující tabulce jsou popsány globální verze VSPerfCLREnv možností. Tyto možnosti nastaví příslušné proměnné prostředí v registru.

|Možnost|Popis|
|------------|-----------------|
|**GlobalTraceOn**|Umožňuje globální profilaci pomocí metody instrumentace. Neshromažďuje události přidělení paměti nebo data o životnosti objektů.|
|**GlobalTraceGC**|Povoluje profilaci globálních přidělení paměti pomocí metody instrumentace. Nepovoluje shromažďování dat o životnosti objektů.|
|**GlobalTraceGCLife**|Povoluje profilaci globálních přidělení paměti pomocí metody instrumentace. Také umožňuje shromažďování dat o životnosti objektů.|
|**GlobalSampleOn**|Umožňuje globální profilaci pomocí metody vzorkování. Nepovoluje shromažďování událostí přidělení paměti nebo dat o životnosti objektů.|
|**GlobalSampleGC**|Povoluje profilaci globálních přidělení paměti pomocí metody vzorkování. Nepovoluje shromažďování dat o životnosti objektů.|
|**GlobalSampleGCLife**|Povoluje profilaci globálních přidělení paměti pomocí metody vzorkování. Také umožňuje shromažďovat data o životnosti objektů.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>VSPerfCLREnv možnosti odstranění nastavení prostředí

 Po dokončení profilace spravované aplikace použijte jednu z následujících možností k odstranění proměnných prostředí, které byly přidány pomocí VSPerfCLREnv. Následující tabulka popisuje, jak odstranit standardní i globální proměnné prostředí:

|Možnost|Popis|
|------------|-----------------|
|**Zaokrouhl**|Odstraní proměnné prostředí pro profilování Standard .NET. Tuto možnost použijte, pokud se při nastavení proměnných prostředí profileru použily možnosti, které nejsou globální VSPerfClrEnv.|
|**GlobalOff**|Odstraní proměnné prostředí pro globální profilaci .NET. Tuto možnost použijte, pokud aplikace byla spuštěna v operačním systému, nikoli v profileru.|

## <a name="remarks"></a>Poznámky

Tyto možnosti nejsou požadovány pro profilování spravované aplikace, pokud je aplikace spuštěna pomocí Prohlížeč výkonu v integrovaném vývojovém prostředí (IDE). Prohlížeč výkonu nastaví všechna požadovaná nastavení prostředí.

Pokud během profilace nebylo nastaveno správné prostředí, během analýzy se zobrazí upozornění a názvy spravovaných funkcí nebudou správně vyřešeny.

## <a name="see-also"></a>Viz také:

[Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
