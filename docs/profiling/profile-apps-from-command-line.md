---
title: Měření výkonu z příkazového řádku
description: Změřte výkon procesoru a využití spravované paměti v aplikaci z příkazového řádku.
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
ms.openlocfilehash: 18850a6e365988abd33b7e2e2a3972ba5cb0a91a
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638695"
---
# <a name="measure-application-performance-from-the-command-line"></a>Měření výkonu aplikace z příkazového řádku

Informace o výkonu aplikace můžete shromažďovat pomocí nástrojů příkazového řádku.

V příkladu popsaném v tomto článku shromažďujete informace o výkonu programu Microsoft Notepad, ale stejnou metodu lze použít k profilování libovolného procesu.

## <a name="prerequisites"></a>Požadavky

* Visual Studio 2019 nebo novější verze

* Znalost nástrojů příkazového řádku

* Chcete-li shromažďovat informace o výkonu vzdáleného počítače bez nainstalovaného sady Visual Studio, nainstalujte do vzdáleného počítače [nástroje performance pro sady Visual Studio.](https://visualstudio.microsoft.com/downloads#performance-tools-for-visual-studio-2019) Verze nástrojů musí odpovídat verzi sady Visual Studio.

## <a name="collect-performance-data"></a>Shromažďování údajů o výkonu

Profilování pomocí nástrojů nastavení cli nástroje Visual Studio Diagnostika funguje tak, že připojí nástroj profilování spolu s jedním z agentů kolektoru, k procesu. Když připojíte nástroj profilování, zahájíte diagnostickou relaci, která zachycuje a ukládá data profilování, dokud není nástroj zastaven, a v tomto okamžiku jsou data exportována do souboru *diagsession.* Potom můžete otevřít tento soubor v sadě Visual Studio a analyzovat výsledky.

1. Spusťte poznámkový blok a pak otevřete Správce úloh, abyste získali jeho ID procesu (PID). Ve Správci úloh najdete pid na kartě **Podrobnosti.**

1. Otevřete příkazový řádek a změňte adresář pomocí spustitelného souboru inkasního agenta, obvykle zde.

   ```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\```

1. Spusťte *nástroj VSDiagnostics.exe* zadáním následujícího příkazu.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Argumenty, které musí být zahrnuty, jsou:

   * \<*id*> Identifikuje relaci kolekce. ID musí být číslo mezi 1-255.
   * \<*pid*>, PID procesu, který chcete profilovat, v tomto případě PID, který jste našli v kroku 1
   * \<*configFile*> konfigurační soubor pro inkasního agenta, který chcete spustit. Další informace naleznete v [tématu Configuration files for agents](#config_file).

1. Změňte velikost poznámkového bloku nebo do něj něco zadejte, abyste se ujistili, že jsou shromažďovány některé zajímavé informace o profilování.

1. Zastavte relaci kolekce a odešlete výstup do souboru zadáním následujícího příkazu.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Přejděte na výstup souboru z předchozího příkazu a otevřete jej v sadě Visual Studio a zkontrolujte shromážděné informace.

## <a name="agent-configuration-files"></a><a name="config_file"></a>Konfigurační soubory agenta

Agenti kolekce jsou zaměnitelné součásti, které shromažďují různé typy dat v závislosti na tom, co se pokoušíte měřit.

Pro větší pohodlí můžete tyto informace uložit do konfiguračního souboru agenta. Konfigurační soubor je *soubor JSON,* který obsahuje minimálně název *dll* a jeho CLSID COM. Zde jsou ukázkové konfigurační soubory, které najdete v následující složce:

```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

* Konfigurace využití procesoru (Base/High/Low), což odpovídá datům shromážděným pro nástroj profilování [využití procesoru.](../profiling/cpu-usage.md)
* Konfigurace DotNetObjectAlloc (Base/Low), které odpovídají datům shromážděným pro [nástroj pro alokaci objektů .NET](../profiling/dotnet-alloc-tool.md).

Konfigurace Base/Low/High se vztahují k vzorkovací frekvenci. Například Nízká je 100 vzorků za sekundu a Vysoká je 4000 vzorků za sekundu.

Pro nástroj *VSDiagnostics.exe* pro práci s agentem kolekce vyžaduje pro příslušného agenta soubor DLL i CLSID COM a agent může mít také další možnosti konfigurace. Pokud používáte agenta bez konfiguračního souboru, použijte formát v následujícím příkazu.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>Oprávnění

Chcete-li profilovat aplikaci, která vyžaduje zvýšená oprávnění, musíte tak učinit z příkazového řádku se zvýšenými oprávněními.
