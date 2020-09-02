---
title: 'Návod: profilace z příkazového řádku s použitím vzorkování | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1d53972f-6f35-4842-8c74-1b627f18c70a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96dfe49ce4e174680202cd60c3e8bca83cfbf575
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64820327"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>Návod: Profilování z příkazového řádku s použitím vzorkování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak profilovat aplikaci pomocí nástrojů příkazového řádku a vzorkování k identifikaci problémů s výkonem.  
  
 V tomto návodu provedete kroky procesu profilování spravované aplikace pomocí nástrojů příkazového řádku a pomocí vzorkování můžete izolovat a identifikovat problémy s výkonem v aplikaci.  
  
 V tomto návodu budete postupovat podle těchto kroků:  
  
- Profilování aplikace pomocí nástrojů příkazového řádku a vzorkování.  
  
- Analyzovat ukázkové výsledky profilace, které hledají a odstraňují problémy s výkonem.  
  
## <a name="prerequisites"></a>Předpoklady  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] nebo [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
- Zprostředkující porozumění [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)]  
  
- Zprostředkující porozumění práci s nástroji příkazového řádku  
  
- Kopie [ukázky PeopleTrax –](../profiling/peopletrax-sample-profiling-tools.md)  
  
- Chcete-li pracovat s informacemi poskytnutými profilací, je vhodné mít k dispozici informace o symbolech ladění.  
  
## <a name="command-line-profiling-using-the-sampling-method"></a>Profilace z příkazového řádku pomocí metody vzorkování  
 Vzorkování je metoda profilace, pomocí které se pravidelně dotazuje konkrétní proces, aby se zjistila aktivní funkce. Výsledná data poskytují počet, jak často byla funkce nad zásobníkem volání při vzorkování procesu.  
  
> [!NOTE]
> Nástroje příkazového řádku balíku nástrojů pro profilaci jsou umístěny v podadresáři \Team Tools\Performance Tools instalačního adresáře sady Visual Studio. Na 64 bitových počítačích jsou k dispozici obě verze nástroje 64 bitů a 32. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do příkazu samotného. Další informace najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). PeopleTrax – je 32 aplikace.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>Profilování aplikace PeopleTrax – pomocí metody vzorkování  
  
1. Nainstalujte ukázkovou aplikaci PeopleTrax – a sestavte prodejní verzi aplikace.  
  
2. Otevřete okno příkazového řádku a přidejte Nástroje pro profilaci adresář do proměnné prostředí místní cesta.  
  
3. Změňte pracovní adresář na adresář, který obsahuje binární soubory PeopleTrax –.  
  
4. Zadejte následující příkaz pro nastavení příslušných proměnných prostředí:  
  
    ```  
    VSPerfCLREnv /sampleon  
    ```  
  
5. Spusťte profilování spuštěním VSPerfCmd.exe, což je nástroj příkazového řádku, který řídí Profiler. Následující příkaz spustí aplikaci a Profiler v režimu vzorkování:  
  
    ```  
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe  
    ```  
  
     Spustí se proces profileru a připojí se k procesu PeopleTrax.exe. Proces profileru začne zapisovat shromážděná data profilování do souboru sestavy.  
  
6. Klikněte na **získat lidi**.  
  
7. Klikněte na **ExportData**.  
  
     Poznámkový blok otevře a zobrazí nový soubor, který obsahuje exportovaná data z **PeopleTrax –**.  
  
8. Zavřete Poznámkový blok a pak zavřete aplikaci **PeopleTrax –** .  
  
9. Vypněte profiler. Zadejte následující příkaz:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
10. K resetování proměnných prostředí použijte následující příkaz:  
  
    ```  
    VSPerfCLREnv /sampleoff  
    ```  
  
11. Data profilování jsou uložena v souboru. vsp analyzovat výsledky pomocí jedné z následujících metod:  
  
    - Otevřete soubor. vsp v integrovaném vývojovém prostředí sady Visual Studio.  
  
         ani  
  
    - Vygenerujte soubor hodnot oddělených čárkami (. csv) pomocí nástroje příkazového řádku VSPerfReport.exe. Chcete-li generovat sestavy pro použití mimo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozhraní IDE, použijte následující příkaz:  
  
        ```  
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all  
        ```  
  
## <a name="see-also"></a>Viz také  
 [Přehled výkonnostní relace](../profiling/performance-session-overview.md)   
 [Profilace z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)   
 [Zobrazení sestav výkonu](../profiling/performance-report-views.md)
