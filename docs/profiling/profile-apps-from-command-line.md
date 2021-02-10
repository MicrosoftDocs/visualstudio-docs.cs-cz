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
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 0b1d5906213b148605e35c483b377280dc942515
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936545"
---
# <a name="measure-application-performance-from-the-command-line"></a>Měření výkonu aplikace z příkazového řádku

Pomocí nástrojů příkazového řádku můžete shromažďovat informace o výkonu aplikace.

V příkladu popsaném v tomto článku shromažďujete informace o výkonu pro Microsoft Notepad, ale stejnou metodu lze použít k profilování jakéhokoli procesu.

## <a name="prerequisites"></a>Požadavky

* Visual Studio 2019 nebo novější verze

* Znalost nástrojů příkazového řádku

* Chcete-li shromáždit informace o výkonu na vzdáleném počítači bez nainstalované sady Visual Studio, nainstalujte [Remote Tools for Visual Studio](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019) na vzdáleném počítači. Verze nástrojů musí odpovídat vaší verzi sady Visual Studio.

## <a name="collect-performance-data"></a>Shromažďování údajů o výkonu

Profilace pomocí nástrojů rozhraní příkazového řádku Visual Studio Diagnostics funguje tak, že k procesu připojí nástroj pro profilaci společně s jedním z agentů kolektoru. Když připojíte nástroj profilace, zahájíte relaci diagnostiky, která zachycuje a ukládá data profilování, dokud se nástroj nezastaví. v takovém případě se data exportují do souboru *. diagsession* . Pak můžete tento soubor otevřít v aplikaci Visual Studio a analyzovat výsledky.

1. Spusťte Poznámkový blok a otevřete Správce úloh a získejte jeho ID procesu (PID). Ve Správci úloh Najděte na kartě **Podrobnosti** PID.

1. Otevřete příkazový řádek a přejděte do adresáře se spustitelným souborem agenta shromažďování, obvykle zde (pro Visual Studio Enterprise).

   ```<Visual Studio installation folder>\2019\Enterprise\Team Tools\DiagnosticsHub\Collector\```

1. Spusťte *VSDiagnostics.exe* zadáním následujícího příkazu.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Argumenty, které musí být zahrnuty:

   * \<*id*> Identifikuje relaci shromažďování. ID musí být číslo mezi 1-255.
   * \<*pid*>, PID procesu, který chcete profilovat, v tomto případě PID, který jste našli v kroku 1.
   * \<*configFile*>, konfigurační soubor pro agenta shromažďování, který chcete spustit. Další informace najdete v tématu [konfigurační soubory pro agenty](#config_file).

   Například můžete použít následující příkaz pro agenta CPUUsageBase nahrazením *identifikátoru PID* , jak je popsáno výše.

   ```cmd
   VSDiagnostics.exe start 1 /attach:<pid> /loadConfig:AgentConfigs\CPUUsageLow.json
   ```

1. Změňte velikost poznámkového bloku nebo něco do něj zadejte, abyste se ujistili, že jsou shromažďovány zajímavé informace o profilaci.

1. Zastavte relaci shromažďování a odešlete výstup do souboru zadáním následujícího příkazu.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Vyhledejte výstup souboru *. diagsession* z předchozího příkazu a otevřete ho v aplikaci Visual Studio (**soubor**  >  **otevřen**) a Projděte si shromažďované informace.

   Chcete-li analyzovat výsledky, přečtěte si dokumentaci k příslušnému nástroji pro sledování výkonu. Může to být například [využití CPU](../profiling/cpu-usage.md), [Nástroj pro přidělování objektů .NET](../profiling/dotnet-alloc-tool.md)nebo [databázový](../profiling/analyze-database.md) nástroj.

## <a name="agent-configuration-files"></a><a name="config_file"></a> Konfigurační soubory agenta

Agenti kolekcí jsou vzájemně zaměnitelné komponenty, které shromažďují různé typy dat v závislosti na tom, co se snažíte změřit.

Pro usnadnění práce můžete tyto informace uložit do konfiguračního souboru agenta. Konfigurační soubor je soubor *. JSON* , který obsahuje minimálně název souboru *. dll* a jeho identifikátor CLSID com. Tady jsou ukázkové konfigurační soubory, které najdete v následující složce:

```<Visual Studio installation folder>Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

Chcete-li stáhnout a zobrazit konfigurační soubory agenta, přečtěte si následující odkazy:

- https://aka.ms/vs/diaghub/agentconfig/cpubase
- https://aka.ms/vs/diaghub/agentconfig/cpuhigh
- https://aka.ms/vs/diaghub/agentconfig/cpulow
- https://aka.ms/vs/diaghub/agentconfig/database
- https://aka.ms/vs/diaghub/agentconfig/dotnetasyncbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetallocbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetalloclow
- https://aka.ms/vs/diaghub/agentconfig/dotnetcountersbase

Konfigurace CpuUsage (základní/vysoká/nízká) odpovídají datům shromážděným pro nástroj profilace [využití procesoru](../profiling/cpu-usage.md) .
Konfigurace DotNetObjectAlloc (základní/nízká) odpovídají datům shromážděným pro [Nástroj přidělování objektů .NET](../profiling/dotnet-alloc-tool.md).

Základní a nízké/vysoké konfigurace odkazují na vzorkovací frekvenci. Například nízká je 100 vzorků/s a vysoká je 4000 vzorků za sekundu.

Aby nástroj *VSDiagnostics.exe* pracoval s agentem shromažďování dat, vyžaduje knihovnu DLL i identifikátor CLSID com pro příslušný agent a Agent může mít také další možnosti konfigurace. Pokud používáte agenta bez konfiguračního souboru, použijte formát v následujícím příkazu.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>Oprávnění

Chcete-li profilovat aplikaci, která vyžaduje zvýšená oprávnění, musíte to provést z příkazového řádku se zvýšenými oprávněními.
