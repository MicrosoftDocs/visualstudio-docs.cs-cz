---
title: Spuštění nástrojů pro profilaci s ladicím programem nebo bez něj | Microsoft Docs
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45632967c39348e8dc78dc3e2fb95227dcd86d7d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285890"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Spouštění nástrojů pro profilaci s ladicím programem nebo bez něj

Visual Studio nabízí možnost měření výkonu a nástrojů pro profilaci. Některé nástroje, jako je využití CPU a využití paměti, můžou běžet s ladicím programem nebo bez něj, a to na vydaných nebo ladicích konfiguracích sestavení. Nástroje pro profilaci výkonu, jako je Časová osa aplikace, mohou běžet v sestavení ladění nebo vydání. Nástroje integrované v ladicím programu, jako je okno Diagnostické nástroje a karta události, spouštějte pouze během ladicích cvičení.

>[!NOTE]
>Nástroje pro sledování výkonu bez ladicího programu můžete používat se systémem Windows 7 nebo novějším. Pro spuštění nástrojů pro profilaci integrovaných s ladicím programem je vyžadován systém Windows 8 nebo novější.

Profiler výkonu bez ladicího programu a Diagnostické nástroje integrované s ladicím programem poskytují různé informace a prostředí. Nástroje integrované v ladicím programu zobrazují zarážky a hodnoty proměnných. Nástroje bez ladicího programu poskytují výsledky směrem k prostředí koncových uživatelů.

Chcete-li se rozhodnout, které nástroje a výsledky použít, vezměte v úvahu tyto informace:

- Problémy s externím výkonem, jako jsou vstupně-výstupní operace se soubory nebo problémy s odezvou sítě, se v ladicím programu nebo v neladicích nástrojích neliší.
- Pro problémy způsobené voláními náročnými na procesor mohou nastat výrazné rozdíly ve výkonu mezi sestaveními vydaných verzí a ladění. Zkontrolujte, zda problém existuje v sestavení vydaných verzí.
- Pokud k problému dochází pouze během sestavení ladění, pravděpodobně nemusíte spouštět nástroje bez ladicího programu. V případě problémů s vydáním sestavení se rozhodněte, zda ladicí program bude pomáhat s dalším šetřením.
- Sestavení vydaných verzí poskytují optimalizace, jako jsou volání funkcí a konstanty, vyřazení nepoužitých cest kódu a ukládání proměnných způsobem, který nelze použít v ladicím programu. Čísla výkonu v nástrojích integrovaných s ladicím programem jsou méně přesná, protože sestavení ladění nemají tyto optimalizace.
- Ladicí program změní dobu výkonu, protože vyžaduje operace ladicího programu, jako je zachycení výjimek a událostí načtení modulu.
- Čísla výkonu sestavení verze v nástrojích profileru výkonu jsou nejpřesnější a přesná. Výsledky nástroje integrované v ladicím programu jsou nejužitečnější pro porovnání s dalšími měřeními souvisejícími s laděním.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a>Shromažďování dat profilace během ladění

Když spustíte ladění v aplikaci Visual Studio tak, že vyberete **ladění**  >  **Spustit ladění**nebo stisknete klávesu **F5**, ve výchozím nastavení se zobrazí okno **diagnostické nástroje** . Pokud ho chcete otevřít ručně, vyberte **ladit**  >  **Windows**  >  **Zobrazit diagnostické nástroje**. V okně **diagnostické nástroje** se zobrazují informace o událostech, paměti procesu a využití procesoru.

![Snímek obrazovky okna Diagnostické nástroje](../profiling/media/diagnostictoolswindow.png " Okno Diagnostické nástroje")

- Pomocí ikony **Nastavení** na panelu nástrojů vyberte, jestli se má zobrazit **využití paměti**, **Analýza uživatelského rozhraní**a **využití procesoru**.

- V rozevíracím seznamu **Nastavení** vyberte **Nastavení** a otevřete **stránku vlastností diagnostické nástroje** s dalšími možnostmi.

- Pokud používáte Visual Studio Enterprise, můžete povolit nebo zakázat IntelliTrace tak, že kliknete na **nástroje**  >  **Možnosti**  >  **IntelliTrace**.

Diagnostická relace skončí po zastavení ladění.

### <a name="the-events-tab"></a>Karta události

Během relace ladění vypíše karta události v okně Diagnostické nástroje diagnostické události, ke kterým dojde. Kategorie *zarážky*, *soubory*a další v této kategorii vám umožní rychle vyhledat seznam pro kategorii nebo přeskočit kategorie, o kterých nezáleží.

Pomocí rozevíracího seznamu **Filtr** můžete filtrovat události v zobrazení a mimo ně výběrem nebo zrušením určitých kategorií událostí.

![Snímek obrazovky s filtrem diagnostických událostí](../profiling/media/diagnosticeventfilter.png "Filtr diagnostické události")

Pomocí vyhledávacího pole vyhledejte konkrétní řetězec v seznamu událostí. Tady jsou výsledky hledání *názvu* řetězce, který se shoduje se čtyřmi událostmi:

![Snímek obrazovky s vyhledáváním diagnostických událostí](../profiling/media/diagnosticseventsearch.png "Hledání diagnostické události")

Další informace najdete v tématu [hledání a filtrování událostí diagnostické nástroje okna na kartě události](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Shromažďování dat profilace bez ladění

Chcete-li shromažďovat data o výkonu bez ladění, můžete spustit nástroje profileru výkonu.

1. Otevřete projekt v sadě Visual Studio, nastavte konfiguraci řešení na **release**a jako cíl nasazení vyberte **místní ladicí program systému Windows**   (nebo **místní počítač**).

1. Vyberte **ladit**  >  **Performance Profiler**nebo stiskněte **ALT** + **F2**.

1. Na stránce spuštění diagnostických nástrojů vyberte jeden nebo více nástrojů, které chcete spustit. Zobrazují se jenom nástroje, které platí pro typ projektu, operační systém a programovací jazyk. Vyberte **Zobrazit všechny nástroje** a zobrazí se také nástroje, které jsou pro tuto diagnostickou relaci zakázané.

   ![Snímek obrazovky diagnostických nástrojů](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. Chcete-li spustit relaci diagnostiky, vyberte možnost **Spustit**.

   Když je relace spuštěná, některé nástroje zobrazují grafy dat v reálném čase na stránce diagnostické nástroje a také ovládací prvky pro pozastavení a obnovení sběru dat.

    ![Snímek obrazovky se shromažďováním dat v centru výkonu a diagnostiky](../profiling/media/diaghubcollectdata.png "Shromáždění dat z centra")

1. Chcete-li ukončit relaci diagnostiky, vyberte **Zastavit shromažďování**.

   Analyzovaná data se zobrazí na stránce **sestavy** .

Sestavy můžete uložit a otevřít je ze seznamu **naposledy otevřených relací** na stránce spuštění diagnostické nástroje.

![Snímek obrazovky se seznamem Diagnostické nástroje naposledy otevřené relace](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

## <a name="collect-profiling-data-from-the-command-line"></a>Shromažďování dat profilace z příkazového řádku

Chcete-li změřit údaje o výkonu z příkazového řádku, můžete použít VSDiagnostics.exe, který je součástí sady Visual Studio nebo nástrojů Remote Tools. To je užitečné pro zachytávání trasování výkonu v systémech, kde není nainstalovaná sada Visual Studio, nebo pro skriptování kolekce trasování výkonu. Když použijete VSDiagnostics.exe, spustíte relaci diagnostiky, která zachycuje a ukládá data profilování, dokud se nástroj nezastaví. V tomto okamžiku jsou tato data exportována do souboru. diagsession a tento soubor můžete otevřít v aplikaci Visual Studio a analyzovat výsledky.

### <a name="launch-an-application"></a>Spuštění aplikace

1. Otevřete příkazový řádek a přejděte do adresáře s VSDiagnostics.exe:

   ```
   <Visual Studio Install Folder>\Team Tools\DiagnosticsHub\Collector\
   ```

2. Spusťte VSDiagnostics.exe s následujícím příkazem:

   ```
   VSDiagnostics.exe start <id> /launch:<appToLaunch> /loadConfig:<configFile>
   ```

   Je nutné zahrnout následující argumenty:

   - \<id\>: Identifikuje relaci shromažďování. ID musí být číslo mezi 1-255.
   - \<appToLaunch\>: Spustitelný soubor, který se má spustit a profilovat.
   - \<configFile\>: Konfigurační soubor pro agenta shromažďování, který chcete spustit.

3. Chcete-li zastavit shromažďování a zobrazit výsledky, postupujte podle kroků v části "zastavení shromažďování" dále v tomto článku.

### <a name="attach-to-an-existing-application"></a>Připojit k existující aplikaci

1. Otevřete aplikaci, například Poznámkový blok, a pak otevřete **Správce úloh** a Získejte ID procesu (PID). Ve Správci úloh Najděte na kartě **Podrobnosti**PID   .
2. Otevřete příkazový řádek a přejděte do adresáře se spustitelným souborem agenta kolekce. Obvykle je to tady:

   ```
   <Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\
   ```

3. Spusťte soubor VSDiagnostics.exe zadáním následujícího příkazu.

   ```
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Je nutné zahrnout následující argumenty:

   - \<id\>: Identifikuje relaci shromažďování. ID musí být číslo mezi 1-255.
   - \<pid\>: PID procesu, který chcete profilovat, v tomto případě je to PID, který jste našli v kroku 1.
   - \<configFile\>: Konfigurační soubor pro agenta shromažďování, který chcete spustit. Další informace najdete v tématu [konfigurační soubory pro agenty](../profiling/profile-apps-from-command-line.md).

4. Chcete-li zastavit shromažďování a zobrazit výsledky, postupujte podle kroků v následující části.

### <a name="stop-collection"></a>Zastavit shromažďování

1. Zastavte relaci shromažďování a odešlete výstup do souboru zadáním následujícího příkazu.

   ```
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

2. V předchozím příkazu přejdete na výstup souboru a otevřete ho v aplikaci Visual Studio a Projděte shromážděné informace.

## <a name="agent-configuration-files"></a>Konfigurační soubory agenta

Agenti kolekcí jsou vzájemně zaměnitelné komponenty, které shromažďují různé typy dat v závislosti na tom, co se snažíte změřit.
Pro usnadnění práce můžete tyto informace uložit do konfiguračního souboru agenta. Konfigurační soubor je soubor. JSON, který obsahuje minimálně název souboru. dll a jeho identifikátor CLSID COM. Tady jsou ukázkové konfigurační soubory, které najdete v následující složce:

```
<Visual Studio installation folder>\Team Tools\DiagnosticsHub\Collector\AgentConfigs\
```

Chcete-li stáhnout a zobrazit konfigurační soubory agenta, přečtěte si následující odkazy:

- https://aka.ms/vs/diaghub/agentconfig/cpubase
- https://aka.ms/vs/diaghub/agentconfig/cpuhigh
- https://aka.ms/vs/diaghub/agentconfig/cpulow
- https://aka.ms/vs/diaghub/agentconfig/database
- https://aka.ms/vs/diaghub/agentconfig/dotnetasyncbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetallocbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetalloclow

Konfigurace CpuUsage (základní/vysoká/nízká) odpovídají datům shromážděným pro nástroj profilace [využití procesoru](../profiling/cpu-usage.md) .
Konfigurace DotNetObjectAlloc (základní/nízká) odpovídají datům shromážděným pro [Nástroj přidělování objektů .NET](../profiling/dotnet-alloc-tool.md).

Základní a nízké/vysoké konfigurace odkazují na vzorkovací frekvenci. Například nízká je 100 vzorků/s a vysoká je 4000 vzorků za sekundu.
Aby nástroj VSDiagnostics.exe mohl pracovat s agentem shromažďování dat, vyžaduje knihovnu DLL i identifikátor CLSID COM pro příslušný agent. Agent může mít také další možnosti konfigurace. Pokud používáte agenta bez konfiguračního souboru, použijte formát v následujícím příkazu:

```
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```
