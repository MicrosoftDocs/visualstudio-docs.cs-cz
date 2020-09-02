---
title: 'Návod: profilování z příkazového řádku pomocí instrumentace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a37350cf274fbb551326ac96387330b0f3956e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64817641"
---
# <a name="walkthrough-command-line-profiling-using-instrumentation"></a>Návod: Profilování z příkazového řádku s použitím instrumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod vás provede profilací [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] samostatné aplikace za účelem shromažďování podrobných dat o časování a počtu volání pomocí metody instrumentace nástroje pro profilaci. V tomto návodu budete provádět následující úlohy:  
  
- Pomocí nástroje příkazového řádku [VSInstr](../profiling/vsinstr.md) vygenerujte instrumentované binární soubory.  
  
- Použijte nástroj [VSPerfCLREnv](../profiling/vsperfclrenv.md) k nastavení proměnných prostředí pro shromažďování dat profilování .NET.  
  
- Pomocí nástroje [VSPerfCmd](../profiling/vsperfcmd.md) Shromážděte data profilace.  
  
- Použijte nástroj [VSPerfReport](../profiling/vsperfreport.md) ke generování sestav založených na souborech dat profilování.  
  
## <a name="prerequisites"></a>Předpoklady  
  
- [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]  
  
- Zprostředkující porozumění C #  
  
- Zprostředkující porozumění práci s nástroji příkazového řádku  
  
- Kopie [ukázky PeopleTrax –](../profiling/peopletrax-sample-profiling-tools.md)  
  
- Chcete-li pracovat s informacemi poskytnutými profilací, je vhodné mít k dispozici informace o symbolech ladění. Další informace naleznete v tématu [How to: Reference Windows symbol Information](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="command-line-profiling-using-the-instrumentation-method"></a>Profilace z příkazového řádku pomocí metody instrumentace  
 Instrumentace je metoda profilace, kterou speciálně sestavené verze profilových binárních souborů obsahují funkce sondy, které shromažďují informace o časování na vstupu a výstupu do funkcí v instrumentované modulu. Vzhledem k tomu, že tato metoda profilace je více invazivní než vzorkování, dojde k většímu množství režie. Instrumentované binární soubory jsou také větší než soubory ladění nebo vydání a nejsou určeny pro nasazení.  
  
> [!NOTE]
> Neodesílat vašim zákazníkům instrumentované binární soubory. Instrumentované binární soubory mohou obsahovat několik rizik. Binární soubory obsahují informace, které usnadňují zpětnou analýzu a také rizika zabezpečení aplikace.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-instrumentation-method"></a>Profilování aplikace PeopleTrax – pomocí metody instrumentace  
  
1. Nainstalujte ukázkovou aplikaci PeopleTrax – a sestavte prodejní verzi.  
  
2. Otevřete okno příkazového řádku a přidejte **Nástroje pro profilaci** adresář do proměnné prostředí místní cesta.  
  
3. Změňte pracovní adresář na adresář obsahující binární soubory PeopleTrax –.  
  
4. Vytvořte adresář, který bude obsahovat sestavy založené na souborech. Zadejte následující příkaz:  
  
    ```  
    md Reports  
    ```  
  
5. K instrumentaci binárních souborů v aplikaci použijte nástroj příkazového řádku VSInstr. Na samostatné příkazové řádky zadejte následující příkazy:  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Poznámka:** Ve výchozím nastavení VSInstr ukládá neinstrumentované zálohování původního souboru. Název záložního souboru má příponu. orig. Například původní verze "MyApp.exe" by se uložila jako "MyApp.exe. orig".  
  
6. Zadejte následující příkaz pro nastavení příslušných proměnných prostředí:  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7. Chcete-li spustit Profiler, zadejte následující příkaz:  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8. Po spuštění profileru v režimu trasování spusťte instrumentované verze procesu PeopleTrax.exe, abyste mohli shromažďovat data.  
  
     Zobrazí se okno aplikace **PeopleTrax –** .  
  
9. Klikněte na **získat lidi**.  
  
     Mřížka dat PeopleTrax – se naplní daty.  
  
10. Klikněte na **exportovat data**.  
  
     Spustí Poznámkový blok a zobrazí nový soubor, který obsahuje seznam lidí z aplikace **PeopleTrax –** .  
  
11. Zavřete Poznámkový blok a pak zavřete aplikaci **PeopleTrax –** .  
  
12. Vypněte profiler. Zadejte následující příkaz:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Zadáním následujícího příkazu resetujete proměnné prostředí:  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. Pomocí nástroje VSPerfReport můžete vygenerovat soubory sestav s hodnotami oddělenými čárkami (. csv). Zadejte:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     Vygenerované sestavy můžete analyzovat v programu v tabulce nebo můžete použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE k analýze dat profilování v souboru Report. vsp. Další informace najdete v tématu [Analýza dat nástrojů výkonu](../profiling/analyzing-performance-tools-data.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled výkonnostní relace](../profiling/performance-session-overview.md)   
 [Profilace z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)   
 [Zobrazení sestav výkonu](../profiling/performance-report-views.md)
