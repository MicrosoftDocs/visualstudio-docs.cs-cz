---
title: Použití služby Microsoft Monitoring Agent | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: fd0a86b9-015d-408e-aa58-59a0a97826ac
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3146de7efb7db567149b7741f2868a932f8476ac
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842063"
---
# <a name="using-the-microsoft-monitoring-agent"></a>Použití služby Microsoft Monitoring Agent
Místně můžete monitorovat webové aplikace ASP.NET hostované službou IIS a službu SharePoint 2010 nebo 2013 aplikací pro chyby, problémy s výkonem nebo jiné problémy s použitím **agenta Microsoft Monitoring Agent**. Můžete uložit diagnostické události z agenta do souboru protokolu IntelliTrace (.iTrace). V protokolu pak můžete otevřít v sadě Visual Studio Enterprise (ale ne edice Professional nebo Community) pro ladění problémů s všechny diagnostické nástroje sady Visual Studio. Může také shromažďovat diagnostická data IntelliTrace a metoda dat spuštěním agenta v **trasování** režimu. Microsoft Monitoring Agent je možné integrovat s [Application Insights](/azure/application-insights/) a [System Center Operation Manageru](/previous-versions/system-center/system-center-2012-R2/hh205987(v=sc.12)). Agenta Microsoft Monitoring Agent změnit prostředí cílového systému, když je nainstalovaná.  
  
> [!NOTE]
>  Může také shromažďovat data IntelliTrace diagnostiky a metoda pro webový server, SharePoint, WPF a Windows aplikace formuláře na vzdálených počítačích beze změny cílového prostředí s použitím **samostatného kolektoru IntelliTrace**. Samostatný kolektor má větší dopad na výkon ve srovnání se spouštěním agenta Microsoft Monitoring Agent **monitorování** režimu. Zobrazit [použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
 Pokud používáte System Center 2012, použijte agenta Microsoft Monitoring Agent pomocí nástroje Operations Manager dostávat upozornění na problémy a vytváření pracovních položek sady Team Foundation Server s odkazy na uložené protokoly IntelliTrace. Můžete přiřadit tyto pracovní položky ostatním uživatelům k dalšímu ladění. Zobrazit [integrace nástroje Operations Manager s procesy vývoje](/previous-versions/system-center/system-center-2012-R2/jj614609(v=sc.12)) a [sledování pomocí agenta Microsoft Monitoring Agent](/previous-versions/system-center/system-center-2012-R2/dn465153(v=sc.12)).  
  
 Než začnete, zkontrolujte, zda je odpovídajícího zdroje a symbolů pro kód sestavené a nasazené. Díky tomu můžete přejít přímo do kódu aplikace při spuštění ladění a prohlížení diagnostických událostí v protokolu IntelliTrace. [Nastavte se sestavení](../debugger/diagnose-problems-after-deployment.md) tak, aby Visual Studio může automaticky vyhledat a otevřít odpovídající zdroj k nasazenému kódu.  
  
1.  [Krok 1: Nastavení agenta Microsoft Monitoring Agent](#SetUpMonitoring)  
  
2.  [Krok 2: Zahájení monitorování aplikace](#MonitorEvents)  
  
3.  [Krok 3: Uložení zaznamenané události](#SaveEvents)  
  
##  <a name="SetUpMonitoring"></a> Krok 1: Nastavení agenta Microsoft Monitoring Agent  
 Nastavení samostatného agenta na webovém serveru provádět místní monitorování bez změny vašich aplikací. Pokud používáte System Center 2012, přečtěte si [instalace agenta Microsoft Monitoring Agent](/previous-versions/system-center/system-center-2012-R2/dn465156(v=sc.12)).  
  
###  <a name="SetUpStandaloneMMA"></a> Nastavte samostatného agenta  
  
1.  Ujistěte se, že:  
  
    -   Webový server je spuštěn [podporované verze Internetové informační služby (IIS)](/previous-versions/system-center/system-center-2012-R2/dn465154(v=sc.12)).  
  
    -   Webový server má rozhraní .NET Framework 3.5, 4 nebo 4.5.  
  
    -   Webový server běží prostředí Windows PowerShell 3.0 nebo novější. [Otázka: Co když budu mít Windows PowerShell 2.0?](#PowerShell2)  
  
    -   Máte oprávnění správce na vašem webovém serveru spouštět příkazy prostředí PowerShell a recyklovat fond aplikací při spuštění sledování.  
  
    -   Jste odinstalovat všechny předchozí verze agenta Microsoft Monitoring Agent.  
  
2.  [Stáhněte si zdarma Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384), 32bitová verze **MMASetup-i386.exe** nebo 64bitovou verzi **MMASetup-AMD64.exe**, z webu Microsoft Download Center na webu Server.  
  
3.  Spouštění staženého spustitelného souboru spusťte Průvodce instalací.  
  
4.  Vytvořte zabezpečený adresář na webovém serveru k ukládání protokolů IntelliTrace, například **C:\IntelliTraceLogs**.  
  
     Ujistěte se, že tento adresář vytvořit před zahájením monitorování. Aby se zabránilo zpomalení vaší aplikace, vyberte umístění na místním vysokorychlostním disku, který není velmi aktivní.  
  
    > [!IMPORTANT]
    >  Protokoly nástroje IntelliTrace může obsahovat osobní a citlivé údaje. Omezte tento adresář pouze na ty identity, které musí pracovat se soubory. Zkontrolujte zásady ochrany osobních údajů vaší společnosti.  
  
5.  Ke spuštění podrobné úrovni funkcí monitorování nebo k monitorování aplikací služby SharePoint, měl fond aplikací, který je hostitelem vaší webové aplikaci nebo aplikaci služby SharePoint oprávnění čtení a zápisu do adresáře protokolu IntelliTrace. [Otázka: Jak můžu nastavit oprávnění pro fond aplikací?](#FullPermissionsITLog)  
  
### <a name="q--a"></a>Dotazy a odpovědi  
  
####  <a name="PowerShell2"></a> Otázka: Co když budu mít Windows PowerShell 2.0?  
 **Odpověď:** důrazně doporučujeme používat PowerShell 3.0. V opačném případě budete muset importovat rutiny Microsoft Monitoring Agent PowerShell při každém spuštění prostředí PowerShell. Také nebude mít přístup ke stažení obsahu nápovědy.  
  
1.  Otevřít **prostředí Windows PowerShell** nebo **Windows PowerShell ISE** okno příkazového řádku jako správce.  
  
2.  Importujte modul Microsoft Monitoring Agent PowerShell z výchozího umístění instalace:  
  
     **PS C: > Import-Module "C:\Program Files\Microsoft Monitoring Agent\Agent\PowerShell\Microsoft.MonitoringAgent.PowerShell\Microsoft.MonitoringAgent.PowerShell.dll"**  
  
3.  [Najdete na webu TechNet](http://technet.microsoft.com/systemcenter/default) zobrazíte nejaktuálnějšího obsahu nápovědy.  
  
####  <a name="FullPermissionsITLog"></a> Otázka: Jak můžu nastavit oprávnění pro fond aplikací?  
 **Odpověď:** použít Windows **icacls** příkaz % $n nebo pomocí Průzkumníka Windows (nebo Průzkumníka souborů). Příklad:  
  
- Nastavení oprávnění se Windows **icacls** příkaz:  
  
  - Pro webovou aplikaci v **DefaultAppPool** fondu aplikací:  
  
     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\DefaultAppPool":RX`  
  
  - Pro aplikaci služby SharePoint ve **SharePoint - 80** fondu aplikací:  
  
     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\SharePoint - 80":RX`  
  
    -nebo-  
  
- Nastavení oprávnění pomocí Průzkumníka Windows (nebo Průzkumníka souborů):  
  
  1.  Otevřít **vlastnosti** pro adresář protokolu IntelliTrace.  
  
  2.  Na **zabezpečení** kartě **upravit**, **přidat**.  
  
  3.  Ujistěte se, že **zabudované objekty zabezpečení** se zobrazí v **vyberte typ objektu** pole. Pokud ji má, možnost **typy objektů** a přidejte ji.  
  
  4.  Ujistěte se, že se zobrazí v místním počítači **z tohoto umístění** pole. Pokud ji má, možnost **umístění** ho změnit.  
  
  5.  V **zadejte názvy objektů k výběru** pole, přidat fond aplikací pro webovou aplikaci nebo aplikaci služby SharePoint.  
  
  6.  Zvolte **Kontrola názvů** přeložit název. Zvolte **OK**.  
  
  7.  Ujistěte se, že má fond aplikací **čtení & Spustit** oprávnění.  
  
##  <a name="MonitorEvents"></a> Krok 2: Zahájení monitorování aplikace  
 Použít rutinu prostředí Windows PowerShell [Start-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313686) příkazu zahajte sledování vaší aplikace. Pokud používáte System Center 2012, přečtěte si [monitorování webových aplikací pomocí agenta Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465157.aspx).  
  
1.  Na webovém serveru, otevřete **prostředí Windows PowerShell** nebo **Windows PowerShell ISE** okno příkazového řádku jako správce.  
  
     ![Otevřete prostředí Windows PowerShell jako správce](../debugger/media/ffr_powershellrunadmin.png "FFR_PowerShellRunAdmin")  
  
2.  Spustit [Start-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313686) příkazu zahajte sledování vaší aplikace. Tato operace restartuje všechny webové aplikace na webovém serveru.  
  
     Tady je krátkou syntaxi:  
  
     **Start-WebApplicationMonitoring** *"\<název_aplikace >"*  *\<monitoringMode >* *"\<outputPath >"*  *\<UInt32 >* *"\<collectionPlanPathAndFileName >"*  
  
     Tady je příklad, který používá jenom název webové aplikace a zjednodušené **monitorování** režimu:  
  
     **PS C: > Start-WebApplicationMonitoring "FabrikamFabrikamFiber.Web" sledovat "C:IntelliTraceLogs"**  
  
     Tady je příklad, který používá cesta služby IIS a zjednodušené **monitorování** režimu:  
  
     **PS C: > Start-WebApplicationMonitoring "IIS:sitesFabrikamFabrikamFiber.Web" sledovat "C:IntelliTraceLogs"**  
  
     Jakmile bude monitorování zahájeno, se může zobrazit pozastavení agenta sledování Microsoft během restartování aplikace.  
  
     ![Spuštění sledování pomocí agenta MMA potvrzení](../debugger/media/ffr_powershellstartmonitoringconfirmation.png "FFR_PowerShellStartMonitoringConfirmation")  
  
    |||  
    |-|-|  
    |*"\<název_aplikace >"*|Zadejte cestu k názvu webu a webové aplikace ve službě IIS. Můžete také zahrnout cestu ke službě IIS, pokud dáváte přednost.<br /><br /> *"\<IISWebsiteName >\\< IISWebAppName\>"*<br /><br /> -nebo-<br /><br /> **"IIS:\sites**  *\\< IISWebsiteName\>\\< IISWebAppName\>"*<br /><br /> Tuto cestu můžete najít ve Správci služby IIS. Příklad:<br /><br /> ![Cesta k webu služby IIS a web app](../debugger/media/ffr_iismanager.png "FFR_IISManager")<br /><br /> Můžete také použít [Get-WebSite](http://technet.microsoft.com/library/ee807832.aspx) a [získat WebApplication](http://technet.microsoft.com/library/ee790554.aspx) příkazy.|  
    |*\<monitoringMode >*|Zadejte režim monitorování:<br /><br /> <ul><li>**Monitorování**: minimální podrobnosti o událostech výjimky a události související s výkonem. Tento režim použije výchozí plán kolekce.</li><li>**Trasování**: zaznamenat podrobnosti na úrovni funkce nebo monitorování aplikací SharePoint 2010 a SharePoint 2013 pomocí zadaný plán shromažďování. V tomto režimu by mohlo způsobit nepoužitelnost vaše aplikace spouštět pomaleji.<br /><br /> <ul><li>[Otázka: Jak můžu nastavit oprávnění pro fond aplikací?](#FullPermissionsITLog)</li><li>[Otázka: jak lze získat většinu dat bez zpomalení aplikace?](#Minimizing)</li></ul><br />     V tomto příkladu zaznamenává události Sharepointu aplikace hostované na webu služby SharePoint:<br /><br />     **Start-WebApplicationMonitoring "FabrikamSharePointSite\FabrikamSharePointApp" trasování C:\IntelliTraceLogs""C:\Program Files\Microsoft Monitoring Agent\Agent\IntelliTraceCollector\collection_plan.ASP.NET.default.xml""**</li><li>**Vlastní**: zaznamenání vlastní podrobností pomocí zadané vlastní plán. Budete muset restartovat monitorování při úpravě plánu kolekce po monitorování je již spuštěna.</li></ul>|  
    |*"\<outputPath >"*|Zadejte úplné adresář pro ukládání protokolů IntelliTrace. Ujistěte se, že tento adresář vytvořit před zahájením monitorování.|  
    |*\<UInt32 >*|Zadejte maximální velikost pro protokol nástroje IntelliTrace. Výchozí maximální velikost protokolu IntelliTrace je 250 MB.<br /><br /> Když se dosáhne tohoto limitu, agent přepíše nejstarší položky, abyste udělali místo pro další položky. Chcete-li tento limit změnit, použijte **- MaximumFileSizeInMegabytes** možnost nebo upravit `MaximumLogFileSize` atribut v plánu shromažďování.|  
    |*"\<collectionPlanPathAndFileName >"*|Zadejte úplnou cestu nebo relativní cestu a název souboru v plánu shromažďování. Tento plán je soubor XML, který konfiguruje nastavení pro agenta.<br /><br /> Tyto plány jsou součástí agenta a pracovat s web apps a aplikací služby SharePoint:<br /><br /> -   **plán collection_plan.ASP.NET.default.XML**<br />     Shromažďuje pouze události, jako je například výjimky, události výkonu, volání databáze a požadavky na webový server.<br />-   **collection_plan.ASP.NET.Trace.XML**<br />     Shromažďuje volání úrovni funkcí a všechna data ve výchozí plán kolekce. Tento plán je vhodný pro podrobnou analýzu, ale může zpomalit vaši aplikaci.<br /><br /> Lokalizované verze těchto plánů můžete najít v podsložkách agenta. Můžete také [přizpůsobte tyto plány nebo vytvořte vlastní plány](http://go.microsoft.com/fwlink/?LinkId=227871) k nedocházelo ke zpomalování vaší aplikace. Umístěte vlastní plány do stejného zabezpečeného umístění jako agenta.<br /><br /> [Otázka: jak lze získat většinu dat bez zpomalení aplikace?](#Minimizing)|  
  
     Další informace o úplnou syntaxi a další příklady, spusťte **get-help Start-WebApplicationMonitoring-podrobné** příkazu nebo **get-help Start-WebApplicationMonitoring-příklady** příkaz.  
  
3.  Chcete-li zkontrolovat stav všech sledovaných webových aplikace, spusťte [Get-WebApplicationMonitoringStatus](http://go.microsoft.com/fwlink/?LinkID=313685) příkazu.  
  
### <a name="q--a"></a>Dotazy a odpovědi  
  
####  <a name="Minimizing"></a> Otázka: jak lze získat většinu dat bez zpomalení aplikace?  
 **Odpověď:** agenta Microsoft Monitoring Agent může shromažďovat velké množství dat a má vliv na výkon vaší aplikace v závislosti na tom, které chcete shromažďovat data a jak shromažďovat. Tady jsou některé způsoby, jak získat většinu dat bez zpomalení vaší aplikace:  
  
- Agent pro webové aplikace a aplikace služby SharePoint, zaznamenává data pro každou aplikaci, která sdílí určený fond aplikací. To může zpomalit jakékoli aplikaci, která sdílí stejný fond aplikací, i když můžete omezit kolekci pro moduly pro jednu aplikaci. Aby se zabránilo zpomalení jiné aplikace, hostujte každou aplikaci v jejím vlastním fondu aplikací.  
  
- Prohlédněte si události, pro které agent shromažďuje data v plánu shromažďování. Upravte plán shromažďování a zakažte události, které nejsou důležité nebo vás nezajímají. Tím lze vylepšit výkon při spouštění a výkon modulu runtime.  
  
   Chcete-li zakázat událost, nastavte `enabled` atribut pro `<DiagnosticEventSpecification>` elementu `false`:  
  
   `<DiagnosticEventSpecification enabled="false">`  
  
   Pokud `enabled` atribut neexistuje, je událost povolena.  
  
   Příklad:  
  
  -   Zakážete události pracovního postupu Windows pro aplikace, které nepoužívají Windows Workflow.  
  
  -   Zakažte registru pro aplikace, které přístup k registru, ale nemají problémy s nastavením registru.  
  
- Zkontrolujte moduly, pro které agent shromažďuje data v plánu shromažďování. Upravte plán kolekce umožňuje zahrnout pouze moduly, které vás zajímají.  
  
   To snižuje množství informací o volání metody a dalších instrumentačních dat, které agent shromažďuje při spuštění a spuštění aplikace. Tato data vám umožní krokovat kód při ladění a kontrola hodnoty předané do a vrácené z volání funkcí.  
  
  1. Otevřete plán shromažďování. Najít `<ModuleList>` elementu.  
  
  2. V `<ModuleList>`, nastavte `isExclusionList` atribut `false`.  
  
  3. Použití `<Name>` – element pro určení každého modulu s některou z následujících akcí: název souboru, Řetězcová hodnota pro zahrnutí každého modulu, jehož název obsahuje daný řetězec, nebo veřejný klíč.  
  
     Tento příklad vytvoří seznam, který shromažďuje data pouze z modulu hlavní webové aplikace Fabrikam Fiber:  
  
  ```xml  
  <ModuleList isExclusionList="false">  
     <Name>FabrikamFiber.Web.dll</Name>  
  </ModuleList>  
  
  ```  
  
   Pro shromažďování dat z libovolného modulu, jehož název obsahuje "Fabrikam", vytvořte seznam podobný následujícímu:  
  
  ```xml  
  <ModuleList isExclusionList="false">  
     <Name>Fabrikam</Name>  
  </ModuleList>  
  
  ```  
  
   Ke shromažďování dat z modulů zadáním jejich tokenů veřejných klíčů, vytvořte seznam podobný následujícímu:  
  
  ```xml  
  <ModuleList isExclusionList="false">  
     <Name>PublicKeyToken:B77A5C561934E089</Name>  
     <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>  
     <Name>PublicKeyToken:31BF3856AD364E35</Name>  
     <Name>PublicKeyToken:89845DCD8080CC91</Name>  
     <Name>PublicKeyToken:71E9BCE111E9429C</Name>  
  </ModuleList>  
  
  ```  
  
   **Otázka: Proč právě namísto toho Nevyloučit moduly?**  
  
   **Odpověď:** ve výchozím nastavení plány shromažďování dat vylučují moduly nastavením `isExclusionList` atribut `true`. Však to může být stále shromažďování dat z modulů, které nesplňují kritéria v seznamu nebo, které vás nemusejí zajímat, například moduly třetích stran nebo open source.  
  
#### <a name="q-what-values-does-the-agent-collect"></a>Otázka: jaké hodnoty je nemá agenta shromažďování?  
 **Odpověď:** dopad na výkon, agent shromažďuje pouze tyto hodnoty:  
  
- Primitivní datové typy, které jsou předány do a vracené z metod  
  
- Předán primitivních datových typů v polích objektů nejvyšší úrovně a vracené z metod  
  
  Předpokládejme například, že máte `AlterEmployee` podpis metody, která přijímá celočíselné `id` a `Employee` objekt `oldemployee`:  
  
  `public Employee AlterEmployee(int id, Employee oldemployee)`  
  
  `Employee` Typ má následující atributy: `Id`, `Name`, a `HomeAddress`. Existuje vztah přidružení mezi `Employee` a `Address` typu.  
  
  ![Vztah mezi zaměstnanci a adresa](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")  
  
  Agent zaznamenává hodnoty `id`, `Employee.Id`, `Employee.Name` a `Employee` objekt vrácený z `AlterEmployee` metody. Agent však nezaznamenává informace o `Address` objektu, než zda měl hodnotu null nebo ne. Agent také nezaznamenává data o místních proměnných v `AlterEmployee` metoda Pokud jiné metody nepoužívají tyto místní proměnné jako parametry v tomto okamžiku jsou zaznamenávány jako parametry metod.  
  
##  <a name="SaveEvents"></a> Krok 3: Uložení zaznamenané události  
 Když najdete chybu nebo potíže s výkonem, uložte zaznamenané události do protokolu IntelliTrace. Agent vytvoří protokol pouze v případě, že zaznamenal události. Pokud používáte System Center 2012, přečtěte si [monitorování webových aplikací pomocí agenta Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465157.aspx).  
  
### <a name="save-recorded-events-but-continue-monitoring"></a>Uložení zaznamenaných událostí ale pokračovat v monitorování  
 Když chcete vytvořit protokol nástroje IntelliTrace, ale nechcete, aby k restartování aplikace nebo zastavit monitorování, postupujte podle těchto kroků. Agent pokračuje ve sledování i v případě restartování serveru nebo aplikace.  
  
1. Na vašem webovém serveru otevřete okno příkazového řádku prostředí Windows PowerShell jako správce.  
  
2. Spustit [Checkpoint-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313684) příkazu uložte snímek protokolu IntelliTrace:  
  
    **Checkpoint-WebApplicationMonitoring** *"\<IISWebsiteName >\\< IISWebAppName\>"*  
  
    \- nebo –  
  
    **Checkpoint-WebApplicationMonitoring "IIS:\sites**  *\\< IISWebsiteName\>\\< IISWebAppName\>"*  
  
    Příklad:  
  
    **PS C:\\> Checkpoint-WebApplicationMonitoring "Fabrikam\FabrikamFiber.Web"**  
  
    -nebo-  
  
    **PS C: > Checkpoint-WebApplicationMonitoring "IIS:sitesFabrikamFabrikamFiber.Web"**  
  
    Další informace získáte spuštěním **get-help Checkpoint-WebApplicationMonitoring-podrobné** příkazu nebo **get-help Checkpoint-WebApplicationMonitoring-příklady** příkazu.  
  
3. Zkopírujte protokol k zabezpečení sdílené složky a potom otevřete protokol z počítače, který má Visual Studio Enterprise (ale ne edice Professional nebo Community).  
  
   > [!IMPORTANT]
   >  Buďte opatrní při sdílení protokolů IntelliTrace, protože mohou obsahovat osobní a citlivé údaje. Ujistěte se, kdo má přístup k tyto protokoly má oprávnění k oprávněn prohlížet tato data. Zkontrolujte zásady ochrany osobních údajů vaší společnosti.  
  
   **Další krok:** [Diagnostika zaznamenané události v sadě Visual Studio Enterprise](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)  
  
### <a name="save-recorded-events-and-stop-monitoring"></a>Uložení zaznamenaných událostí a zastavit monitorování  
 Chcete-li pouze diagnostické informace při reprodukci konkrétního problému, postupujte podle těchto kroků. Tato operace restartuje všechny webové aplikace na webovém serveru.  
  
1. Na vašem webovém serveru otevřete okno příkazového řádku prostředí Windows PowerShell jako správce.  
  
2. Spustit [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) příkaz k vytvoření protokolu IntelliTrace a zastavte sledování konkrétní webové aplikace:  
  
    **Stop-WebApplicationMonitoring** *"\<IISWebsiteName >\\< IISWebAppName\>"*  
  
    \- nebo –  
  
    **Stop-WebApplicationMonitoring "IIS:\sites**  *\\< IISWebsiteName\>\\< IISWebAppName\>"*  
  
    Nebo se zastavit monitorování všech webových aplikací:  
  
    **Stop-WebApplicationMonitoring - všechny**  
  
    Příklad:  
  
    **PS C:\\> Stop-WebApplicationMonitoring "Fabrikam\iFabrikamFiber.Web"**  
  
    \- nebo –  
  
    **PS C:\\> Stop-WebApplicationMonitoring "IIS:\sites\Fabrikam\FabrikamFiber.Web"**  
  
    Další informace získáte spuštěním **get-help Stop-WebApplicationMonitoring-podrobné** příkazu nebo **get-help Stop-WebApplicationMonitoring-příklady** příkazu.  
  
3. Zkopírujte protokol k zabezpečení sdílené složky a potom otevřete protokol z počítače, který má Visual Studio Enterprise.  
  
   **Další krok:** [Diagnostika zaznamenané události v sadě Visual Studio Enterprise](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)  
  
## <a name="q--a"></a>Dotazy a odpovědi  
  
### <a name="q-where-can-i-get-more-information"></a>D: kde lze získat další informace?  
  
#### <a name="blogs"></a>Blogy  
 [Představujeme službu Microsoft Monitoring Agent.](https://blogs.msdn.microsoft.com/devops/2013/09/20/introducing-microsoft-monitoring-agent/)  
  
 [Optimalizace kolekce IntelliTrace na provozních serverech](http://go.microsoft.com/fwlink/?LinkId=255233)  
  
#### <a name="forums"></a>Diskuzní fóra  
 [Diagnostika sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)
