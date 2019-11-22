---
title: Diagnostikujte problémy po nasazení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a3463eab-a352-4d17-8551-adbaad526db0
caps.latest.revision: 66
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 41b24cf97ef0768ee700841aa859698cd2307710
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298293"
---
# <a name="diagnose-problems-after-deployment"></a>Diagnostika problémů po nasazení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li diagnostikovat problémy ve webové aplikaci ASP.NET po nasazení pomocí IntelliTrace, zahrňte do své verze informace o sestavení, aby aplikace Visual Studio automaticky nalezla správné zdrojové soubory a soubory symbolů, které jsou požadovány pro ladění protokolu IntelliTrace.  
  
 Pokud používáte Microsoft Monitoring Agent k řízení IntelliTrace, musíte také na svém webovém serveru nastavit sledování výkonu aplikace. Tato akce zaznamenává diagnostické události při spuštění aplikace a ukládá je do souboru protokolu IntelliTrace. Pak se můžete podívat na události v Visual Studio Enterprise (ale ne na edice Professional nebo Community), přejít na kód, ve kterém došlo k události, prohlédnout zaznamenané hodnoty v daném časovém okamžiku a přejít vpřed nebo zpět prostřednictvím kódu, který byl spuštěn. Po vyhledání a vyřešení problému opakujte cyklus pro sestavení, vydání a monitorování vaší verze, abyste mohli vyřešit budoucí potenciální problémy dříve a rychleji.  
  
 ![Kód, sestavení, vydání, monitorování, diagnostika, oprava](../debugger/media/ffr-cycle.png "FFR_Cycle")  
  
 **Budete potřebovat:**  
  
- Sada Visual Studio 2015 nebo Team Foundation Server 2015, 2013, 2012 nebo 2010 pro nastavení sestavení  
  
- Microsoft Monitoring Agent k monitorování aplikace a záznamu diagnostických dat  
  
- Visual Studio Enterprise (ale ne edice Professional nebo Community) ke kontrole diagnostických dat a ladění kódu pomocí IntelliTrace  
  
## <a name="SetUpBuild"></a>Krok 1: zahrnutí informací o sestavení do vaší vydané verze  
 Nastavte proces sestavení tak, aby vytvořil manifest sestavení (soubor BuildInfo. config) pro váš webový projekt a zahrnul tento manifest do vaší vydané verze. Tento manifest obsahuje informace o projektu, správě zdrojového kódu a systému sestavení, které byly použity k vytvoření konkrétního sestavení. Tyto informace pomáhají aplikaci Visual Studio najít vyhovující zdroj a symboly po otevření protokolu IntelliTrace ke kontrole zaznamenaných událostí.  
  
### <a name="AutomatedBuild"></a>Vytvoření manifestu sestavení pro automatizované sestavení pomocí Team Foundation Server  
 Použijte tyto kroky, pokud používáte Správa verzí Team Foundation nebo Git.  
  
#### <a name="TFS2013"></a> Team Foundation Server 2013  
 Nastavte definici sestavení pro přidání umístění zdroje, sestavení a symbolů do manifestu sestavení (soubor BuildInfo. config). Sestavení Team Foundation Build automaticky vytvoří tento soubor a umístí ho do výstupní složky vašeho projektu.  
  
1. [Upravte definici sestavení nebo vytvořte novou definici sestavení.](https://msdn.microsoft.com/library/1c2eca2d-9a65-477e-9b23-0678ff7882ee)  
  
    ![Zobrazit definici sestavení v TFS 2013](../debugger/media/ffr-tfs2013viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")  
  
2. Zvolte výchozí šablonu (TfvcTemplate.12.xaml) nebo vlastní šablonu.  
  
    ![Vyberte sestavení Šablona &#45; procesu TFS 2013](../debugger/media/ffr-tfs2013buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")  
  
3. Určete, kam se má uložit soubor symbolů (PDB), aby byl zdroj indexován automaticky.  
  
    Pokud používáte vlastní šablonu, ujistěte se, že šablona má aktivitu pro indexování zdroje. Později přidáte argument MSBuild, který určí, kam se mají ukládat soubory symbolů.  
  
    ![Nastavení cesty symbolů v definici sestavení TFS 2013](../debugger/media/ffr-tfs2013builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")  
  
    Další informace o symbolech naleznete v tématu [Publish data Symbols](https://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6).  
  
4. Přidejte tento argument MSBuild pro zahrnutí serveru TFS a umístění symbolů do souboru manifestu sestavení:  
  
    **/p:IncludeServerNameInBuildInfo=True**  
  
    Kdokoli, kdo má přístup k vašemu webovému serveru, uvidí tato umístění v manifestu sestavení. Ujistěte se, že je váš zdrojový server zabezpečený.  
  
5. Pokud používáte vlastní šablonu, přidejte tento argument nástroje MSBuild a určete, kam se má uložit soubor symbolů:  
  
    **/p: BuildSymbolStorePath =** \<*cesta ke symbolům*>  
  
    ![Zahrnout informace o sestavení serveru v sadě TFS def Build 2013](../debugger/media/ffr-tfs2013builddefincludeserverinfo.png "FFR_TFS2013BuildDefIncludeServerInfo")  
  
    A přidejte tyto řádky do souboru webového projektu (.csproj, .vbproj):  
  
   ```  
   <!-- Import the targets file. Change the folder location as necessary. -->  
      <Import Project=""$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\BuildInfo\Microsoft.VisualStudio.ReleaseManagement.BuildInfo.targets" />  
  
   ```  
  
6. Spusťte nové sestavení.  
  
   **Krok 2:** [Krok 2: vydání aplikace](#DeployRelease)  
  
#### <a name="TFS2012_2010"></a>Team Foundation Server 2012 nebo 2010  
 Použijte následující postup, chcete-li automaticky vytvořit manifest sestavení (soubor BuildInfo. config) pro váš projekt a umístit jej do výstupní složky vašeho projektu. Soubor se zobrazí jako*ProjectName*. BuildInfo. config "ve složce výstupu, ale po publikování aplikace je přejmenována" BuildInfo. config "ve složce pro nasazení.  
  
1. Na server Team Foundation Build nainstalujte Visual Studio 2013 (libovolná edice).  
  
2. V rámci definice sestavení zadejte umístění pro ukládání symbolů tak, aby byl zdroj automaticky indexován.  
  
    Pokud používáte vlastní šablonu, ujistěte se, že šablona má aktivitu pro indexování zdroje.  
  
3. Do definice sestavení přidejte následující argumenty nástroje MSBuild:  
  
   - **/p:VisualStudioVersion=12.0**  
  
   - **/p:MSBuildAssemblyVersion=12.0**  
  
   - **/tv:12.0**  
  
   - **/p:IncludeServerNameInBuildInfo=True**  
  
   - **/p: BuildSymbolStorePath =** \<*cesta ke symbolům*>  
  
4. Spusťte nové sestavení.  
  
   **Krok 2:** [Krok 2: vydání aplikace](#DeployRelease)  
  
### <a name="ManualBuild"></a>Vytvoření manifestu sestavení pro ruční sestavení pomocí sady Visual Studio  
 Použijte následující postup, chcete-li automaticky vytvořit manifest sestavení (soubor BuildInfo. config) pro váš projekt a umístit jej do výstupní složky vašeho projektu. Soubor se zobrazí jako*ProjectName*. BuildInfo. config "ve složce výstupu, ale po publikování aplikace je přejmenována" BuildInfo. config "ve složce pro nasazení.  
  
1. V **Průzkumník řešení**uvolněte webový projekt.  
  
2. Otevřete soubor projektu (. csproj,. vbproj). Přidejte tyto řádky:  
  
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
  
   **Krok 2:** [Krok 2: vydání aplikace](#DeployRelease)  
  
### <a name="MSBuild"></a>Vytvoření manifestu sestavení pro ruční sestavení pomocí nástroje MSBuild. exe  
 Přidejte tyto argumenty sestavení při spuštění sestavení:  
  
 **/p:GenerateBuildInfoConfigFile=True**  
  
 **/p:IncludeServerNameInBuildInfo=True**  
  
 **/p: BuildSymbolStorePath =** \<*cesta ke symbolům*>  
  
## <a name="DeployRelease"></a>Krok 2: vydání vaší aplikace  
 Použijete-li [balíček Web. deploy](https://msdn.microsoft.com/library/dd394698.aspx) , který byl vytvořen procesem sestavení pro nasazení aplikace, je manifest sestavení automaticky přejmenován z "*ProjectName*". BuildInfo. config "na" BuildInfo. config "a je umístěn ve stejné složce se souborem Web. config vaší aplikace na vašem webovém serveru.  
  
 Použijete-li k nasazení aplikace jiné metody, ujistěte se, že je manifest sestavení přejmenován z "*ProjectName*". BuildInfo. config "na" BuildInfo. config "a umístí se do stejné složky se souborem Web. config vaší aplikace na webovém serveru.  
  
## <a name="step-3-monitor-your-app"></a>Krok 3: Sledování vaší aplikace  
 Nastavte na webovém serveru sledování výkonu aplikací, abyste mohli monitorovat problémy, zaznamenávat diagnostické události a ukládat tyto události do souboru protokolu IntelliTrace. [Problémy s nasazením](../debugger/using-the-intellitrace-stand-alone-collector.md)najdete v tématu monitorování vydání.  
  
## <a name="InvestigateEvents"></a>Krok 4: Vyhledání problému  
 Chcete-li zkontrolovat zaznamenané události a ladit kód pomocí IntelliTrace, budete potřebovat Visual Studio Enterprise na svém vývojovém počítači nebo jiném počítači. Můžete také použít nástroje jako CodeLens, mapy ladicího programu a mapy kódu, které vám pomůžou problém diagnostikovat.  
  
### <a name="open-the-intellitrace-log-and-matching-solution"></a>Otevření protokolu nástroje IntelliTrace a odpovídajícího řešení  
  
1. Z Visual Studio Enterprise otevřete protokol IntelliTrace (soubor. iTrace). Nebo stačí dvakrát kliknout na soubor, pokud jste Visual Studio Enterprise ve stejném počítači.  
  
2. Vyberte možnost **Otevřít řešení** , pokud chcete, aby aplikace Visual Studio automaticky otevřela vyhovující řešení nebo projekt, pokud projekt nebyl sestaven jako součást řešení. [Otázka: v protokolu IntelliTrace chybí informace o naší nasazené aplikaci. Proč k tomu došlo? Co mám dělat?](#InvalidConfigFile)  
  
     Visual Studio automaticky přiloží všechny nedokončené změny při otevření odpovídajícího řešení nebo projektu. Chcete-li získat další podrobnosti o této sadě odložených změn, podívejte se do okna **výstup** nebo **Team Explorer**.  
  
     Než provedete změny, ověřte, že máte správný zdroj. Pokud používáte větvení, možná pracujete v jiné větvi, než aplikace Visual Studio najde shodný zdroj, jako je vaše větev vydání.  
  
     ![Otevřít řešení z protokolu IntelliTrace](../debugger/media/ffr-itsummarypageopensolution.png "FFR_ITSummaryPageOpenSolution")  
  
     Pokud máte existující pracovní prostor mapovaný na toto řešení nebo projekt, Visual Studio vybere tento pracovní prostor k vložení nalezeného zdroje.  
  
     ![Otevřít ze správy zdrojového kódu do mapovaného pracovního prostoru](../debugger/media/ffr-openprojectfromsourcecontrol-mapped.png "FFR_OpenProjectFromSourceControl_Mapped")  
  
     V opačném případě zvolte jiný pracovní prostor nebo vytvořte nový pracovní prostor. Sada Visual Studio bude mapovat celou větev na tento pracovní prostor.  
  
     ![Otevřít ze správy zdrojových &#45; kódů vytvořit nový pracovní prostor](../debugger/media/ffr-openprojectfromsourcecontrol-createnewworkspace.png "FFR_OpenProjectFromSourceControl_CreateNewWorkspace")  
  
     Chcete-li vytvořit pracovní prostor s konkrétními mapováními nebo názvem, který není názvem vašeho počítače, vyberte možnost **Spravovat**.  
  
     [Otázka: Proč Visual Studio říká, že můj vybraný pracovní prostor je nezpůsobilý?](#IneligibleWorkspace)  
  
     [Otázka: Proč nemůžu pokračovat, dokud nevyberu kolekci týmu nebo jinou kolekci?](#ChooseTeamProject)  
  
### <a name="diagnose-a-performance-problem"></a>Diagnostikování problému s výkonem  
  
1. V části **narušení výkonu**Zkontrolujte zaznamenané události výkonu, jejich celkové časy spuštění a další informace o událostech. Pak přejděte hlouběji do metod, které byly volány během konkrétní události výkonu.  
  
     ![Zobrazit podrobnosti události výkonu](../debugger/media/ffr-itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  
  
     Můžete také pouze dvakrát kliknout na událost.  
  
2. Na stránce události zkontrolujte časy spuštění těchto volání. Vyhledejte pomalé volání ve stromu spuštění.  
  
     Pokud máte více volání vnořených nebo jiných, zobrazují se nejpomalejší volání ve vlastním oddílu.  
  
     Rozbalte volání za účelem kontroly všech vnořených volání a hodnot, které byly zaznamenány v daném časovém okamžiku. Potom spusťte ladění z tohoto volání.  
  
     ![Spustit ladění z volání metody](../debugger/media/ffr-itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  
  
     Můžete také pouze dvakrát kliknout na volání.  
  
     Pokud je metoda v kódu aplikace, sada Visual Studio přejde na tuto metodu.  
  
     ![Přejít na kód aplikace z události výkonu](../debugger/media/ffr-itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  
  
     Nyní můžete zkontrolovat další zaznamenané hodnoty, zásobník volání, krokovat kód, nebo použít okno **IntelliTrace** pro [pohyb zpět nebo vpřed "v čase" mezi jinými metodami](../debugger/intellitrace.md) , které byly volány během této události výkonu. [Jaké jsou všechny ostatní události a informace v protokolu IntelliTrace?](../debugger/using-saved-intellitrace-data.md) [Co dalšího mohu udělat?](#WhatElse) [Chcete získat další informace o událostech souvisejících s výkonem?](https://devblogs.microsoft.com/devops/performance-details-in-intellitrace/)  
  
### <a name="diagnose-an-exception"></a>Diagnostikování výjimky  
  
1. V části **data výjimky**Zkontrolujte zaznamenané události výjimky, jejich typy, zprávy a případy, kdy došlo k výjimkám. Pokud se chcete dostat hlouběji do kódu, spusťte ladění od poslední události ve skupině výjimek.  
  
     ![Spustit ladění z události výjimky](../debugger/media/ffr-itsummarypageexception.png "FFR_ITSummaryPageException")  
  
     Můžete také pouze dvakrát kliknout na událost.  
  
     Pokud došlo k výjimce v kódu aplikace, sada Visual Studio pokračuje tam, kde došlo k výjimce.  
  
     ![Přejít na kód aplikace z události výjimky](../debugger/media/ffr-itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  
  
     Nyní můžete zkontrolovat další zaznamenané hodnoty, zásobník volání nebo použít okno **IntelliTrace** pro [pohyb zpět nebo vpřed "v čase" mezi ostatními zaznamenanými událostmi](../debugger/intellitrace.md), souvisejícím kódem a hodnotami zaznamenanými v těchto okamžicích v čase. [Jaké jsou všechny ostatní události a informace v protokolu IntelliTrace?](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="WhatElse"></a>Co dalšího mohu udělat?  
  
- [Získat další informace o tomto kódu](../ide/find-code-changes-and-other-history-with-codelens.md). Chcete-li najít odkazy na tento kód, jeho historii změn, související chyby, pracovní položky, revize kódu nebo testy jednotek – to vše bez nutnosti opustit editor – použijte indikátory CodeLens v editoru.  
  
     ![CodeLens &#45; zobrazit odkazy na tento kód](../debugger/media/ffr-itsummarypageperformancecodelensreferences.png "FFR_ITSummaryPagePerformanceCodeLensReferences")  
  
     ![CodeLens &#45; zobrazit historii změn pro tento kód](../debugger/media/ffr-itsummarypageperformancecodelensauthors.png "FFR_ITSummaryPagePerformanceCodeLensAuthors")  
  
- [Namapujte místo v kódu během ladění.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) Chcete-li vizuálně sledovat metody, které byly volány během relace ladění, namapujte zásobník volání.  
  
     ![Mapování zásobníku volání při ladění](../debugger/media/ffr-itsummarypageperformancedebuggermap.png "FFR_ITSummaryPagePerformanceDebuggerMap")  
  
### <a name="FAQ"></a> Q & A  
  
#### <a name="WhyInclude"></a>Otázka: Proč zahrnout informace o projektu, správě zdrojového kódu, sestavení a symbolech pomocí moje verze?  
 Visual Studio používá tyto informace k nalezení odpovídajícího řešení a zdroje pro vydanou verzi, kterou se pokoušíte ladit. Po otevření protokolu IntelliTrace a výběru události pro spuštění ladění používá Visual Studio symboly k vyhledání a zobrazení kódu, kde k události došlo. Pak se můžete podívat na hodnoty, které se zaznamenaly, a přesunout vpřed nebo zpět prostřednictvím provádění kódu.  
  
 Pokud používáte server TFS a tyto informace nejsou v manifest sestavení (BuildInfo. config), sada Visual Studio hledá na aktuálně připojeném serveru TFS shodný zdroj a symboly. Pokud sada Visual Studio nemůže najít správný server TFS nebo odpovídající zdroj, budete vyzváni k výběru jiného serveru TFS.  
  
#### <a name="InvalidConfigFile"></a>Otázka: v protokolu IntelliTrace chybí informace o naší nasazené aplikaci. Proč k tomu došlo? Co mám udělat?  
 K tomu může dojít při nasazení z vývojového počítače nebo když během nasazování nejste připojeni k serveru TFS.  
  
1. Přejít do složky pro nasazení vašeho projektu.  
  
2. Vyhledejte a otevřete manifest sestavení (soubor BuildInfo. config).  
  
3. Ujistěte se, že soubor obsahuje požadované informace:  
  
- **ProjectName**  
  
   Název projektu v aplikaci Visual Studio. Příklad:  
  
  ```  
  <ProjectName>FabrikamFiber.Extranet.Web</ProjectName>  
  ```  
  
- **SourceControl**  
  
- Informace o vašem systému správy zdrojů a těchto požadovaných vlastnostech:  
  
  - **TFS**  
  
    - **ProjectCollectionUri**: identifikátor URI pro váš Team Foundation Server a kolekci projektů  
  
    - **ProjectItemSpec**: cesta k souboru projektu vaší aplikace (. csproj nebo. vbproj)  
  
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
  
    - **GitSourceControl**: umístění schématu **GitSourceControl**  
  
    - **RepositoryUrl**: identifikátor URI pro váš Team Foundation Server, kolekci projektů a úložiště Git  
  
    - **ProjectPath**: cesta k souboru projektu vaší aplikace (. csproj nebo. vbproj)  
  
    - **CommitId**: ID pro potvrzení  
  
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
  
  - **BuildLabel** (pro TeamBuild): název a číslo sestavení. Tento popisek se používá také jako název události nasazení. Další informace o číslech sestavení naleznete v tématu [použití čísel sestavení k poskytnutí smysluplných názvů pro dokončená sestavení](https://msdn.microsoft.com/library/1f302e9d-4b0a-40b5-8009-b69ca6f988c3).  
  
  - **SymbolPath** (doporučeno): seznam identifikátorů URI pro umístění symbolů (soubor PDB) oddělený středníkem. Tyto identifikátory URI můžou být adresy URL nebo UNCs. Díky tomu může Visual Studio snadněji najít vyhovující symboly, které vám pomůžou s laděním.  
  
  - **BuildReportUrl** (pro TeamBuild): umístění sestavy sestavení v sadě TFS  
  
  - **BuildId** (pro TeamBuild): identifikátor URI pro podrobnosti o sestavení v TFS. Tento identifikátor URI se používá také jako ID události nasazení. Pokud nepoužíváte TeamBuild, musí být ID jedinečné.  
  
  - **BuiltSolution**: cesta k souboru řešení, který aplikace Visual Studio používá k vyhledání a otevření odpovídajícího řešení. Toto je obsah vlastnosti **SolutionPath** MSBuild.  
  
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
  
#### <a name="IneligibleWorkspace"></a>Otázka: Proč Visual Studio říká, že můj vybraný pracovní prostor je nezpůsobilý?  
 **A:** Vybraný pracovní prostor nemá žádná mapování mezi složkou správy zdrojového kódu a místní složkou. Chcete-li vytvořit mapování pro tento pracovní prostor, vyberte možnost **Spravovat**. V opačném případě zvolte již namapovaný pracovní prostor nebo vytvořte nový pracovní prostor.  
  
 ![Otevřít ze správy zdrojového kódu bez namapovaného pracovního prostoru](../debugger/media/ffr-openprojectfromsourcecontrol-notmapped.png "FFR_OpenProjectFromSourceControl_NotMapped")  
  
#### <a name="ChooseTeamProject"></a>Otázka: Proč nemůžu pokračovat, dokud nevyberu kolekci týmu nebo jinou kolekci?  
 **A:** K tomu může dojít z některého z těchto důvodů:  
  
- Sada Visual Studio není připojena k serveru TFS.  
  
     ![Otevřít ze správy &#45; zdrojového kódu Nepřipojeno](../debugger/media/ffr-openprojectfromsourcecontrol-notconnected.png "FFR_OpenProjectFromSourceControl_NotConnected")  
  
- Sada Visual Studio nenašla řešení nebo projekt v aktuální kolekci týmu.  
  
     Když soubor manifestu sestavení (\<*ProjectName*>. BuildInfo. config) neurčuje, kde aplikace Visual Studio najde požadovaný zdroj. Visual Studio používá aktuálně připojeného TFS k nalezení odpovídajícího řešení nebo projektu. Pokud nemá aktuální kolekce týmu odpovídající zdroj, vyzve vás sada Visual Studio k připojení k jiné kolekci týmu.  
  
- Sada Visual Studio nenalezla řešení nebo projekt v kolekci určené souborem manifestu sestavení (\<*ProjectName*>. BuildInfo. config).  
  
     Zadaný server TFS nemusí již mít odpovídající nebo dokonce existující zdroj. Možným důvodem je, že jste migrovali na nový server TFS. Pokud zadaný server TFS neexistuje, může přibližně po minutě vypršet časový limit sady Visual Studio a poté budete vyzváni k připojení do jiné kolekce. Chcete-li pokračovat, připojte se ke správnému serveru TFS.  
  
     ![Otevřít ze správy &#45; zdrojového kódu](../debugger/media/ffr-openprojectfromsourcecontrol-migrated.png "FFR_OpenProjectFromSourceControl_Migrated")  
  
#### <a name="WhatWorkspace"></a>Otázka: co je pracovní prostor?  
 **A:** [Pracovní prostor ukládá kopii zdroje](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a) , takže ho můžete vyvinout a otestovat samostatně ještě před vrácením práce se změnami. Pokud ještě nemáte pracovní prostor, který je přímo namapován na nalezené řešení nebo projekt, pak vás sada Visual Studio vyzve k výběru dostupného pracovního prostoru nebo k vytvoření nového pracovního prostoru s názvem vašeho počítače jako výchozím názvem pracovního prostoru.  
  
#### <a name="UntrustedSymbols"></a>Otázka: Proč se zobrazí tato zpráva o nedůvěryhodných symbolech?  
 ![Ladit s cestou k nedůvěryhodným symbolům?](../debugger/media/ffr-ituntrustedsymbolpaths.png "FFR_ITUntrustedSymbolPaths")  
  
 **A:** Tato zpráva se zobrazí, když cesta k symbolům v souboru manifestu sestavení (\<*ProjectName*>. BuildInfo. config) není zahrnut v seznamu důvěryhodných cest k symbolům. Cestu můžete přidat do seznamu cest symbolů v možnostech ladicího programu.
