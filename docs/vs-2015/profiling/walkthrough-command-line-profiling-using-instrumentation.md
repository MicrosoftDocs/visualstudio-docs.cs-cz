---
title: 'Návod: Profilace z příkazového řádku pomocí instrumentace | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b670ef29ca2edcc96ed8886b82dd5d7c6cb416b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741470"
---
# <a name="walkthrough-command-line-profiling-using-instrumentation"></a>Návod: Profilace z příkazového řádku s použitím instrumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento názorný postup vás provede profilace [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] samostatnou aplikaci pro shromáždění podrobných časových a údaje o počtu volání pomocí metody instrumentace z nástrojů pro profilaci. V tomto návodu provedete následující úlohy:  
  
-   Použití [VSInstr](../profiling/vsinstr.md) nástroj příkazového řádku ke generování instrumentované binární soubory.  
  
-   Použití [VSPerfCLREnv](../profiling/vsperfclrenv.md) nástroj k nastavení proměnných prostředí pro shromažďování dat profilování rozhraní .NET.  
  
-   Použití [VSPerfCmd](../profiling/vsperfcmd.md) nástroje ke shromažďování dat profilace.  
  
-   Použití [VSPerfReport](../profiling/vsperfreport.md) nástroj pro generování sestav na základě souboru dat profilování.  
  
## <a name="prerequisites"></a>Požadavky  
  
-   [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]  
  
-   Zprostředkující Principy jazyka C#  
  
-   Zprostředkující znalost práce pomocí nástrojů příkazového řádku  
  
-   Kopie [peopletrax – ukázka](../profiling/peopletrax-sample-profiling-tools.md)  
  
-   Pro práci s profilace na základě informací poskytnutých, je nejlepší mít ladění k dispozici informace o symbolech. Další informace najdete v tématu [postupy: odkaz na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="command-line-profiling-using-the-instrumentation-method"></a>Příkazového řádku pro profilaci pomocí metody instrumentace  
 Instrumentace je metodu profilace, podle kterého obsahují speciálně vytvořených verze profilovaných binárních souborů testu funkce, které shromažďovat informace o časování na vstupu a výstupu funkcí v instrumentovaném modulu. Vzhledem k tomu, že tato metoda profilování invazivnější než vzorkování, budou vám účtovány větší množství režie. Instrumentované binární soubory jsou také větší než ladění nebo vydání binární soubory a nejsou určeny pro nasazení.  
  
> [!NOTE]
>  Neodesílejte instrumentované binární soubory pro vaše zákazníky. Instrumentované binární soubory může obsahovat několik rizik. Binární soubory zahrnují informace, které vaše aplikace usnadňuje zpětné analýzy, jakož i bezpečnostní rizika.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-instrumentation-method"></a>Chcete-li Profilovat aplikaci PeopleTrax pomocí metody instrumentace  
  
1.  Nainstalovat ukázkovou aplikaci PeopleTrax a vytvořit vydanou verzi.  
  
2.  Otevřete okno příkazového řádku a přidejte **nástrojů pro profilaci sady** adresáře do místní proměnné prostředí Path.  
  
3.  Změňte pracovní adresář na adresář obsahující PeopleTrax binární soubory.  
  
4.  Vytvořte adresář obsahující soubor na základě sestav. Zadejte následující příkaz:  
  
    ```  
    md Reports  
    ```  
  
5.  Pomocí nástroje příkazového řádku VSInstr instrumentace binárních souborů v aplikaci. Na samostatné řádky příkazu zadejte následující příkazy:  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Poznámka:** ve výchozím nastavení, uloží nástroj VSInstr neinstrumentovaného záloha původního souboru. Název záložního souboru má příponu. orig. Například původní verzi "MyApp.exe" by se uložila jako "MyApp.exe.orig."  
  
6.  Zadejte následující příkaz nastavit příslušné proměnné prostředí:  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7.  Chcete-li spustit profiler, zadejte následující příkaz:  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8.  Po spuštění profileru v režimu trace spusťte instrumentovanou verzí procesu PeopleTrax.exe shromažďovat data.  
  
     **PeopleTrax** se zobrazí okno aplikace.  
  
9. Klikněte na tlačítko **získá osoby**.  
  
     Datová mřížka PeopleTrax naplní daty.  
  
10. Klikněte na tlačítko **exportovat Data**.  
  
     Poznámkový blok spustí a zobrazí nový soubor, který obsahuje seznam lidí z **PeopleTrax** aplikace.  
  
11. Zavřete poznámkový blok a pak **PeopleTrax** aplikace.  
  
12. Vypněte profiler. Zadejte následující příkaz:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Zadejte následující příkaz k resetování proměnné prostředí:  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. Použijte vsperfreport – nástroj pro generování nebo soubory sestavy hodnot oddělených čárkami (CSV). Typ:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     Můžete analyzovat vygenerovaných sestav v tabulkovém programu nebo můžete použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE k analýze dat profilace v souboru Report.vsp. Další informace najdete v tématu [analýza dat nástrojů pro výkon](../profiling/analyzing-performance-tools-data.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled výkonnostní relace](../profiling/performance-session-overview.md)   
 [Profilace z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Nástroj VSPerfCmd](../profiling/vsperfcmd.md)   
 [Porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)   
 [Zobrazení sestav výkonu](../profiling/performance-report-views.md)



