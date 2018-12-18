---
title: Diagnostika problémů po nasazení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3463eab-a352-4d17-8551-adbaad526db0
caps.latest.revision: 66
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6c4c60265fda66f7506fe6d886fa671527c1587
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785453"
---
# <a name="diagnose-problems-after-deployment"></a>Diagnostika problémů po nasazení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagnostikovat problémy ve vaší webové aplikaci ASP.NET po nasazení s použitím technologie IntelliTrace, přidejte informace sestavení s vaší verzí umožňuje sadě Visual Studio automaticky vyhledá správné zdrojové soubory a soubory symbolů, které jsou nutné k ladění protokolu IntelliTrace.  
  
 Pokud používáte agenta Microsoft Monitoring Agent do správy nástroje IntelliTrace, budete také muset nastavit nastavte application performance monitoring pro aplikace na webovém serveru. To zaznamenává diagnostické události, když vaše aplikace běží a uloží události do souboru protokolu IntelliTrace. Můžete pak podívejte se na události v sadě Visual Studio Enterprise (ale ne Professional nebo Community), přejděte do kódu, kde k události došlo, podívejte se na zaznamenané hodnoty v tomto okamžiku v čase a posunout dopředu nebo dozadu prostřednictvím kódu, který spustil. Po nalezení a vyřešení problému, opakujte cyklus sestavení, vydání a sledování vaší verze, abyste mohli vyřešit potenciální potíže v budoucnosti dříve a rychleji.  
  
 ![Kód, sestavení, vydání, monitorování, Diagnostika, opravy](../debugger/media/ffr-cycle.png "FFR_Cycle")  
  
 **Budete potřebovat:**  
  
-   Visual Studio 2015 nebo Team Foundation Server 2015, 2013, 2012 nebo 2010 nastavte vaše sestavení  
  
-   Microsoft Monitoring Agent monitorování aplikací a záznam diagnostických dat  
  
-   Visual Studio Enterprise (ale ne edice Professional nebo Community) ke kontrole diagnostických dat a ladění kódu s použitím technologie IntelliTrace  
  
##  <a name="SetUpBuild"></a> Krok 1: Zahrnují informace o vaší verze sestavení  
 Nastavení procesu sestavení k vytvoření manifestu sestavení (soubor BuildInfo.config) pro webový projekt a zahrnují tento manifest s vaší verzí. Tento manifest obsahuje informace o projektu, správy zdrojového kódu a systém sestavení, které byly použity k vytvoření konkrétního sestavení. Tyto informace pomáhají aplikaci Visual Studio po otevření protokolu nástroje IntelliTrace zaznamenané události zkontrolujte vyhledání odpovídajícího zdroje a symbolů.  
  
###  <a name="AutomatedBuild"></a> Vytvoření manifestu sestavení pro automatické sestavení pomocí Team Foundation Server  
 Ať už používáte správu verzí Team Foundation nebo Git, postupujte následovně.  
  
####  <a name="TFS2013"></a> Team Foundation Server 2013  
 Nastavte definici sestavení přidat umístění zdroje, sestavení a symboly do manifestu sestavení (soubor BuildInfo.config). Team Foundation Build automaticky vytvoří tento soubor a umístí jej do výstupní složky vašeho projektu.  
  
1. [Upravte definici sestavení nebo vytvořte novou definici sestavení.](http://msdn.microsoft.com/library/1c2eca2d-9a65-477e-9b23-0678ff7882ee)  
  
    ![Zobrazit sestavení definice v TFS 2013](../debugger/media/ffr-tfs2013viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")  
  
2. Zvolte výchozí šablonu (TfvcTemplate.12.xaml) nebo vlastní šablonu.  
  
    ![Zvolte šablonu procesu sestavení &#45; TFS 2013](../debugger/media/ffr-tfs2013buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")  
  
3. Zadejte, kam chcete uložit soubor symbolů (PDB), aby zdroj automaticky indexován.  
  
    Pokud používáte vlastní šablonu, ujistěte se, že šablona má aktivitu pro indexování zdroje. Později přidáte argument MSBuild zadat, kam chcete uložit soubory symbolů.  
  
    ![Nastavit cestu symbolů v definici sestavení TFS 2013](../debugger/media/ffr-tfs2013builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")  
  
    Další informace o symbolech naleznete v tématu [publikování dat symbolů](http://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6).  
  
4. Přidejte tento argument MSBuild, čímž zahrnout vaše TFS a umístění symbolů do souboru manifestu sestavení:  
  
    **/p:IncludeServerNameInBuildInfo = true**  
  
    Kdokoli, kdo má přístup k webový server může zobrazit tato umístění v manifestu sestavení. Ujistěte se, že je zdrojový server zabezpečený.  
  
5. Pokud používáte vlastní šablonu, přidejte tento argument MSBuild zadat, kam uložit symboly:  
  
    **/p:BuildSymbolStorePath =**\<*cesty k symbolům*>  
  
    ![Zahrnout informace o serveru sestavení do definice sestavení TFS 2013](../debugger/media/ffr-tfs2013builddefincludeserverinfo.png "FFR_TFS2013BuildDefIncludeServerInfo")  
  
    A přidejte tyto řádky do souboru webového projektu (.csproj, .vbproj):  
  
   ```  
   <!-- Import the targets file. Change the folder location as necessary. -->  
      <Import Project=""$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\BuildInfo\Microsoft.VisualStudio.ReleaseManagement.BuildInfo.targets" />  
  
   ```  
  
6. Spusťte nové sestavení.  
  
   **Krok 2:** [krok 2: Vydávejte svoje aplikace](#DeployRelease)  
  
####  <a name="TFS2012_2010"></a> Team Foundation Server 2012 nebo 2010  
 Postupujte podle těchto kroků k automatickému vytvoření manifestu sestavení (soubor BuildInfo.config) pro váš projekt a vložit ho do výstupní složky vašeho projektu. Soubor se zobrazí jako "*ProjectName*. BuildInfo.config"ve výstupní složce, ale je přejmenován na"BuildInfo.config"ve složce nasazení po publikování aplikace.  
  
1. Visual Studio 2013 (libovolná edice) nainstalujte na svém serveru sestavení Team Foundation.  
  
2. V rámci definice sestavení zadejte umístění pro ukládání symbolů tak, aby byl zdroj automaticky indexován.  
  
    Pokud používáte vlastní šablonu, ujistěte se, že šablona má aktivitu pro indexování zdroje.  
  
3. Do definice sestavení přidejte následující argumenty nástroje MSBuild:  
  
   -   **/p:VisualStudioVersion = 12.0**  
  
   -   **/p:MSBuildAssemblyVersion = 12.0**  
  
   -   **/TV:12.0**  
  
   -   **/p:IncludeServerNameInBuildInfo = true**  
  
   -   **/p:BuildSymbolStorePath =**\<*cesty k symbolům*>  
  
4. Spusťte nové sestavení.  
  
   **Krok 2:** [krok 2: Vydávejte svoje aplikace](#DeployRelease)  
  
###  <a name="ManualBuild"></a> Vytvoření manifestu sestavení pro ruční sestavení pomocí sady Visual Studio  
 Postupujte podle těchto kroků k automatickému vytvoření manifestu sestavení (soubor BuildInfo.config) pro váš projekt a vložit ho do výstupní složky vašeho projektu. Soubor se zobrazí jako "*ProjectName*. BuildInfo.config"ve výstupní složce, ale je přejmenován na"BuildInfo.config"ve složce nasazení po publikování aplikace.  
  
1. V **Průzkumníka řešení**, uvolněte váš webový projekt.  
  
2. Otevřete soubor projektu (.csproj, .vbproj). Přidejte tyto řádky:  
  
   ```xml  
   <!-- **************************************************** -->  
   <!-- Build info -->  
   <PropertyGroup>  
      <!-- Generate the BuildInfo.config file -->  
      <GenerateBuildInfoConfigFile>True</GenerateBuildInfoConfigFile>  
      <!-- Include server name in build info -->   
      <IncludeServerNameInBuildInfo>True</IncludeServerNameInBuildInfo>   
      <!-- Include the symbols path so Visual Studio can find the matching deployed code when you start debugging. -->  
      <BuildSymbolStorePath><path to symbols></BuildSymbolStorePath>  
   </PropertyGroup>  
   <!-- **************************************************** -->  
   ```  
  
3. Proveďte vrácení aktualizovaného souboru projektu se změnami.  
  
4. Spusťte nové sestavení.  
  
   **Krok 2:** [krok 2: Vydávejte svoje aplikace](#DeployRelease)  
  
###  <a name="MSBuild"></a> Vytvoření manifestu sestavení pro ruční sestavení pomocí MSBuild.exe  
 Přidejte tyto argumenty při spuštění sestavení:  
  
 **/p:GenerateBuildInfoConfigFile = true**  
  
 **/p:IncludeServerNameInBuildInfo = true**  
  
 **/p:BuildSymbolStorePath =**\<*cesty k symbolům*>  
  
##  <a name="DeployRelease"></a> Krok 2: Vydávejte svoje aplikace  
 Pokud používáte [balíčku Web.Deploy](http://msdn.microsoft.com/library/dd394698.aspx) , která byla vytvořena procesem sestavení pro nasazení vaší aplikace, manifest sestavení automaticky přejmenován z "*ProjectName*. BuildInfo.config"k"BuildInfo.config"a je umístěn ve stejné složce se souborem Web.config vaší aplikace na webovém serveru.  
  
 Pokud nasadíte aplikaci pomocí jiné metody, ujistěte se, že manifest sestavení je přejmenován ze "*ProjectName*. BuildInfo.config"k"BuildInfo.config"a je umístěn ve stejné složce se souborem Web.config vaší aplikace na webovém serveru.  
  
## <a name="step-3-monitor-your-app"></a>Krok 3: Sledování vaší aplikace  
 Nastavte monitorování výkonu aplikací na webovém serveru tak, aby sledování vaší aplikace pro problémy, zaznamenat diagnostické události a uložit tyto události do souboru protokolu IntelliTrace. Zobrazit [sledování vaší verze problémů s nasazováním](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
##  <a name="InvestigateEvents"></a> Krok 4: Nalezení příčiny problému  
 Na svém vývojovém počítači nebo jiným počítačům zkontrolujte zaznamenané události a ladění kódu pomocí nástroje IntelliTrace, budete potřebovat Visual Studio Enterprise. Můžete také použít nástroje jako CodeLens, mapy ladicího programu a mapy kódu při diagnostice problému.  
  
### <a name="open-the-intellitrace-log-and-matching-solution"></a>Otevření protokolu nástroje IntelliTrace a odpovídajícího řešení  
  
1.  Otevřete protokol nástroje IntelliTrace (soubor .iTrace) z Visual Studio Enterprise. Nebo stačí dvakrát klikněte na soubor, pokud máte Visual Studio Enterprise ve stejném počítači.  
  
2.  Zvolte **otevřete řešení** mít Visual Studio automaticky otevřela odpovídající řešení nebo projekt, pokud projekt nebyl vytvořen jako součást řešení. [Otázka: protokol nástroje IntelliTrace neobsahuje informace o mé nasazené aplikaci. Proč k tomu? Co mám dělat?](#InvalidConfigFile)  
  
     Automaticky odloží sada Visual Studio všechny čekající změny při otevření odpovídajícího řešení nebo projektu. Chcete-li získat další podrobnosti o této sadě odložených změn, podívejte **výstup** okno nebo **Team Exploreru**.  
  
     Než provedete jakékoli úpravy, ujistěte se, že máte správný zdroj. Pokud používáte větvení, když pracujete v jiné větvi, než kde sada Visual Studio najde odpovídající zdroj, jako je větev vydané verze.  
  
     ![Otevřít řešení ze protokolu IntelliTrace](../debugger/media/ffr-itsummarypageopensolution.png "FFR_ITSummaryPageOpenSolution")  
  
     Pokud máte existující pracovní prostor mapován na toto řešení nebo projekt, vybere sada Visual Studio tento pracovní prostor k vložení, který našel zdroj.  
  
     ![Otevřít ze správy zdrojových kódů pro mapovanou prostoru](../debugger/media/ffr-openprojectfromsourcecontrol-mapped.png "FFR_OpenProjectFromSourceControl_Mapped")  
  
     V opačném případě zvolte jiný pracovní prostor nebo vytvořte nový pracovní prostor. Sada Visual Studio bude mapovat celou větev na tento pracovní prostor.  
  
     ![Otevřít ze správy zdrojových kódů &#45; vytvořit nový pracovní prostor](../debugger/media/ffr-openprojectfromsourcecontrol-createnewworkspace.png "FFR_OpenProjectFromSourceControl_CreateNewWorkspace")  
  
     Chcete-li vytvořit pracovní prostor s konkrétními mapováními nebo názvem, který není názvem vašeho počítače, zvolte **spravovat**.  
  
     [Otázka: Proč sada Visual Studio říká, že je že můj vybraný pracovní prostor nezpůsobilý?](#IneligibleWorkspace)  
  
     [Otázka: Proč nemohu pokračovat, dokud nevyberu kolekci týmu nebo jinou kolekci?](#ChooseTeamProject)  
  
### <a name="diagnose-a-performance-problem"></a>Diagnostikování problému s výkonem  
  
1.  V části **narušení výkonu**, zkontrolujte zaznamenané události výkonu, jejich celkové časy spuštění a další informace o události. Pak přejděte hlouběji do metod, které byly volány během konkrétní události výkonu.  
  
     ![Zobrazit podrobnosti o událostech výkonu](../debugger/media/ffr-itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  
  
     Můžete také pouze dvakrát kliknout na událost.  
  
2.  Na stránce události zkontrolujte časy spuštění těchto volání. Vyhledejte pomalé volání ve stromu spuštění.  
  
     Pokud máte více volání vnořených nebo jiných, zobrazují se nejpomalejší volání ve vlastním oddílu.  
  
     Rozbalte volání za účelem kontroly všech vnořených volání a hodnot, které byly zaznamenány v daném časovém okamžiku. Potom spusťte ladění z tohoto volání.  
  
     ![Spuštění ladění od volání metody](../debugger/media/ffr-itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  
  
     Můžete také pouze dvakrát kliknout na volání.  
  
     Pokud je metoda v kódu aplikace, sada Visual Studio přejde na tuto metodu.  
  
     ![Přejděte ke kódu aplikace od události výkonu](../debugger/media/ffr-itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  
  
     Nyní můžete zkontrolovat další zaznamenané hodnoty, zásobník volání, procházet kódem nebo použít **IntelliTrace** okno [přesune zpět nebo vpřed "v čase" mezi ostatními metodami](../debugger/intellitrace.md) , které byly volány během této události výkonu. [Co je všechny tyto další události a informace v protokolu nástroje IntelliTrace? ](../debugger/using-saved-intellitrace-data.md) [Co dalšího můžu dělat odsud?](#WhatElse) [Přečtěte si další informace o událostech výkonu?](http://blogs.msdn.com/b/visualstudioalm/archive/2013/09/20/performance-details-in-intellitrace.aspx)  
  
### <a name="diagnose-an-exception"></a>Diagnostikování výjimky  
  
1.  V části **Data výjimky**, zkontrolujte zaznamenané události výjimky, jejich typy, zprávy, a kdy výjimka nastala. Pokud se chcete dostat hlouběji do kódu, spusťte ladění od poslední události ve skupině výjimek.  
  
     ![Spuštění ladění od události výjimky](../debugger/media/ffr-itsummarypageexception.png "FFR_ITSummaryPageException")  
  
     Můžete také pouze dvakrát kliknout na událost.  
  
     Pokud došlo k výjimce v kódu aplikace, sada Visual Studio pokračuje tam, kde došlo k výjimce.  
  
     ![Přejděte na kód aplikace z události výjimky](../debugger/media/ffr-itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  
  
     Nyní můžete zkontrolovat další zaznamenané hodnoty, zásobník volání, nebo použít **IntelliTrace** okno [přesune zpět nebo vpřed "v čase" mezi ostatními zaznamenanými událostmi](../debugger/intellitrace.md), souvisejícím kódem a zaznamenanými hodnotami v Tyto body v čase. [Co je všechny tyto další události a informace v protokolu nástroje IntelliTrace?](../debugger/using-saved-intellitrace-data.md)  
  
###  <a name="WhatElse"></a> Co dalšího můžete mohu ještě udělat?  
  
-   [Získejte další informace o tomto kódu](../ide/find-code-changes-and-other-history-with-codelens.md). Najít odkazy na tento kód, jeho historii změn, související chyby, pracovní položky, revize kódu nebo testy částí – vše bez opuštění editoru – použijte indikátory CodeLens v editoru.  
  
     ![Funkce CodeLens &#45; zobrazit odkazy na tento kód](../debugger/media/ffr-itsummarypageperformancecodelensreferences.png "FFR_ITSummaryPagePerformanceCodeLensReferences")  
  
     ![Funkce CodeLens &#45; změnit zobrazení historie pro tento kód](../debugger/media/ffr-itsummarypageperformancecodelensauthors.png "FFR_ITSummaryPagePerformanceCodeLensAuthors")  
  
-   [Při ladění namapujte příslušné místo v kódu.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) Chcete-li vizuálně sledovat metody, které byly volány během relace ladění, namapujte zásobník volání.  
  
     ![Mapování zásobníku volání při ladění](../debugger/media/ffr-itsummarypageperformancedebuggermap.png "FFR_ITSummaryPagePerformanceDebuggerMap")  
  
###  <a name="FAQ"></a> Q & A  
  
####  <a name="WhyInclude"></a> Otázka: Proč obsahují informace o projektu, správy zdrojového kódu, sestavení a symboly s vydání verze?  
 Visual Studio používá tyto informace k vyhledání odpovídajícího řešení a zdroje pro vydání, který se snažíte ladit. Po otevření protokolu nástroje IntelliTrace a vyberte událost pro spuštění ladění, Visual Studio používá symboly můžete najít a zobrazit je kód kde k události došlo. Potom můžete podívat na hodnoty, které byly zaznamenány a posunout dopředu nebo dozadu prostřednictvím provádění kódu.  
  
 Pokud používáte TFS a tyto informace není v manifest sestavení (soubor BuildInfo.config), Visual Studio vyhledá odpovídajícího zdroje a symboly na váš aktuálně připojený server TFS. Pokud aplikace Visual Studio nemůže najít správné sady TFS nebo odpovídající zdroj, budete vyzváni k výběru jiné sady TFS.  
  
####  <a name="InvalidConfigFile"></a> Otázka: protokol nástroje IntelliTrace neobsahuje informace o mé nasazené aplikaci. Proč k tomu? Co mám udělat?  
 K tomu může dojít při nasazení z vývojového počítače nebo nejste připojeni k serveru TFS během nasazení.  
  
1.  Přejděte do složky vašeho projektu nasazení.  
  
2.  Vyhledání a otevření manifestu sestavení (soubor BuildInfo.config).  
  
3.  Ujistěte se, že soubor obsahuje požadované informace:  
  
- **ProjectName**  
  
   Název projektu v sadě Visual Studio. Příklad:  
  
  ```  
  <ProjectName>FabrikamFiber.Extranet.Web</ProjectName>  
  ```  
  
- **SourceControl**  
  
- Informace o systému správy zdrojů a tyto požadované vlastnosti:  
  
  - **TFS**  
  
    - **ProjectCollectionUri**: identifikátor URI pro Team Foundation Server a projekt kolekce  
  
    - **ProjectItemSpec**: cesta k souboru projektu vaší aplikace (.csproj nebo .vbproj)  
  
    - **ProjectVersionSpec**: verze projektu  
  
      Příklad:  
  
    ```  
    <SourceControl type="TFS">  
       <TfsSourceControl>  
          <ProjectCollectionUri>http://fabrikamfiber:8080/tfs/FabrikamFiber</ProjectCollectionUri>  
          <ProjectItemSpec>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectItemSpec>  
          <ProjectVersionSpec>LFabrikamFiber_BuildAndPublish_20130813@$/WorkInProgress</ProjectVersionSpec>  
       </TfsSourceControl>  
    </SourceControl>  
    ```  
  
  - **Git**  
  
    - **GitSourceControl**: umístění **GitSourceControl** schématu  
  
    - **RepositoryUrl**: identifikátor URI pro Team Foundation Server, kolekce projektu a úložiště Git  
  
    - **ProjectPath**: cesta k souboru projektu vaší aplikace (.csproj nebo .vbproj)  
  
    - **CommitId**: id potvrzení  
  
      Příklad:  
  
    ```  
    <SourceControl type="Git">   
       <GitSourceControl xmlns="http://schemas.microsoft.com/visualstudio/deploymentevent_git/2013/09">  
          <RepositoryUrl>http://gittf:8080/tfs/defaultcollection/_git/FabrikamFiber</RepositoryUrl>  
          <ProjectPath>/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectPath>  
          <CommitId>50662c96502dddaae5cd5ced962d9f14ec5bc64d</CommitId>  
       </GitSourceControl>  
    </SourceControl>  
    ```  
  
- **Sestavení**  
  
   Informace o systému sestavení, buď `"TeamBuild"` nebo `"MSBuild"`, a tyto požadované vlastnosti:  
  
  - **BuildLabel** (pro TeamBuild): název sestavení a číslo. Tento popisek se také používá jako název události nasazení. Další informace o čísla sestavení najdete v tématu [použít sestavení čísla poskytnout smysluplné názvy k dokončeným sestavením](http://msdn.microsoft.com/library/1f302e9d-4b0a-40b5-8009-b69ca6f988c3).  
  
  - **SymbolPath** (doporučeno): seznam identifikátorů URI pro symboly (soubor PDB) oddělený středníky. Tyto identifikátory URI mohou být adresy URL nebo UNC. Díky tomu snadněji pro Visual Studio najít odpovídající symboly vám pomoci s laděním.  
  
  - **BuildReportUrl** (pro TeamBuild): umístění sestavy sestavení na serveru TFS  
  
  - **BuildId** (pro TeamBuild): identifikátor URI pro sestavení podrobnosti v sadě TFS. Pomocí tohoto identifikátoru URI slouží také jako ID události nasazení. To je id musí být jedinečné, pokud nepoužíváte typ TeamBuild.  
  
  - **BuiltSolution**: cesta k souboru řešení, které Visual Studio používá k vyhledání a otevření odpovídajícího řešení. Toto je obsah **SolutionPath** vlastnosti Msbuildu.  
  
    Příklad:  
  
  - **TFS**  
  
    ```  
    <Build type="TeamBuild">  
       <MsBuild>  
          <BuildLabel kind="label">FabrikamFiber_BuildAndPublish_20130813.1</BuildLabel>  
          <SymbolPath>\\fabrikamfiber\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
          <BuildReportUrl kind="informative, url" url="http://fabrikamfiber:8080/tfs/FabrikamFiber/_releasePipeline/FindRelease?buildUri=fabrikamfiber%3a%2f%2f%2fBuild%2fBuild%2f448">Build Report Url</BuildReportUrl>  
          <BuildId kind="id">1c4444d2-518d-4673-a590-dce2773c7744,fabrikamfiber:///Build/Build/448</BuildId>  
          <BuiltSolution>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
       </MsBuild>  
    </Build>  
    ```  
  
  - **Git**  
  
    ```  
    <Build type="MSBuild">   
       <MSBuild>  
          <SymbolPath>\\gittf\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
          <BuiltSolution>/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
       </MSBuild>  
    </Build>  
    ```  
  
####  <a name="IneligibleWorkspace"></a> Otázka: Proč sada Visual Studio říká, že je že můj vybraný pracovní prostor nezpůsobilý?  
 **Odpověď:** vybraný pracovní prostor neobsahuje žádná mapování mezi složkou správy zdrojového kódu a místní složky. Chcete-li vytvořit mapování pro tento pracovní prostor, zvolte **spravovat**. V opačném případě zvolte již namapovaný pracovní prostor nebo vytvořte nový pracovní prostor.  
  
 ![Otevřít ze správy zdrojových kódů s žádné namapovaný pracovní prostor](../debugger/media/ffr-openprojectfromsourcecontrol-notmapped.png "FFR_OpenProjectFromSourceControl_NotMapped")  
  
####  <a name="ChooseTeamProject"></a> Otázka: Proč nemohu pokračovat, dokud nevyberu kolekci týmu nebo jinou kolekci?  
 **Odpověď:** k tomu může dojít z některého z těchto důvodů:  
  
-   Sada Visual Studio není připojena k serveru TFS.  
  
     ![Otevřít ze správy zdrojových kódů &#45; Nepřipojeno](../debugger/media/ffr-openprojectfromsourcecontrol-notconnected.png "FFR_OpenProjectFromSourceControl_NotConnected")  
  
-   Sada Visual Studio nenašla řešení nebo projekt v aktuální kolekci týmu.  
  
     Když soubor manifestu sestavení (\<*ProjectName*>. BuildInfo.config) neurčuje, kde může sada Visual Studio najít odpovídající zdroj, používá Visual Studio váš aktuálně připojený TFS k vyhledání odpovídajícího řešení nebo projektu. Pokud nemá aktuální kolekce týmu odpovídající zdroj, vyzve vás sada Visual Studio k připojení k jiné kolekci týmu.  
  
-   Sada Visual Studio nenalezla řešení nebo projektu v kolekci specifikované souborem manifestu sestavení (\<*ProjectName*>. BuildInfo.config).  
  
     Zadaný server TFS nemusí již mít odpovídající nebo dokonce existující zdroj. Možným důvodem je, že jste migrovali na nový server TFS. Pokud zadaný server TFS neexistuje, může přibližně po minutě vypršet časový limit sady Visual Studio a poté budete vyzváni k připojení do jiné kolekce. Chcete-li pokračovat, připojte se ke správnému serveru TFS.  
  
     ![Otevřít ze správy zdrojových kódů &#45; migrovat](../debugger/media/ffr-openprojectfromsourcecontrol-migrated.png "FFR_OpenProjectFromSourceControl_Migrated")  
  
####  <a name="WhatWorkspace"></a> Otázka: co je pracovní prostor?  
 **Odpověď:** vaše [pracovní prostor ukládá kopie zdroje](http://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a) takže můžete vyvinout a otestovat samostatně před vrácení práce se změnami. Pokud ještě nemáte pracovní prostor, který je přímo namapován na nalezené řešení nebo projekt, pak vás sada Visual Studio vyzve k výběru dostupného pracovního prostoru nebo k vytvoření nového pracovního prostoru s názvem vašeho počítače jako výchozím názvem pracovního prostoru.  
  
####  <a name="UntrustedSymbols"></a> Otázka: Proč se zobrazí tato zpráva o nedůvěryhodných symbolech?  
 ![Ladit s cestou nedůvěryhodných symbolech? ](../debugger/media/ffr-ituntrustedsymbolpaths.png "FFR_ITUntrustedSymbolPaths")  
  
 **Odpověď:** tato zpráva se zobrazí, když cesta symbolů v souboru manifestu sestavení (\<*ProjectName*>. BuildInfo.config) není součástí seznamu důvěryhodných cest symbolů. Cestu můžete přidat do seznamu cest symbolů v možnostech ladicího programu.





