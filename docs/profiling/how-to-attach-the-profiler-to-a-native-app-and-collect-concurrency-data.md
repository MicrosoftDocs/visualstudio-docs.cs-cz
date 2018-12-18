---
title: Připojení profileru k nativní aplikaci a shromažďování dat souběžnosti
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: ef2c5a7cbd21cba8b60944c2e3f45e4af05e630a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067042"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>Postupy: připojení profileru k nativní samostatné aplikaci a shromažďování dat souběžnosti pomocí příkazového řádku
Tento článek popisuje způsob použití [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vláknu příkazového řádku nástrojů pro profilaci k připojení profileru k běžící nativní samostatné aplikaci (C/C++) a shromažďovat data kolizí.  
  
> [!NOTE]
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v *\Team Tools\Performance nástroje* jedná o podadresář adresáře instalace sady Visual Studio. Na 64bitových počítačích jsou k dispozici 64bitové i 32bitové verze nástrojů. Chcete-li využívat nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH **příkazového řádku** okno nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadejte cestu k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Zatímco je profiler připojen k aplikaci, lze pozastavit a obnovit sběr dat. Chcete-li ukončit relaci profilování, musí Profiler již připojen k aplikaci a Profiler musí být explicitně vypnut.  
  
## <a name="attach-the-profiler-to-a-running-native-application"></a>Připojení profileru k běžící nativní aplikace  
  
#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>K připojení profileru k běžící nativní aplikace  
  
1.  Na příkazovém řádku zadejte následující příkaz:  
  
     [Nástroj VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**  
  
     V následující tabulce můžete použít některou z možností **/start:concurrency** možnost.  
  
    |Možnost|Popis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`Username`|Určuje volitelnou doménu a uživatelské jméno účtu, který má být udělen přístup k profileru.|  
    |[/ crosssession](../profiling/crosssession.md)|Umožňuje profilování procesů v jiných přihlašovacích relacích.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Určuje čítač výkonu Windows má být shromážděn během profilování.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Použití s **/wincounter** pouze. Určuje počet milisekund mezi událostmi sběru čítače výkonu Windows. Výchozí hodnota je 500.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Určuje událost trasování událostí pro Windows (ETW) má být shromážděn během profilování. Události trasování událostí pro Windows jsou shromážděny v samostatném (ETL) soubor.|  
  
2.  Připojení profileru k cílové aplikaci tak, že zadáte následující příkaz:  
  
     **Nástroj VSPerfCmd**[/ attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`}  
  
     `PID` Určuje ID procesu cílové aplikace. ID všech spuštěných procesů lze zobrazit ve Správci úloh Windows.  
  
## <a name="control-data-collection"></a>Řízení shromažďování dat  
 Dokud je cílová aplikace spuštěna, lze sběr dat řídit spouštěním či pozastavováním zápisu dat do souboru s použitím *VSPerfCmd.exe* možnosti. Řízením sběru dat může shromažďovat data pro určitou část provádění programu, například spouštění či ukončování aplikace.  
  
#### <a name="to-start-and-stop-data-collection"></a>Spuštění a zastavení shromažďování dat  
  
-   Následující páry možností v následující tabulce spouští a zastavují sběr dat. Každou možnost zadejte na samostatný příkazový řádek. Sběr dat lze zapnout a vypnout několikrát.  
  
    |Možnost|Popis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Spustí (**globalon**) nebo zastaví (**/globaloff**) sběr dat pro všechny procesy.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Spustí (**/processon**) nebo zastaví (**/processoff**) sběr dat pro proces, který ID procesu (`PID`) určuje.|  
    |[/ attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ attach** spustí sběr dat pro proces, který ID procesu (`PID`) nebo názvem procesu (*ProcName*) určuje. **/ detach** zastaví sběr dat pro zadaný proces nebo pro všechny procesy, pokud není zadán žádný proces.|  
  
## <a name="end-the-profiling-session"></a>Ukončit relaci profilování  
 Chcete-li ukončit relaci profilování, profiler nesmí pokračovat ve shromažďování dat. Zastavit shromažďování dat z aplikace, která je profilována pomocí metody odběru vzorků jejím ukončením nebo vyvoláním **VSPerfCmd / detach** možnost. Poté je zapotřebí vyvolat **VSPerfCmd/Shutdown** možnost profiler vypne a uzavře soubor dat profilování.  
  
#### <a name="to-end-a-profiling-session"></a>Chcete-li ukončit relaci profilování  
  
1.  Odpojte profiler od cílové aplikace nebo ukončením tak, že zadáte následující příkaz:  
  
     **Nástroj VSPerfCmd / odpojení**  
  
2.  Vypněte profiler zadáním následujícího příkazu:  
  
     **Nástroj VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)