---
title: VSPerfCmd – připojení profileru k nativní službě za účelem získání statistiky aplikace
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: f45d08a82bdc3f6807f9a4d5a0cb31dc157e4c9c
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328659"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line"></a>Postupy: Připojení profileru k nativní službě ke shromažďování statistik aplikace pomocí příkazového řádku
Tento článek popisuje, jak pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástrojů příkazového řádku nástroje pro profilaci připojit profiler k nativní službě a shromažďovat statistiku výkonu pomocí metody vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

 I když je profiler připojen ke službě, můžete pozastavit a obnovit shromažďování dat.

 Chcete-li ukončit relaci profilování, musí být profiler odpojen od služby a poté explicitně ukončen.

## <a name="start-the-application-with-the-profiler"></a>Spuštění aplikace pomocí profileru
 K připojení profileru k nativní službě použijte možnosti **VSPerfCmd.exe** [/Start](../profiling/start.md) a [/Attach](../profiling/attach.md) pro inicializaci profileru a jeho připojení k cílové aplikaci. V jednom příkazovém řádku můžete zadat **/Start** a **/Attach** a jejich příslušné možnosti. Můžete také přidat možnost [/globaloff](../profiling/globalon-and-globaloff.md) pro pozastavení sběru dat na začátku cílové aplikace. Pak můžete pomocí [/GlobalOn](../profiling/globalon-and-globaloff.md) začít shromažďovat data.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Připojení profileru k nativní službě

1. V případě potřeby službu spusťte.

2. Otevřete okno příkazového řádku.

3. Spusťte profiler. Zadejte:

    **VSPerfCmd/Start: Sample**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - Možnost **/Start: Sample** inicializuje Profiler.

   - Parametr **/output:** `OutputFile` je vyžadován s parametrem **/Start**. `OutputFile`Určuje název a umístění dat profilování (.* VSP*) soubor.

     Pomocí možnosti **/Start: Sample** můžete použít kteroukoli z následujících možností.

   > [!NOTE]
   > Pro služby jsou obvykle vyžadovány možnosti **/User** a **/CrossSession** .

   | Možnost | Popis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní profilový proces. Tato možnost je vyžadována, pouze pokud je proces spuštěn jako jiný uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci uživatelské jméno na kartě procesy ve Správci úloh systému Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud aplikace běží v jiné relaci. ID relace je uvedeno ve sloupci ID relace na kartě procesy ve Správci úloh systému Windows. **/Cs** lze zadat jako zkratku pro **/CrossSession**. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilace. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/WinCounter** . Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro Windows (ETW), která se má shromáždit během profilace. Události ETW jsou shromažďovány v samostatném souboru (. ETL). |

4. Připojte profiler ke službě. Zadejte:

    **VSPerfCmd/attach:** `PID` [`Sample Event`]

    `PID`Určuje ID procesu cílové aplikace. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

    Ve výchozím nastavení jsou data o výkonu Navzorkovaná každých 10 000 000 hodinových cyklů procesoru. To je přibližně jednou za 10 sekund na frekvencí 1 GHz procesoru. Můžete určit jednu z následujících možností pro změnu intervalu hodinových cyklů nebo zadat jinou událost vzorkování.

   |Událost vzorku|Popis|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Změní interval vzorkování na počet nepřerušených hodinových cyklů určených parametrem `Interval`.|
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Změní událost vzorkování na chyby stránkování. Pokud `Interval` je zadaný, nastaví počet chyb stránek mezi ukázkami. Výchozí hodnota je 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:** `Interval` ]|Změní událost vzorkování na systémová volání z procesu do jádra operačního systému (voláním). Pokud `Interval` je zadáno, nastaví počet volání mezi vzorky. Výchozí hodnota je 10.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Změní událost a interval vzorkování na čítač výkonu a interval procesoru určený parametrem `Config`.|

## <a name="control-data-collection"></a>Řízení shromažďování dat
 I když je cílová aplikace spuštěná, můžete použít možnosti *VSPerfCmd.exe* pro spuštění a zastavení zápisu dat do datového souboru profileru. Řízení sběru dat umožňuje shromažďovat data pro určitou část provádění programu, například spouštění nebo ukončování aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující páry možností **VSPerfCmd** spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Shromažďování dat můžete zapnout a vypnout několikrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/GlobalOn**) nebo zastaví shromažďování dat (**/globaloff**) pro všechny procesy.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/ProcessOn**) nebo zastaví shromažďování dat (**/ProcessOff**) pro proces určený identifikátorem procesu ( `PID` ).|
    |**/Attach:** { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[: { `PID`&#124;`ProcName` }]|**/Attach** začne shromažďovat data pro proces určený ID procesu nebo názvem procesu. **/detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán proces.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, musí být profiler odpojen od služby a pak explicitně vypnut. Nativní službu, která je profilovaná pomocí metody vzorkování, můžete odpojit zastavením služby nebo zavoláním možnosti **VSPerfCmd/detach** . Potom zavoláte možnost **VSPerfCmd** [/shutdown](../profiling/shutdown.md) pro vypnutí profileru a zavření souboru dat profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Chcete-li odpojit Profiler od cílové aplikace, proveďte jeden z následujících kroků:

    - Zastavte službu.

         -nebo-

    - Typ **VSPerfCmd/detach**

2. Vypněte profiler. Zadejte:

     **VSPerfCmd/shutdown**

## <a name="see-also"></a>Viz také
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
