---
title: Měření výkonu z příkazového řádku
description: Změřte výkon procesoru a využití spravované paměti ve vaší aplikaci z příkazového řádku.
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, command-line
- Diagnostics Tools, command-line
- CPU Usage, command-line
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: c109e2ae1db28f8e08ed7c34a7ee0871a6efe670
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558118"
---
# <a name="measure-application-performance-from-the-command-line"></a>Měření výkonu aplikace z příkazového řádku

Pomocí nástrojů příkazového řádku můžete shromažďovat informace o výkonu aplikace.

V příkladu popsaném v tomto článku shromažďujete informace o výkonu pro Microsoft Notepad, ale stejnou metodu lze použít k profilování jakéhokoli procesu.

## <a name="prerequisites"></a>Předpoklady

* Visual Studio 2019 Preview 3 nebo novější verze

* Znalost nástrojů příkazového řádku

## <a name="collect-performance-data"></a>Shromažďování údajů o výkonu

Profilace pomocí nástrojů rozhraní příkazového řádku Visual Studio Diagnostics funguje tak, že k procesu připojí nástroj pro profilaci společně s jedním z agentů kolektoru. Když připojíte nástroj profilace, zahájíte relaci diagnostiky, která zachycuje a ukládá data profilování, dokud se nástroj nezastaví. v takovém případě se data exportují do souboru *. diagsession* . Pak můžete tento soubor otevřít v aplikaci Visual Studio a analyzovat výsledky.

1. Spusťte Poznámkový blok a otevřete Správce úloh a získejte jeho ID procesu (PID). Ve Správci úloh Najděte na kartě **Podrobnosti** PID.

1. Otevřete příkazový řádek a přejděte do adresáře se spustitelným souborem agenta shromažďování, obvykle tady.

   ```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\```

1. Spusťte *VSDiagnostics. exe* zadáním následujícího příkazu.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Argumenty, které musí být zahrnuty:

   * \<*id*> identifikuje relaci shromažďování. ID musí být číslo mezi 1-255.
   * \<*pid*> a PID procesu, který chcete profilovat, v tomto případě PID, který jste našli v kroku 1
   * \<*configFile*>, konfigurační soubor pro agenta shromažďování dat, který chcete spustit. Další informace najdete v tématu [konfigurační soubory pro agenty](#config_file).

1. Změňte velikost poznámkového bloku nebo něco do něj zadejte, abyste se ujistili, že jsou shromažďovány zajímavé informace o profilaci.

1. Zastavte relaci shromažďování a odešlete výstup do souboru zadáním následujícího příkazu.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. V předchozím příkazu přejdete na výstup souboru a otevřete ho v aplikaci Visual Studio a Projděte shromážděné informace.

## <a name="config_file"></a>Konfigurační soubory agenta

Agenti kolekcí jsou vzájemně zaměnitelné komponenty, které shromažďují různé typy dat v závislosti na tom, co se snažíte změřit.

Pro usnadnění práce můžete tyto informace uložit do konfiguračního souboru agenta. Konfigurační soubor je soubor *. JSON* , který obsahuje minimálně název souboru *. dll* a jeho identifikátor CLSID com. Tady jsou ukázkové konfigurační soubory, které najdete v následující složce:

```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

* Konfigurace CpuUsage (základní/vysoká/nízká), které odpovídají datům shromážděným pro nástroj pro profilaci [využití procesoru](../profiling/cpu-usage.md) .
* Konfigurace DotNetObjectAlloc (Base/nízká), které odpovídají datům shromážděným pro [Nástroj přidělování objektů rozhraní .NET](../profiling/dotnet-alloc-tool.md).

Základní a nízké/vysoké konfigurace odkazují na vzorkovací frekvenci. Například nízká je 100 vzorků/s a vysoká je 4000 vzorků za sekundu.

Nástroj *VSDiagnostics. exe* pro práci s agentem shromažďování dat vyžaduje knihovnu DLL i identifikátor CLSID com pro příslušný agent a Agent může mít také další možnosti konfigurace. Pokud používáte agenta bez konfiguračního souboru, použijte formát v následujícím příkazu.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>Oprávnění

Chcete-li profilovat aplikaci, která vyžaduje zvýšená oprávnění, musíte to provést z příkazového řádku se zvýšenými oprávněními.
