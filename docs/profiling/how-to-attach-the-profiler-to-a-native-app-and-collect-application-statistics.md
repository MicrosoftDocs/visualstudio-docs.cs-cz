---
title: Připojení profileru k nativní aplikaci a shromažďování statistik aplikací
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df44fe42-281b-4398-b3fc-277b62ae41f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 96d4a812fd98dbd0f58a8012a61cdaef96db3a8b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779100"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Postupy: Připojení profileru k nativní samostatné aplikaci a shromažďování statistik aplikace pomocí příkazového řádku
Tento článek popisuje, jak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pomocí nástrojů příkazového řádku profilování připojit profiler ke spuštěné nativní samostatné (klientské) aplikaci a shromažďovat statistiky výkonu pomocí metody vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

 Když je profiler připojen k aplikaci, můžete pozastavit a obnovit shromažďování dat. Chcete-li ukončit relaci profilování, profiler již nesmí být připojen k aplikaci a profiler musí být explicitně vypnut.

## <a name="attach-the-profiler"></a>Připojte profiler
 Chcete-li připojit profiler k cílové aplikaci pomocí profileru, použijte **VSPerfCmd/start** a **/attach** možnosti inicializovat profiler a připojit k cílové aplikaci. Můžete zadat **/start** a **/attach** a jejich příslušné možnosti na jednom příkazovém řádku. Můžete také přidat **/globaloff** možnost pozastavit shromažďování dat na začátku cílové aplikace. Potom pomocí **/globalon** začít shromažďovat data.

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Připojení profileru ke spuštěné aplikaci rozhraní .NET Framework

1. Otevřete okno příkazového řádku.

2. Spusťte profiler. Zadejte:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - Možnost[/start](../profiling/start.md)**:sample** inicializuje profiler.

   - [Možnost /output](../profiling/output.md)**:** `OutputFile` je vyžadována s **parametrem /start**. `OutputFile`určuje název a umístění souboru profilovacích dat (.vsp).

     Můžete použít některou z následujících možností s **parametrem /start:sample.**

   | Možnost | Popis |
   | - | - |
   | [/uživatel](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Určuje doménu a uživatelské jméno účtu, který vlastní profilovaný proces. Tato možnost je vyžadována pouze v případě, že proces je spuštěn jako uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci Uživatelské jméno na kartě Procesy ve Správci úloh systému Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umožňuje profilování procesů v jiných relacích. Tato možnost je vyžadována, pokud je aplikace ASP.NET spuštěna v jiné relaci. Idenitifikátor relace je uveden ve sloupci ID relace na kartě Procesy ve Správci úloh systému Windows. **/CS** lze zadat jako zkratku pro **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Určuje čítač výkonu systému Windows, který má být shromážděn během profilování. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Používejte pouze s **/wincounter.** Určuje počet milisekund mezi událostmi shromažďování čítačů výkonu systému Windows. Výchozí hodnota je 500 ms. |
   | [/události](../profiling/events-vsperfcmd.md) **:**`Config` | Určuje událost trasování událostí pro systém Windows (ETW), která má být shromážděna během profilování. Události ETW jsou shromažďovány v samostatném (.* etl*) souboru. |

3. Připojte profiler k cílové aplikaci. Zadejte:

    **VSPerfCmd**[/attach](../profiling/attach.md) `PID` **:**{`Sample Event`&#124;`ProcName`} [ ]  

    `PID`určuje ID procesu cílové aplikace. `ProcessName`určuje název procesu. Všimněte si, `ProcessName` že pokud zadáte a více procesů, které mají stejný název jsou spuštěny, výsledky jsou nepředvídatelné. ID procesů všech spuštěných procesů můžete zobrazit ve Správci úloh systému Windows.

    Ve výchozím nastavení jsou data o výkonu vzorkována každých 10 000 000 nezastavených cyklů hodin procesoru. To je přibližně 100 krát za sekundu na procesoru 1GH. Můžete zadat jednu z následujících možností pro změnu intervalu cyklu hodin nebo pro určení jiné události vzorkování.

   |Ukázková událost|Popis|
   |------------------|-----------------|
   |[/časovač](../profiling/timer.md) **:**`Interval`|Změní interval vzorkování na počet nezastavených hodinových `Interval`cyklů určených aplikací .|
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Změní událost vzorkování na chyby stránky. Pokud `Interval` je zadán, nastaví počet chyb stránky mezi ukázkami. Výchozí hodnota je 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Změní událost vzorkování na systémová volání z procesu do jádra operačního systému (syscalls). Pokud `Interval` je zadán, nastaví počet volání mezi vzorky. Výchozí hodnota je 10.|
   |[/counter](../profiling/counter.md) **:**`Config`|Změní událost vzorkování a interval na čítač `Config`výkonu procesoru a interval, který je zadán v .|

## <a name="control-data-collection"></a>Řízení shromažďování dat
 Když je spuštěna cílová aplikace, můžete použít *vsPerfCmd.exe* možnosti spustit a zastavit zápis dat do datového souboru profileru. Řízení shromažďování dat umožňuje shromažďovat data pro určitou část spuštění programu, jako je například spuštění nebo vypnutí aplikace.

#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat

- Následující dvojice možností **VSPerfCmd** spustit a zastavit shromažďování dat. Určete každou možnost na samostatném příkazovém řádku. Shromažďování dat můžete zapnout a vypnout vícekrát.

    |Možnost|Popis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**/globalon**) nebo zastaví (**/globaloff**) shromažďování dat pro všechny procesy.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) `PID`shromažďování dat pro proces, který je určen .|
    |[/attach](../profiling/attach.md) **:** `PID` [/detach](../profiling/detach.md)|**/attach** začne shromažďovat data pro `PID`proces určený společností . **/detach** zastaví shromažďování dat pro všechny procesy.|

## <a name="end-the-profiling-session"></a>Ukončení relace profilování
 Chcete-li ukončit relaci profilování, profiler musí být odpojen od všech profilovaných procesů a profiler musí být explicitně vypnut. Profiler můžete odpojit od aplikace, která byla profilována pomocí metody vzorkování zavřením aplikace nebo voláním **možnosti VSPerfCmd /detach.** Potom volání **VSPerfCmd /shutdown** možnost vypnout profiler a zavřete profilování datový soubor. Příkaz **VSPerfClrEnv /off** vymaže proměnné prostředí profilování.

#### <a name="to-end-a-profiling-session"></a>Ukončení relace profilování

1. Proveďte jeden z následujících kroků k odpojení profileru od cílové aplikace.

    - Typ **VSPerfCmd /detach**

         -nebo-

    - Zavřete cílovou aplikaci.

2. Vypněte profileru. Zadejte:

     **VSPerfCmd**  [/vypnutí](../profiling/shutdown.md)

3. (Nepovinné) Vymažte proměnné prostředí profilování. Zadejte:

     **VSPerfClrEnv /vypnuto**

## <a name="see-also"></a>Viz také
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
