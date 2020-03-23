---
title: 'Příkazový řádek Profiler: Součást klienta .NET instrument, získání paměťových dat'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 76d216c4f112f88001b0314a23f22e689f729106
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775898"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line"></a>Postupy: Instrumentace samostatné součásti rozhraní .NET Framework a shromažďování dat paměti pomocí příkazového řádku profileru
Tento článek popisuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jak pomocí nástrojů příkazového řádku nástroje nástroje nástroje .NET Framework součást samostatné aplikace, jako je například soubor .exe nebo DLL a shromažďovat informace o paměti pomocí profileru.

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

 Chcete-li shromažďovat paměťová data z komponenty rozhraní .NET Framework pomocí metody instrumentace, použijte nástroj [VSInstr.exe](../profiling/vsinstr.md) ke generování instrumentované verze komponenty a nástroje [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) k inicializaci proměnných prostředí profilování. Potom spustíte profiler pomocí nástroje *VSPerfCmd.exe.*

 Při spuštění instrumentované součásti jsou data paměti automaticky shromažďována do datového souboru. Shromažďování dat můžete pozastavit a obnovit během relace profilování.

 Chcete-li ukončit relaci profilování, ukončete cílovou aplikaci a explicitně vypněte profiler. Ve většině případů doporučujeme vymazat proměnné prostředí profilování na konci relace.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Připojení profileru ke spuštěné aplikaci rozhraní .NET Framework

1. Otevřete okno příkazového řádku.

2. Nástroj **VSInstr** slouží ke generování instrumentované verze cílové aplikace.

3. Inicializace proměnných prostředí profilování rozhraní .NET Framework. Zadejte:

    **VSPerfClrEnv** {**/tracegc** &#124; **/tracegclife**}

   - Možnosti **/tracegc** a **/tracegclife** inicializují proměnné prostředí tak, aby shromažďovaly pouze data přidělení paměti nebo shromažďovaly data přidělení paměti a životnosti objektu.

       |Možnost|Popis|
       |------------|-----------------|
       |**/tracegc**|Povolí pouze shromažďování dat přidělení paměti.|
       |**/tracegclife**|Umožňuje shromažďování dat přidělení paměti i životnosti objektu.|

4. Spusťte profiler. Zadejte:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - Možnost [/start](../profiling/start.md)**:trace** inicializuje profiler.

   - [Možnost /output](../profiling/output.md)**:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění profilovacích dat (.* vsp*).

     Můžete použít některou z následujících možností s **parametrem /start:trace.**

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní profilovaný proces. Tato možnost je vyžadována pouze v případě, že proces je spuštěn jako uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci Uživatelské jméno na kartě **Procesy** ve Správci úloh systému Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace spuštěna v jiné relaci. Idenitifer relace je uveden ve **sloupci ID relace** na kartě **Procesy** ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Chcete-li spustit profiler s pozastavenou kolekcí dat, přidejte možnost **/globaloff** do příkazového řádku **/start.** Použití **/globalon** obnovit profilování. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/counter](../profiling/counter.md) **:**`Config` | Shromažďuje informace z čítače výkonu procesoru, který je zadán v konfiguraci. Informace o čítači jsou přidány k datům shromážděným při každé události profilování. |
   | [události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.* etl*) souboru. |

5. Spusťte cílovou aplikaci z okna příkazového řádku.

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Zatímco je spuštěna cílová aplikace, můžete řídit shromažďování dat spuštěním a zastavením zápisu dat do souboru pomocí možností *VSPerfCmd.exe.* Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností **VSPerfCmd** spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon](../profiling/globalon-and-globaloff.md) [/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat pro`PID`proces, který je určen ID procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Spustí (**/threadon**) nebo zastaví (**/threadoff**) shromažďování dat pro`TID`vlákno, které je určeno ID vlákna ( ).|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, zavřete aplikaci, která je spuštěna součást s přístrojovou součástí a potom zavolejte možnost **VSPerfCmd** [/shutdown](../profiling/shutdown.md) vypnout profiler a zavřete datový soubor profilování. Příkaz **VSPerfClrEnv /off** vymaže proměnné prostředí profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Zavřete cílovou aplikaci.

2. Vypněte profileru. Zadejte:

     **VSPerfCmd /vypnutí**

3. (Nepovinné) Vymažte proměnné prostředí profilování. Zadejte:

     **VSPerfCmd /vypnuto**

## <a name="see-also"></a>Viz také
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
