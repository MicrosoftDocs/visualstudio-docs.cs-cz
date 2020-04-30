---
title: Použití Microsoft Monitoring Agent | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: fd0a86b9-015d-408e-aa58-59a0a97826ac
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 490c10f072ba57f27410ecb1cdca681469692de5
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586712"
---
# <a name="using-the-microsoft-monitoring-agent"></a>Použití služby Microsoft Monitoring Agent
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio naleznete v tématu [using the Microsoft Monitoring Agent](/visualstudio/debugger/using-the-microsoft-monitoring-agent).

Můžete místně monitorovat webové aplikace ASP.NET hostované službou IIS a aplikace SharePoint 2010 nebo 2013 pro chyby, problémy s výkonem nebo jiné problémy pomocí **Microsoft Monitoring Agent**. Diagnostické události můžete uložit z agenta do souboru protokolu IntelliTrace (. iTrace). Pak můžete otevřít soubor protokolu v Visual Studio Enterprise (ale ne v edicích Professional nebo Community) a ladit problémy se všemi diagnostickými nástroji sady Visual Studio. Data diagnostických dat a metod IntelliTrace můžete také shromažďovat spuštěním agenta v režimu **trasování** . Microsoft Monitoring Agent lze integrovat s [Application Insights](/azure/azure-monitor/app/app-insights-overview) a [nástrojem System Center Operations Manager](https://technet.microsoft.com/library/hh205987.aspx). Microsoft Monitoring Agent při instalaci změní prostředí cílového systému.  
  
> [!NOTE]
> Data diagnostiky a metody IntelliTrace můžete také shromažďovat pro webové aplikace, SharePoint, WPF a aplikace Windows Form na vzdálených počítačích, aniž byste museli měnit cílové prostředí pomocí samostatného **kolektoru IntelliTrace**. Samostatný kolektor má vyšší dopad na výkon než spuštění Microsoft Monitoring Agent v režimu **monitorování** . Viz [Použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
 Pokud používáte System Center 2012, můžete pomocí Microsoft Monitoring Agent s Operations Manager získat výstrahy týkající se problémů a vytvořit Team Foundation Server pracovní položky s odkazy na uložené protokoly IntelliTrace. Pak můžete přiřadit tyto pracovní položky jiným uživatelům k dalšímu ladění. Viz [integrace Operations Manager s procesy vývoje](https://technet.microsoft.com/library/jj614609.aspx) a [monitorování pomocí Microsoft Monitoring Agent](https://technet.microsoft.com/library/dn465153.aspx).  
  
 Než začnete, ověřte, zda máte odpovídající zdroj a symboly pro sestavený a nasazený kód. To vám pomůže přejít přímo k kódu aplikace při spuštění ladění a procházení diagnostických událostí v protokolu IntelliTrace. [Nastavte sestavení](../debugger/diagnose-problems-after-deployment.md) tak, aby sada Visual Studio automaticky nalezla a otevřela odpovídající zdroj pro váš nasazený kód.  
  
1. [Krok 1: nastavení Microsoft Monitoring Agent](#SetUpMonitoring)  
  
2. [Krok 2: zahájení monitorování aplikace](#MonitorEvents)  
  
3. [Krok 3: uložení zaznamenaných událostí](#SaveEvents)  
  
## <a name="step-1-set-up-microsoft-monitoring-agent"></a><a name="SetUpMonitoring"></a>Krok 1: nastavení Microsoft Monitoring Agent  
 Nastavte samostatného agenta na webovém serveru, aby se provádělo místní monitorování beze změny aplikace. Pokud používáte System Center 2012, přečtěte si téma [instalace Microsoft Monitoring Agent](https://technet.microsoft.com/library/dn465156.aspx).  
  
### <a name="set-up-the-standalone-agent"></a><a name="SetUpStandaloneMMA"></a>Nastavení samostatného agenta  
  
1. Ujistěte se, že:  
  
    - Webový server používá [podporované verze Internetová informační služba (IIS)](https://technet.microsoft.com/library/dn465154.aspx).  
  
    - Váš webový server má .NET Framework 3,5, 4 nebo 4,5.  
  
    - Na vašem webovém serveru běží Windows PowerShell 3,0 nebo novější. [Otázka: Co když mám prostředí Windows PowerShell 2,0?](#PowerShell2)  
  
    - Máte oprávnění správce na vašem webovém serveru, aby bylo možné spouštět příkazy prostředí PowerShell a recyklovat fond aplikací při spuštění monitorování.  
  
    - Odinstalovali jste všechny dřívější verze Microsoft Monitoring Agent.  
  
2. [Stáhněte si bezplatný Microsoft Monitoring Agent](https://go.microsoft.com/fwlink/?LinkID=309771), buď 32 **. exe** , nebo 64 verze **MMASetup-AMD64. exe**, z webu Microsoft Download Center na váš webový server.  
  
3. Spusťte stažený spustitelný soubor a spusťte tak Průvodce instalací nástroje.  
  
4. Na webovém serveru vytvořte zabezpečený adresář pro ukládání protokolů IntelliTrace, například **C:\IntelliTraceLogs**.  
  
     Než začnete s monitorováním, nezapomeňte vytvořit tento adresář. Abyste se vyhnuli zpomalení vaší aplikace, vyberte umístění na místním vysokorychlostním disku, který není příliš aktivní.  
  
    > [!IMPORTANT]
    > Protokoly IntelliTrace můžou obsahovat osobní a citlivá data. Omezí tento adresář jenom na identity, které musí v souborech fungovat. Podívejte se na zásady ochrany osobních údajů vaší společnosti.  
  
5. Chcete-li spustit podrobné monitorování na úrovni funkcí nebo monitorovat aplikace služby SharePoint, udělte fondu aplikací, který je hostitelem vaší webové aplikace nebo oprávnění ke čtení a zápisu aplikace služby SharePoint, do adresáře protokolu IntelliTrace. [Otázka: Návody nastavit oprávnění pro fond aplikací?](#FullPermissionsITLog)  
  
### <a name="q--a"></a>Otázky a odpovědi  
  
#### <a name="q-what-if-i-have-windows-powershell-20"></a><a name="PowerShell2"></a>Otázka: Co když mám prostředí Windows PowerShell 2,0?  
 **A:** Důrazně doporučujeme, abyste používali PowerShell 3,0. V opačném případě budete muset importovat rutiny Microsoft Monitoring Agent PowerShellu při každém spuštění prostředí PowerShell. Nemáte také přístup k obsahu s nápovědě ke stažení.  
  
1. Otevřete **prostředí Windows PowerShell** nebo **Integrované skriptovací prostředí (ISE) v prostředí Windows PowerShell** okno příkazového řádku jako správce.  
  
2. Importujte modul Microsoft Monitoring Agent PowerShell z výchozího umístění instalace:  
  
     **PS C: >Import-Module "C:\Program Files\Microsoft monitoring Agent\Agent\PowerShell\Microsoft.MonitoringAgent.PowerShell\Microsoft.MonitoringAgent.PowerShell.dll"**  
  
3. Nejnovější obsah obsahu můžete získat na [webu TechNet](https://technet.microsoft.com/systemcenter/default) .  
  
#### <a name="q-how-do-i-set-up-permissions-for-the-application-pool"></a><a name="FullPermissionsITLog"></a>Otázka: Návody nastavit oprávnění pro fond aplikací?  
 **A:** Použijte příkaz Windows **Icacls** nebo použijte Průzkumníka Windows (nebo Průzkumníka souborů). Příklad:  
  
- Nastavení oprávnění pomocí příkazu Windows **Icacls** :  
  
  - Pro webovou aplikaci ve fondu aplikací **DefaultAppPool** :  
  
     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\DefaultAppPool":RX`  
  
  - Pro aplikaci SharePoint ve fondu aplikací **SharePoint-80** :  
  
     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\SharePoint - 80":RX`  
  
    -nebo-  
  
- Nastavení oprávnění pomocí Průzkumníka Windows (nebo Průzkumníka souborů):  
  
  1. Otevřete **vlastnosti** adresáře protokolu IntelliTrace.  
  
  2. Na kartě **zabezpečení** vyberte možnost **Upravit**, **Přidat**.  
  
  3. Zajistěte, aby se v poli **Vybrat typ objektu** zobrazily **předdefinované objekty zabezpečení** . Pokud tam není, vyberte **typy objektů** , které chcete přidat.  
  
  4. Ujistěte se, že se Váš místní počítač zobrazuje v poli **z tohoto umístění** . Pokud tam není, vyberte **umístění** a změňte je.  
  
  5. Do pole **Zadejte názvy objektů k výběru** přidejte fond aplikací pro webovou aplikaci nebo aplikaci služby SharePoint.  
  
  6. Pro překlad názvu vyberte možnost **kontrolovat názvy** . Vyberte **OK**.  
  
  7. Ujistěte se, že fond aplikací má oprávnění **ke čtení & spouštění** .  
  
## <a name="step-2-start-monitoring-your-app"></a><a name="MonitorEvents"></a>Krok 2: zahájení monitorování aplikace  
 Pomocí příkazu Windows PowerShell [Start-WebApplicationMonitoring](https://technet.microsoft.com/library/dn472749(v=sc.20).aspx) můžete začít monitorovat svoji aplikaci. Pokud používáte System Center 2012, přečtěte si téma [monitorování webových aplikací pomocí Microsoft Monitoring Agent](https://technet.microsoft.com/library/dn465157.aspx).  
  
1. Na webovém serveru otevřete **Windows PowerShell** nebo **Integrované skriptovací prostředí (ISE) v prostředí Windows PowerShell** okno příkazového řádku jako správce.  
  
     ![Otevřete Windows PowerShell jako správce.](../debugger/media/ffr-powershellrunadmin.png "FFR_PowerShellRunAdmin")  
  
2. Spusťte příkaz [Start-WebApplicationMonitoring](https://technet.microsoft.com/library/dn472749(v=sc.20).aspx) , abyste mohli začít monitorovat vaši aplikaci. Tato akce restartuje všechny webové aplikace na webovém serveru.  
  
     Tady je krátká syntaxe:  
  
     **Start-WebApplicationMonitoring** *"\<AppName>"* * \<monitoringMode>* *"\<outputPath>"* * \<UInt32>* *"\<collectionPlanPathAndFileName>"*  
  
     Tady je příklad, který používá pouze název webové aplikace a režim zjednodušeného **monitorování** :  
  
     **PS C: >Start-WebApplicationMonitoring "FabrikamFabrikamFiber. Web" monitor "C:IntelliTraceLogs"**  
  
     Tady je příklad, který používá cestu služby IIS a režim zjednodušeného **monitorování** :  
  
     **PS C: >Start-WebApplicationMonitoring "IIS: sitesFabrikamFabrikamFiber. Web" monitor "C:IntelliTraceLogs"**  
  
     Až začnete s monitorováním, může se při restartu aplikace zobrazit Microsoft Monitoring Agent pozastavení.  
  
     ![Spustit monitorování s potvrzením MMA](../debugger/media/ffr-powershellstartmonitoringconfirmation.png "FFR_PowerShellStartMonitoringConfirmation")  
  
    |||  
    |-|-|  
    |*"\<AppName>"*|Zadejte cestu k webovému serveru a názvu webové aplikace ve službě IIS. Pokud budete chtít, můžete také zahrnout cestu služby IIS.<br /><br /> *"\<IISWebsiteName>\\<IISWebAppName\>"*<br /><br /> -nebo-<br /><br /> **"IIS: \ sites** * \\<\> \\ IISWebsiteName<\>IISWebAppName"*<br /><br /> Tuto cestu najdete ve Správci služby IIS. Příklad:<br /><br /> ![Cesta k webu služby IIS a webové aplikaci](../debugger/media/ffr-iismanager.png "FFR_IISManager")<br /><br /> Můžete také použít příkazy [Get-web](https://technet.microsoft.com/library/ee807832.aspx) a [získat webové aplikace](https://technet.microsoft.com/library/ee790554.aspx) .|  
    |*\<monitoringMode>*|Zadejte režim monitorování:<br /><br /> <ul><li>**Monitorování**: zaznamenejte minimální podrobnosti o událostech výjimek a událostech souvisejících s výkonem. Tento režim používá výchozí plán shromažďování dat.</li><li>**Trasování**: zaznamená podrobnosti na úrovni funkce nebo monitoruje aplikace SharePoint 2010 a sharepointu 2013 pomocí zadaného plánu shromažďování dat. V tomto režimu může být aplikace spuštěná pomaleji.<br /><br /> <ul><li>[Otázka: Návody nastavit oprávnění pro fond aplikací?](#FullPermissionsITLog)</li><li>[Otázka: Návody získat většinu dat bez zpomalení aplikace?](#Minimizing)</li></ul><br />     Tento příklad zaznamenává události pro aplikaci služby SharePoint hostované na webu služby SharePoint:<br /><br />     **Start-WebApplicationMonitoring "FabrikamSharePointSite\FabrikamSharePointApp" trasování "C:\Program Files\Microsoft monitoring Agent\Agent\IntelliTraceCollector\ collection_plan. ASP. NET. default. XML" "C:\IntelliTraceLogs"**</li><li>**Vlastní**: Zaznamenejte si vlastní podrobnosti pomocí zadaného plánu vlastní kolekce. Pokud upravíte plán shromažďování po spuštění monitorování, bude nutné restartovat monitorování.</li></ul>|  
    |*"\<outputPath>"*|Zadejte úplnou cestu k adresáři, kam se mají ukládat protokoly IntelliTrace. Než začnete s monitorováním, nezapomeňte vytvořit tento adresář.|  
    |*\<>UInt32*|Zadejte maximální velikost protokolu IntelliTrace. Výchozí maximální velikost protokolu IntelliTrace je 250 MB.<br /><br /> Když protokol dosáhne tohoto limitu, Agent přepíše nejstarší položky, aby bylo možné místo pro další položky. Pokud chcete tento limit změnit, použijte možnost **-MaximumFileSizeInMegabytes** nebo upravte `MaximumLogFileSize` atribut v plánu shromažďování dat.|  
    |*"\<collectionPlanPathAndFileName>"*|Zadejte úplnou cestu nebo relativní cestu a název souboru plánu kolekce. Tento plán je soubor. XML, který konfiguruje nastavení pro agenta.<br /><br /> Tyto plány jsou součástí agenta a pracují s webovými aplikacemi a aplikacemi SharePoint:<br /><br /> -   **collection_plan. ASP. NET. default. XML**<br />     Shromažďuje pouze události, jako jsou výjimky, události výkonu, volání databáze a požadavky webového serveru.<br />-   **collection_plan. ASP. NET. Trace. XML**<br />     Shromažďuje volání na úrovni funkcí a všechna data ve výchozím plánu shromažďování dat. Tento plán je vhodný pro podrobnou analýzu, ale může zpomalit vaši aplikaci.<br /><br /> Lokalizované verze těchto plánů můžete najít v podsložkách agenta. Můžete také [přizpůsobit tyto plány nebo vytvořit vlastní plány](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) , abyste se vyhnuli zpomalení aplikace. Jakékoli vlastní plány umístěte do stejného zabezpečeného umístění jako agenta.<br /><br /> [Otázka: Návody získat většinu dat bez zpomalení aplikace?](#Minimizing)|  
  
     Další informace o úplné syntaxi a dalších příkladech získáte spuštěním příkazu **Get-Help Start-WebApplicationMonitoring – detailed** a příkazu **Get-Help Start-WebApplicationMonitoring-Examples** .  
  
3. Pokud chcete zjistit stav všech monitorovaných webových aplikací, spusťte příkaz [Get-WebApplicationMonitoringStatus](https://technet.microsoft.com/library/dn472751(v=sc.20).aspx) .  
  
### <a name="q--a"></a>Otázky a odpovědi  
  
#### <a name="q-how-do-i-get-the-most-data-without-slowing-down-my-app"></a><a name="Minimizing"></a>Otázka: Návody získat většinu dat bez zpomalení aplikace?  
 **A:** Microsoft Monitoring Agent může shromažďovat spoustu dat a ovlivnit výkon vaší aplikace v závislosti na datech, která jste si zvolili ke shromáždění, a jak je shromažďovat. Tady je několik způsobů, jak získat většinu dat bez zpomalení aplikace:  
  
- U webových aplikací a aplikací služby SharePoint Agent zaznamenává data pro každou aplikaci, která sdílí určený fond aplikací. To může zpomalit jakoukoliv aplikaci, která sdílí stejný fond aplikací, a to i v případě, že kolekci můžete omezit na moduly pro jednu aplikaci. Chcete-li zabránit zpomalování ostatních aplikací, hostovat každou aplikaci ve vlastním fondu aplikací.  
  
- Zkontrolujte události, pro které Agent shromažďuje data v plánu shromažďování dat. Upravte plán shromažďování dat, abyste zakázali události, které nejsou důležité nebo vás zajímají. To může zlepšit výkon při spuštění a běhový výkon.  
  
   Chcete-li zakázat událost, nastavte `enabled` atribut `<DiagnosticEventSpecification>` elementu na `false`:  
  
   `<DiagnosticEventSpecification enabled="false">`  
  
   Pokud `enabled` atribut neexistuje, událost je povolena.  
  
   Příklad:  
  
  - Zakáže události Windows workflowu pro aplikace, které nepoužívají pracovní postup Windows.  
  
  - Zakažte události registru pro aplikace, které přistupují k registru, ale nezobrazují problémy s nastavením registru.  
  
- Zkontrolujte moduly, pro které Agent shromažďuje data v plánu shromažďování dat. Upravte plán shromažďování dat tak, aby obsahoval pouze ty moduly, které vás zajímají.  
  
   Tím se sníží množství informací o volání metody a další data instrumentace, která agent shromažďuje při spuštění a spuštění aplikace. Tato data vám pomůžou krokovat kód při ladění a kontrole hodnot předaných do a vrácených z volání funkce.  
  
  1. Otevřete plán kolekce. Vyhledejte `<ModuleList>` element.  
  
  2. V `<ModuleList>`, nastavte `isExclusionList` atribut na `false`.  
  
  3. Pomocí `<Name>` elementu zadejte každý modul s jedním z následujících způsobů: název souboru, Řetězcová hodnota pro zahrnutí jakéhokoli modulu, jehož název obsahuje tento řetězec nebo veřejný klíč.  
  
     Tento příklad vytvoří seznam, který shromažďuje data pouze z hlavního modulu webové aplikace Fabrikam Fiber:  
  
  ```xml  
  <ModuleList isExclusionList="false">  
     <Name>FabrikamFiber.Web.dll</Name>  
  </ModuleList>  
  
  ```  
  
   Chcete-li shromažďovat data z jakéhokoli modulu, jehož název obsahuje "fabrikam", vytvořte seznam jako takový:  
  
  ```xml  
  <ModuleList isExclusionList="false">  
     <Name>Fabrikam</Name>  
  </ModuleList>  
  
  ```  
  
   Chcete-li shromažďovat data z modulů zadáním jejich tokenů veřejných klíčů, vytvořte seznam, jako je tento:  
  
  ```xml  
  <ModuleList isExclusionList="false">  
     <Name>PublicKeyToken:B77A5C561934E089</Name>  
     <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>  
     <Name>PublicKeyToken:31BF3856AD364E35</Name>  
     <Name>PublicKeyToken:89845DCD8080CC91</Name>  
     <Name>PublicKeyToken:71E9BCE111E9429C</Name>  
  </ModuleList>  
  
  ```  
  
   **Otázka: Proč místo toho nejenom vyloučit moduly?**  
  
   **A:** Ve výchozím nastavení plány shromažďování dat vyloučí moduly nastavením `isExclusionList` atributu na `true`. To však může stále shromažďovat data z modulů, které nesplňují kritéria seznamu nebo které vás nemusejí zajímat, například moduly třetích stran nebo open source.  
  
#### <a name="q-what-values-does-the-agent-collect"></a>Otázka: jaké hodnoty shromažďuje Agent?  
 **A:** Aby se snížil dopad na výkon, agent shromáždí jenom tyto hodnoty:  
  
- Primitivní datové typy, které se předávají a vracejí z metod  
  
- Primitivní datové typy v polích pro objekty nejvyšší úrovně předávané a vrácené z metod  
  
  Předpokládejme například, že máte signaturu `AlterEmployee` metody, která přijímá celé číslo `id` a `Employee` objekt `oldemployee`:  
  
  `public Employee AlterEmployee(int id, Employee oldemployee)`  
  
  `Employee` Typ má následující atributy: `Id`, `Name`a `HomeAddress`. Mezi `Employee` a `Address` typem existuje vztah přidružení.  
  
  ![Vztah mezi zaměstnancem a adresou](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")  
  
  Agent `id`zaznamenává hodnoty pro, `Employee.Id` `Employee.Name` a `Employee` objekt vrácený z `AlterEmployee` metody. Agent však nezaznamená informace o objektu, který `Address` je jiný než bez ohledu na to, zda byl null nebo ne. Agent také nezaznamenává data týkající se místních proměnných v metodě `AlterEmployee` , pokud jiné metody tyto místní proměnné nepoužívají jako parametry, které ukazují, že jsou zaznamenávány jako parametry metody.  
  
## <a name="step-3-save-recorded-events"></a><a name="SaveEvents"></a>Krok 3: uložení zaznamenaných událostí  
 Když najdete chybu nebo problém s výkonem, uložte zaznamenané události do protokolu IntelliTrace. Agent vytvoří protokol pouze v případě, že zaznamenal události. Pokud používáte System Center 2012, přečtěte si téma [monitorování webových aplikací pomocí Microsoft Monitoring Agent](https://technet.microsoft.com/library/dn465157.aspx).  
  
### <a name="save-recorded-events-but-continue-monitoring"></a>Uložte zaznamenané události, ale pokračujte v monitorování.  
 Pokud chcete vytvořit protokol IntelliTrace, ale nechcete aplikaci restartovat, ale nechcete, aby se monitorování zastavilo, postupujte podle těchto kroků. Agent pokračuje v monitorování i v případě, že dojde k restartování serveru nebo aplikace.  
  
1. Na webovém serveru otevřete okno příkazového řádku Windows PowerShellu jako správce.  
  
2. Spuštěním příkazu [Checkpoint-WebApplicationMonitoring](https://technet.microsoft.com/library/dn472750(v=sc.20).aspx) uložte snímek protokolu IntelliTrace:  
  
    **Checkpoint-WebApplicationMonitoring** *"\<IISWebsiteName>\\<IISWebAppName\>"*  
  
    \-ani  
  
    **Checkpoint-WebApplicationMonitoring "IIS: \ sites** * \\<\> \\ IISWebsiteName<\>IISWebAppName"*  
  
    Příklad:  
  
    **PS C:\\>Checkpoint-WebApplicationMonitoring "Fabrikam\FabrikamFiber.Web"**  
  
    -nebo-  
  
    **PS C: >Checkpoint-WebApplicationMonitoring "IIS: sitesFabrikamFabrikamFiber. Web"**  
  
    Další informace získáte spuštěním příkazu **Get-Help Checkpoint-WebApplicationMonitoring – detailed** a příkazu **Get-Help Checkpoint-WebApplicationMonitoring-Examples** .  
  
3. Zkopírujte protokol do zabezpečené sdílené složky a pak otevřete protokol z počítače, který má Visual Studio Enterprise (ale ne edice Professional nebo Community).  
  
   > [!IMPORTANT]
   > Buďte opatrní při sdílení protokolů IntelliTrace, protože by mohly obsahovat osobní a citlivá data. Ujistěte se, že kdokoli má přístup k těmto protokolům, má oprávnění zobrazit tato data. Podívejte se na zásady ochrany osobních údajů vaší společnosti.  
  
   **Další:** [Diagnostika zaznamenaných událostí v Visual Studio Enterprise](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)  
  
### <a name="save-recorded-events-and-stop-monitoring"></a>Uložit zaznamenané události a zastavit monitorování  
 Pokud chcete získat diagnostické informace jenom při reprodukci konkrétního problému, postupujte podle těchto kroků. Tato akce restartuje všechny webové aplikace na webovém serveru.  
  
1. Na webovém serveru otevřete okno příkazového řádku Windows PowerShellu jako správce.  
  
2. Spuštěním příkazu [Stop-WebApplicationMonitoring](https://technet.microsoft.com/library/dn472753(v=sc.20).aspx) vytvořte protokol IntelliTrace a zastavte monitorování konkrétní webové aplikace:  
  
    **Stop-WebApplicationMonitoring** *"\<IISWebsiteName>\\<IISWebAppName\>"*  
  
    \-ani  
  
    **Stop-WebApplicationMonitoring "IIS: \ sites** * \\<\> \\ IISWebsiteName<\>IISWebAppName"*  
  
    Nebo pokud chcete zastavit monitorování všech webových aplikací:  
  
    **Stop-WebApplicationMonitoring – vše**  
  
    Příklad:  
  
    **PS C:\\>Stop-WebApplicationMonitoring "Fabrikam\iFabrikamFiber.Web"**  
  
    \-ani  
  
    **PS C:\\>stop-WEBAPPLICATIONMONITORING "IIS: \ sites\Fabrikam\FabrikamFiber.Web"**  
  
    Další informace získáte spuštěním příkazu **Get-Help Stop-WebApplicationMonitoring – detailed** a příkazu **Get-Help Stop-WebApplicationMonitoring-Examples** .  
  
3. Zkopírujte protokol do zabezpečené sdílené složky a pak otevřete protokol z počítače, ve kterém je Visual Studio Enterprise.  
  
   **Další:** [Diagnostika zaznamenaných událostí v Visual Studio Enterprise](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)  
  
## <a name="q--a"></a>Otázky a odpovědi  
  
### <a name="q-where-can-i-get-more-information"></a>Otázka: kde mohu získat další informace?  
  
#### <a name="blogs"></a>Blogy  
 [Představujeme Microsoft Monitoring Agent](https://devblogs.microsoft.com/devops/introducing-microsoft-monitoring-agent-2/)  
  
 [Optimalizace kolekce IntelliTrace na produkčních serverech](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)  
  
#### <a name="forums"></a>Fóra  
 [Diagnostika sady Visual Studio](https://social.msdn.microsoft.com/Forums/vsdebug)
