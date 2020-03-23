---
title: 'Příkazový řádek profileru: Nativní komponenta nástroje, získání časovacích dat'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36883074-9be8-4e90-a66f-7e87f21fcd30
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: fc7bb0a5e853edee4ff28cded94a5d576a13b596
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775441"
---
# <a name="how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Postup: Instrumentujte nativní samostatnou komponentu a shromažďujte data časování pomocí profileru z příkazového řádku
Toto téma popisuje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] použití nástrojů příkazového řádku Nástroje profilování k instrumentaci nativní součásti, například c++ . *exe* nebo . *dll* a shromažďovat podrobná časová data.

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

Chcete-li shromažďovat podrobná časovací data z komponenty pomocí metody instrumentace, použijte nástroj [VSInstr.exe](../profiling/vsinstr.md) ke generování instrumentované verze komponenty. Potom spustíte profiler. Při spuštění instrumentované součásti jsou data časování automaticky shromažďována do datového souboru. Shromažďování dat můžete pozastavit a obnovit během relace profilování.

 Chcete-li ukončit relaci profilování, zavřete cílovou aplikaci a potom explicitně vypněte profiler.

## <a name="start-the-profiling-session"></a>Spuštění relace profilování

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>Chcete-li zahájit profilování pomocí metody instrumentace

1. Otevřete okno příkazového řádku.

2. Nástroj **VSInstr** slouží ke generování instrumentované verze cílové aplikace.

3. Spusťte profiler. Zadejte:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - Možnost [/start](../profiling/start.md)**:trace** inicializuje profiler.

   - [Možnost /output](../profiling/output.md)**:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     S možností **/start:trace** můžete použít jednu nebo více z následujících možností.

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní profilovaný proces. Tato možnost je vyžadována pouze v případě, že proces je spuštěn jako uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci **Uživatelské jméno** na kartě **Procesy** ve Správci úloh systému Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace spuštěna v jiné relaci. Idenitifikátor relace je uveden ve sloupci **ID relace** na kartě Procesy ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Spustí profiler s pozastavenou kolekcí dat. Použití [/globalon](../profiling/globalon-and-globaloff.md) obnovit profilování. |
   | [/counter](../profiling/counter.md) **:**`Config` | Shromažďuje informace z čítače výkonu `Config`procesoru, který je určen v . Informace o čítači jsou přidány k datům shromážděným při každé události profilování. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.* etl*) souboru. |

4. Spusťte cílovou aplikaci typickým způsobem.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je spuštěna cílová aplikace, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe.* Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat pro`PID`proces, který je určen ID procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) shromažďování dat pro`TID`vlákno, které je určeno ID vlákna ( ).|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, zavřete aplikaci, která je spuštěna součást s přístrojovou součástí a potom zavolejte možnost **VSPerfCmd** [/shutdown](../profiling/shutdown.md) vypnout profiler a zavřete datový soubor profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Zavřete cílovou aplikaci.

2. Vypněte profileru. Zadejte:

     **VSPerfCmd /vypnutí**

## <a name="see-also"></a>Viz také
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)
