---
title: 'VSPerfCmd: Připojte profiler k nativní službě, abyste získali statistiky aplikací'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 00f0d3cedf2ef1875d93f7706f7cfa48a8b6b274
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779087"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line"></a>Postupy: Připojení profileru k nativní službě ke shromažďování statistik aplikace pomocí příkazového řádku
Tento článek popisuje, jak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pomocí nástrojů příkazového řádku profilování připojit profiler k nativní službě a shromažďovat statistiky výkonu pomocí metody vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

 Zatímco profiler je připojen ke službě, můžete pozastavit a obnovit shromažďování dat.

 Chcete-li ukončit relaci profilování, musí být profiler odpojen od služby a poté explicitně ukončen.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru
 Chcete-li připojit profiler k nativní službě, použijte **VSPerfCmd.exe**[/start](../profiling/start.md) a [/attach](../profiling/attach.md) možnosti inicializovat profiler a připojit jej k cílové aplikaci. Můžete zadat **/start** a **/attach** a jejich příslušné možnosti na jednom příkazovém řádku. Můžete také přidat [/globaloff](../profiling/globalon-and-globaloff.md) možnost pozastavit shromažďování dat na začátku cílové aplikace. Potom můžete použít [/globalon](../profiling/globalon-and-globaloff.md) začít shromažďovat data.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Připojení profileru k nativní službě

1. V případě potřeby spusťte službu.

2. Otevřete okno příkazového řádku.

3. Spusťte profiler. Zadejte:

    **VSPerfCmd /start:sample**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - Možnost **/start:sample** inicializuje profiler.

   - Možnost **/output:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění profilovacích dat (.* vsp*).

     Můžete použít některou z následujících možností s **parametrem /start:sample.**

   > [!NOTE]
   > Možnosti **/user** a **/crosssession** jsou obvykle vyžadovány pro služby.

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní profilovaný proces. Tato možnost je vyžadována pouze v případě, že proces je spuštěn jako uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci Uživatelské jméno na kartě Procesy ve Správci úloh systému Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace spuštěna v jiné relaci. ID relace je uvedeno ve sloupci ID relace na kartě Procesy ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.etl) souboru. |

4. Připojte profiler ke službě. Zadejte:

    **VSPerfCmd /připojit:** `PID` [`Sample Event`]

    `PID`určuje ID procesu cílové aplikace. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

    Ve výchozím nastavení jsou data o výkonu vzorkována každých 10 000 000 nezastavených cyklů hodin procesoru. To je přibližně jednou za 10 sekund na procesoru 1GH. Můžete zadat jednu z následujících možností pro změnu intervalu cyklu hodin nebo pro určení jiné události vzorkování.

   |Událost vzorku|Popis|
   |------------------|-----------------|
   |[/časovač](../profiling/timer.md) **:**`Interval`|Změní interval vzorkování na počet nepřerušených hodinových cyklů určených parametrem `Interval`.|
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Změní událost vzorkování na chyby stránky. Pokud `Interval` je zadán, nastaví počet chyb stránky mezi ukázkami. Výchozí hodnota je 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Změní událost vzorkování na systémová volání z procesu do jádra operačního systému (syscalls). Pokud `Interval` je zadán, nastaví počet volání mezi vzorky. Výchozí hodnota je 10.|
   |[/counter](../profiling/counter.md) **:**`Config`|Změní událost a interval vzorkování na čítač výkonu a interval procesoru určený parametrem `Config`.|

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Zatímco je spuštěna cílová aplikace, můžete použít možnosti *VSPerfCmd.exe* ke spuštění a zastavení zápisu dat do datového souboru profileru. Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností **VSPerfCmd** spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) shromažďování dat`PID`pro proces určený ID procesu ( ).|
    |**/attach:** `PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach** začne shromažďovat data pro proces určený ID procesu nebo název procesu. **/detach** zastaví shromažďování dat pro zadaný proces nebo pro všechny procesy, pokud proces není zadán.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, musí být profiler odpojen od služby a poté explicitně ukončen. Nativní službu, která je profilována metodou vzorkování, můžete odpojit zastavením služby nebo voláním možnosti **VSPerfCmd /detach.** Potom volání **VSPerfCmd** [/shutdown](../profiling/shutdown.md) možnost vypnout profiler a zavřete profilování datový soubor.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Jedním z následujících akcí odpojte profiler od cílové aplikace:

    - Zastavte službu.

         -nebo-

    - Typ **VSPerfCmd /detach**

2. Vypněte profileru. Zadejte:

     **VSPerfCmd /vypnutí**

## <a name="see-also"></a>Viz také
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
