---
title: Použití samostatného kolektoru IntelliTrace | Microsoft Docs
ms.date: 07/30/2019
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.collectdataoutsideVS
helpviewer_keywords:
- IntelliTrace, debugging applications in production
ms.assetid: 1bde9807-8219-4a2a-a440-ac5ee5178159
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6f0e0ce657c1cc0ed79d56e3daa90480ed0c1381
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536490"
---
# <a name="using-the-intellitrace-stand-alone-collector-c-visual-basic"></a>Použití samostatného kolektoru IntelliTrace (C#, Visual Basic)

**Samostatný kolektor IntelliTrace** umožňuje shromažďovat diagnostická data IntelliTrace pro vaše aplikace na produkčních serverech nebo v jiných prostředích, aniž by bylo nutné instalovat sadu Visual Studio do cílového počítače a přitom beze změny prostředí cílového systému. Samostatné kolektor IntelliTrace funguje na webech, SharePointu, WPF a aplikacích model Windows Forms. Až budete hotovi s shromažďováním dat, stačí odstranit kolektor a odinstalovat ho.

 Sledujte IntelliTrace v akci: [shromažďování a analýza dat IntelliTrace v produkčním prostředí pro ladění (video pro kanál 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)

> [!NOTE]
> Můžete také shromažďovat stejná IntelliTrace data pro webové aplikace a aplikace SharePoint běžící na vzdálených počítačích pomocí **Microsoft Monitoring Agent** v režimu **trasování** .
>
> Události související s výkonem můžete shromažďovat v datech IntelliTrace spuštěním agenta v režimu **monitorování** . Režim **monitorování** má méně vliv na výkon než režim **trasování** nebo samostatný **kolektor IntelliTrace**. Microsoft Monitoring Agent při instalaci změní prostředí cílového systému. Viz [použití Microsoft Monitoring Agent](../debugger/using-the-microsoft-monitoring-agent.md).
> Samostatný kolektor IntelliTrace nepodporuje snímky procesů.

 **Požadavky**

- .NET Framework 3,5 nebo vyšší

- Visual Studio Enterprise (ale ne edice Professional nebo Community) na vývojovém počítači nebo jiném počítači pro otevření souborů. iTrace

  > [!NOTE]
  > Nezapomeňte uložit soubory symbolů (PDB). Chcete-li ladit pomocí IntelliTrace a krokovat kód, je nutné mít stejné zdrojové soubory a soubory symbolů. Viz [diagnostikování problémů po nasazení](../debugger/diagnose-problems-after-deployment.md).

  **Nejčastější dotazy**

- [Které aplikace pracují se sadou kolekcí?](#WhatApps)

- [Jak mám začít?](#GetStarted)

- [Jak můžu získat většinu dat bez zpomalení aplikace?](#Minimizing)

- [Kde jinak můžu získat IntelliTrace data?](#WhereElse)

## <a name="what-apps-work-with-the-collector"></a><a name="WhatApps"></a>Které aplikace pracují se sadou kolekcí?

- Webové aplikace ASP.NET hostované ve službě Internetová informační služba (IIS) verze 7,0, 7,5, 8,0, 12,0 a 16,0

- Aplikace SharePoint 2010 a SharePoint 2013

- Windows Presentation Foundation (WPF) a aplikace model Windows Forms.

## <a name="how-do-i-get-started"></a><a name="GetStarted"></a>Návody začít?

1. [Instalace kolekce](#BKMK_Install_the_IntelliTrace_Stand_Alone_Collector)

2. [Nastavení oprávnění pro adresář sběrače](#ConfigurePermissionsRunningCollector)

3. [Instalace rutin prostředí PowerShell pro IntelliTrace pro shromažďování dat pro webové aplikace nebo aplikace služby SharePoint](#BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets)

4. [Nastavení oprávnění pro adresář souboru. iTrace](#BKMK_Create_and_Configure_a_Log_File_Directory)

5. [Shromažďování dat z webové aplikace nebo aplikace služby SharePoint](#BKMK_Collect_Data_from_IIS_Application_Pools)

     -nebo-

     [Shromažďovat data ze spravované aplikace](#BKMK_Collect_Data_from_Executables)

6. [Otevřete soubor. iTrace v Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="install-the-collector"></a><a name="BKMK_Install_the_IntelliTrace_Stand_Alone_Collector"></a>Instalace kolekce

1. Na serveru vaší aplikace vytvořte adresář kolektoru, například: **C:\IntelliTraceCollector** .

2. Získejte kolektor z [webu Microsoft Download Center](https://visualstudio.microsoft.com/downloads/#intellitrace-standalone-collector-for-visual-studio-2019), [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=intellitrace%20standalone%20collector%20visual%20studio%202017)nebo z instalační složky nástroje Visual Studio 2013 Update 3. [IntelliTrace Collector for Visual Studio 2013 Update 4](https://www.microsoft.com/download/details.aspx?id=44909)::

   - **Stažení softwaru** nebo **My.VisualStudio.com**společnosti Microsoft:

     1. Vedle **IntelliTraceCollector.exe**klikněte na **Stáhnout**.

     2. Uložte IntelliTraceCollector.exe do adresáře kolektoru, například: **C:\IntelliTraceCollector**

     3. Spusťte IntelliTraceCollector.exe. Tím se extrahuje soubor IntelliTraceCollection.cab.

        \-ani

   - **Instalační složka sady Visual Studio**:

     1. Zkopírujte IntelliTraceCollection.cab ze složky, ve které je kolektor nainstalován, například:

          **.. \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace**

          nebo, pro předchozí verze sady Visual Studio:

          **.. \Microsoft Visual Studio 12.0 \ Common7\IDE\CommonExtensions\Microsoft\IntelliTrace\12.0.0**

     2. Vložte IntelliTraceCollection.cab do adresáře kolektoru, například: **C:\IntelliTraceCollector**

3. Rozbalte IntelliTraceCollection.cab:

   1. Na serveru vaší aplikace otevřete okno příkazového řádku jako správce.

   2. Přejděte do adresáře kolektoru, například: **C:\IntelliTraceCollector**

   3. Pomocí příkazu **Rozbalit** , včetně tečky (**.**) na konci, rozbalte IntelliTraceCollection.cab:

        `expand  /f:* IntelliTraceCollection.cab .`

       > [!NOTE]
       > Tečka (**.**) zachová podsložky, které obsahují lokalizované plány kolekcí.

## <a name="set-up-permissions-for-the-collector-directory"></a><a name="ConfigurePermissionsRunningCollector"></a>Nastavení oprávnění pro adresář sběrače

1. Na serveru vaší aplikace otevřete okno příkazového řádku jako správce.

2. Pomocí příkazu Windows **Icacls** udělte správci serveru úplná oprávnění k adresáři kolektoru. Příklad:

     `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\AdministratorID>* `":F`

3. Shromažďování dat pro webovou aplikaci nebo aplikaci služby SharePoint:

    1. Poskytněte osobě, která spustí rutiny prostředí PowerShell pro IntelliTrace, úplná oprávnění k adresáři kolektoru.

         Příklad:

         `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\UserID>* `":F`

    2. Udělte fondu aplikací oprávnění ke čtení a spouštění aplikace SharePoint pro adresář sběrače.

         Příklad:

        - Pro webovou aplikaci ve fondu aplikací **DefaultAppPool** :

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\DefaultAppPool":RX`

        - Pro aplikaci SharePoint ve fondu aplikací **SharePoint-80** :

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\SharePoint - 80":RX`

## <a name="install-intellitrace-powershell-cmdlets-to-collect-data-for-web-apps-or-sharepoint-applications"></a><a name="BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets"></a>Instalace rutin prostředí PowerShell pro IntelliTrace pro shromažďování dat pro webové aplikace nebo aplikace služby SharePoint

1. Na serveru vaší aplikace se ujistěte, že je PowerShell povolený. Ve většině verzí Windows serveru můžete tuto funkci přidat do nástroje pro správu **Správce serveru** .

     ![Přidání PowerShellu pomocí Správce serveru](../debugger/media/intellitrace_servermanager_addpowershell.png "INTELLITRACE_ServerManager_AddPowerShell")

2. Nainstalujte rutiny prostředí PowerShell pro IntelliTrace.

    1. Otevřete okno příkazového řádku PowerShellu jako správce.

        1. Klikněte na tlačítko **Start**, **všechny programy**, **příslušenství**, **Windows PowerShell**.

        2. Vyberte jeden z následujících kroků:

            - V 64 operačních systémech otevřete místní nabídku **prostředí Windows PowerShell**. Vyberte **Spustit jako správce**.

            - V 32 operačních systémech otevřete místní nabídku **prostředí Windows PowerShell (x86)**. Vyberte **Spustit jako správce**.

    2. V příkazovém okně PowerShellu pomocí příkazu **Import-Module** importujte **Microsoft.VisualStudio.IntelliTrace.PowerShell.dll**.

         Příklad:

         `Import-Module "C:\IntelliTraceCollector\Microsoft.VisualStudio.IntelliTrace.PowerShell.dll"`

## <a name="set-up-permissions-for-the-itrace-file-directory"></a><a name="BKMK_Create_and_Configure_a_Log_File_Directory"></a>Nastavení oprávnění pro adresář souboru. iTrace

1. Na serveru vaší aplikace vytvořte adresář souboru. iTrace, například: **C:\IntelliTraceLogFiles**

   > [!NOTE]
   > - Abyste se vyhnuli zpomalení vaší aplikace, vyberte umístění na místním vysokorychlostním disku, který není příliš aktivní.
   >   - Soubory. iTrace a soubory kolektoru můžete umístit na stejné místo. Pokud však máte webovou aplikaci nebo aplikaci služby SharePoint, ujistěte se, že je toto místo mimo adresář, který hostuje aplikaci.
   >
   > [!IMPORTANT]
   > - Omezte adresář souboru. iTrace pouze na ty identity, které musí spolupracovat se kolektorem. Soubor. iTrace může obsahovat citlivé informace, jako jsou data uživatelů, databáze, jiná zdrojová umístění a připojovací řetězce, protože IntelliTrace může zaznamenat jakákoli data, která přecházejí do parametrů metody nebo jako návratové hodnoty.
   >   - Ujistěte se, že uživatelé, kteří můžou otevírat soubory. iTrace, mají oprávnění zobrazovat citlivá data. Při sdílení souborů. iTrace buďte opatrní. Pokud musí mít přístup jiní lidé, zkopírujte soubory do zabezpečeného sdíleného umístění.

2. U webové aplikace nebo aplikace služby SharePoint udělte fondu aplikací úplná oprávnění k adresáři souboru. iTrace. Můžete použít příkaz Windows **Icacls** nebo použít Průzkumníka Windows (nebo Průzkumníka souborů).

    Příklad:

   - Nastavení oprávnění pomocí příkazu Windows **Icacls** :

     - Pro webovou aplikaci ve fondu aplikací **DefaultAppPool** :

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\DefaultAppPool":F`

     - Pro aplikaci SharePoint ve fondu aplikací **SharePoint-80** :

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\SharePoint - 80":F`

       -nebo-

   - Nastavení oprávnění pomocí Průzkumníka Windows (nebo Průzkumníka souborů):

     1. Otevřete **vlastnosti** adresáře souboru. iTrace.

     2. Na kartě **zabezpečení** vyberte možnost **Upravit**, **Přidat**.

     3. Zajistěte, aby se v poli **Vybrat typ objektu** zobrazily **předdefinované objekty zabezpečení** . Pokud tam není, vyberte **typy objektů** , které chcete přidat.

     4. Ujistěte se, že se Váš místní počítač zobrazuje v poli **z tohoto umístění** . Pokud tam není, vyberte **umístění** a změňte je.

     5. Do pole **Zadejte názvy objektů k výběru** přidejte fond aplikací pro webovou aplikaci nebo aplikaci služby SharePoint.

     6. Pro překlad názvu vyberte možnost **kontrolovat názvy** . Vyberte **OK**.

     7. Ujistěte se, že fond aplikací má **oprávnění Úplné řízení**.

## <a name="collect-data-from-a-web-app-or-sharepoint-application"></a><a name="BKMK_Collect_Data_from_IIS_Application_Pools"></a>Shromažďování dat z webové aplikace nebo aplikace služby SharePoint

1. Pokud chcete začít shromažďovat data, otevřete okno příkazového řádku PowerShellu jako správce a pak spusťte tento příkaz:

     `Start-IntelliTraceCollection` `"` *\<ApplicationPool>* `"` *\<PathToCollectionPlan>* *\<FullPathToITraceFileDirectory>*

    > [!IMPORTANT]
    > Po spuštění tohoto příkazu zadejte **Y** a potvrďte tak, že chcete začít shromažďovat data.

     Chcete-li například shromažďovat data z aplikace služby SharePoint ve fondu aplikací **SharePoint-80** :

     `Start-IntelliTraceCollection "SharePoint - 80" "C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogFiles"`

    |Name|Popis|
    |-|-|
    |*ApplicationPool*|Název fondu aplikací, ve kterém se vaše aplikace spouští|
    |*PathToCollectionPlan*|Cesta k plánu shromažďování dat, soubor. XML, který konfiguruje nastavení pro kolektor.<br /><br /> Můžete zadat plán, který je součástí kolekce. Následující plány fungují pro webové aplikace a aplikace služby SharePoint:<br /><br /> -collection_plan.ASP.NET.default.xml<br />     Shromažďuje pouze události IntelliTrace a události služby SharePoint, včetně výjimek, volání databáze a požadavků na webový server.<br />-collection_plan.ASP.NET.trace.xml<br />     Shromažďuje volání funkcí a všechna data v collection_plan.ASP.NET.default.xml. Tento plán je vhodný pro podrobnou analýzu, ale může zpomalit aplikaci více než collection_plan.ASP.NET.default.xml.<br /><br /> Abyste se vyhnuli zpomalení vaší aplikace, přizpůsobte si tyto plány nebo vytvořte vlastní plán. Z důvodu zabezpečení umístěte vlastní plány do stejného zabezpečeného umístění jako soubory kolektoru. Přečtěte si téma [Vytvoření a přizpůsobení plánů kolekcí IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) a [návody získání většiny dat bez zpomalení aplikace?](#Minimizing) **Poznámka:**  Ve výchozím nastavení je maximální velikost souboru. iTrace 100 MB. Když soubor. iTrace dosáhne tohoto limitu, kolektor odstraní nejstarší položky souboru, aby bylo možné místo pro novější položky. Chcete-li tento limit změnit, upravte atribut plánu kolekce `MaximumLogFileSize` . <br /><br /> *Kde najdu lokalizované verze těchto plánů kolekcí?*<br /><br /> Lokalizované plány můžete najít v podsložkách kolekce.|
    |*FullPathToITraceFileDirectory*|Úplná cesta k adresáři souboru. iTrace. **Poznámka k zabezpečení:**  Zadejte úplnou cestu, nikoli relativní cestu.|

     Kolektor se připojí k fondu aplikací a začne shromažďovat data.

     *Můžu v tuto chvíli otevřít soubor. iTrace?* Ne, soubor je během shromažďování dat uzamčen.

2. Reprodukujte problém.

3. Chcete-li vytvořit kontrolní bod souboru. iTrace, použijte tuto syntaxi:

     `Checkpoint-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

4. Ke kontrole stavu shromažďování použijte tuto syntaxi:

     `Get-IntelliTraceCollectionStatus`

5. Chcete-li zastavit shromažďování dat, použijte tuto syntaxi:

     `Stop-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

    > [!IMPORTANT]
    > Po spuštění tohoto příkazu zadejte **Y** a potvrďte tak, že chcete zastavit shromažďování dat. V opačném případě může kolektor i nadále shromažďovat data, soubor iTrace zůstane uzamčený nebo soubor nemusí obsahovat užitečná data.

6. [Otevřete soubor. iTrace v Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="collect-data-from-a-managed-app"></a><a name="BKMK_Collect_Data_from_Executables"></a>Shromažďovat data ze spravované aplikace

1. Pokud chcete spustit aplikaci a shromažďovat data ve stejnou dobu, použijte tuto syntaxi:

     *\<FullPathToIntelliTraceCollectorExecutable>* `\IntelliTraceSC.exe launch /cp:` *\<PathToCollectionPlan>* `/f:` *\<FullPathToITraceFileDirectoryAndFileName>* *\<PathToAppExecutableFileAndFileName>*

     Například pro shromažďování dat z aplikace s názvem **MyApp**:

     `C:IntelliTraceCollectorIntelliTraceSC.exe launch /cp:"C:IntelliTraceCollectorcollection_plan.ASP.NET.default.xml" /f:"C:IntelliTraceLogFilesMyApp.itrace" "C:MyAppMyApp.exe"`

    |Name|Popis|
    |-|-|
    |*FullPathToIntelliTraceCollectorExecutable*|Úplná cesta ke spustitelnému souboru kolektoru, IntelliTraceSC.exe|
    |*PathToCollectionPlan*|Cesta k plánu shromažďování dat, soubor. XML, který konfiguruje nastavení pro kolektor.<br /><br /> Můžete zadat plán, který je součástí kolekce. Následující plány fungují pro spravované aplikace:<br /><br /> -collection_plan.ASP.NET.default.xml<br />     Shromažďuje pouze události IntelliTrace, včetně výjimek, volání databáze a požadavků na webový server.<br />-collection_plan.ASP.NET.trace.xml<br />     Shromažďuje volání funkcí a všechna data v collection_plan.ASP.NET.default.xml. Tento plán je vhodný pro podrobnou analýzu, ale může zpomalit aplikaci více než collection_plan.ASP.NET.default.xml.<br /><br /> Abyste se vyhnuli zpomalení vaší aplikace, přizpůsobte si tyto plány nebo vytvořte vlastní plán. Z důvodu zabezpečení umístěte vlastní plány do stejného zabezpečeného umístění jako soubory kolektoru. Přečtěte si téma [Vytvoření a přizpůsobení plánů kolekcí IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) a [návody získání většiny dat bez zpomalení aplikace?](#Minimizing) **Poznámka:**  Ve výchozím nastavení je maximální velikost souboru. iTrace 100 MB. Když soubor. iTrace dosáhne tohoto limitu, kolektor odstraní nejstarší položky souboru, aby bylo možné místo pro novější položky. Chcete-li tento limit změnit, upravte atribut plánu kolekce `MaximumLogFileSize` . <br /><br /> *Kde najdu lokalizované verze těchto plánů kolekcí?*<br /><br /> Lokalizované plány můžete najít v podsložkách kolekce.|
    |*FullPathToITraceFileDirectoryAndFileName*|Úplná cesta k adresáři souboru. iTrace a název souboru. iTrace s příponou **. iTrace** **Poznámka k zabezpečení:**  Zadejte úplnou cestu, nikoli relativní cestu.|
    |*PathToAppExecutableFileAndFileName*|Cesta a název souboru vaší spravované aplikace|

2. Zastavte shromažďování dat ukončením aplikace.

3. [Otevřete soubor. iTrace v Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="open-the-itrace-file-in-visual-studio-enterprise"></a><a name="BKMK_View_IntelliTrace_Log_Files"></a>Otevřete soubor. iTrace v Visual Studio Enterprise

> [!NOTE]
> Chcete-li ladit pomocí IntelliTrace a krokovat kód, je nutné mít stejné zdrojové soubory a soubory symbolů. Viz [diagnostikování problémů po nasazení](../debugger/diagnose-problems-after-deployment.md).

1. Přesuňte soubor. iTrace nebo ho zkopírujte do počítače s Visual Studio Enterprise (ale ne edice Professional nebo Community).

2. Dvakrát klikněte na soubor. iTrace mimo aplikaci Visual Studio nebo ho otevřete v rámci sady Visual Studio.

     Visual Studio zobrazí stránku **souhrnu IntelliTrace** . Ve většině sekcí můžete zkontrolovat události nebo jiné položky, zvolit položku a spustit ladění pomocí IntelliTrace v místě, kde a kdy k události došlo. Viz [použití uložených IntelliTrace dat](../debugger/using-saved-intellitrace-data.md).

    > [!NOTE]
    > Chcete-li ladit pomocí IntelliTrace a krokovat kód, musíte mít na svém vývojovém počítači vyhovující zdrojové soubory a soubory symbolů. Viz [diagnostikování problémů po nasazení](../debugger/diagnose-problems-after-deployment.md).

## <a name="how-do-i-get-the-most-data-without-slowing-down-my-app"></a><a name="Minimizing"></a>Návody získat nejvíc dat bez zpomalení aplikace?
 IntelliTrace může shromažďovat spoustu dat, takže dopad na výkon vaší aplikace závisí na datech, která IntelliTrace shromažďuje, a na druhu kódu, který analyzuje. Viz [optimalizace shromažďování IntelliTrace na produkčních serverech](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/).

 Tady je několik způsobů, jak získat většinu dat bez zpomalení aplikace:

- Spusťte kolektor pouze v případě, že se domníváte, že došlo k potížím, nebo když můžete problém reprodukován.

   Spusťte shromažďování, reprodukování problému a potom zastavte shromažďování. Otevřete soubor. iTrace v Visual Studio Enterprise a prověřte data. Viz [otevření souboru. iTrace v Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files).

- V případě webových aplikací a aplikací služby SharePoint kolekce zaznamenává data pro každou aplikaci, která sdílí určený fond aplikací. To může zpomalit jakoukoliv aplikaci, která sdílí stejný fond aplikací, a to i v případě, že v plánu shromažďování dat můžete zadat jenom moduly pro jednu aplikaci.

   Chcete-li zabránit sběrači zpomalit ostatní aplikace, hostovat každou aplikaci ve vlastním fondu aplikací.

- Zkontrolujte události v plánu shromažďování dat, pro které IntelliTrace shromažďuje data. Upravte plán shromažďování dat, abyste zakázali události, které nejsou důležité nebo vás zajímají.

   Chcete-li zakázat událost, nastavte `enabled` atribut `<DiagnosticEventSpecification>` elementu na `false` :

   `<DiagnosticEventSpecification enabled="false">`

   Pokud `enabled` atribut neexistuje, událost je povolena.

   *Jak to zvyšuje výkon?*

  - Dobu spuštění můžete zkrátit tím, že zakážete události, které nejsou relevantní pro danou aplikaci. Například můžete zakázat události Windows Workflow pro aplikace, které nepoužívají pracovní postup systému Windows.

  - Můžete zlepšit výkon při spuštění i za běhu tím, že zakážete události registru pro aplikace, které přistupují k registru, ale nezobrazují problémy s nastavením registru.

- Zkontrolujte moduly v plánu shromažďování dat, pro které IntelliTrace shromažďuje data. Upravte plán shromažďování dat tak, aby obsahoval pouze ty moduly, které vás zajímají:

  1. Otevřete plán kolekce. Vyhledejte `<ModuleList>` element.

  2. V `<ModuleList>` , nastavte `isExclusionList` atribut na `false` .

  3. Pomocí `<Name>` elementu zadejte každý modul s jedním z následujících způsobů: název souboru, Řetězcová hodnota pro zahrnutí jakéhokoli modulu, jehož název obsahuje tento řetězec nebo veřejný klíč.

     Chcete-li například shromažďovat data pouze z hlavního webového modulu webové aplikace Fabrikam Fiber, vytvořte seznam podobný tomuto:

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

   *Jak to zvyšuje výkon?*

   Tím se sníží množství informací o volání metody a další data instrumentace, která IntelliTrace shromažďuje při spuštění a spuštění aplikace. Tato data vám umožní:

  - Krokovat kód po shromáždění dat

  - Prověřte hodnoty předané do a vrácené z volání funkcí.

    *Proč místo toho vyloučit moduly?*

    Ve výchozím nastavení plány shromažďování dat vyloučí moduly nastavením `isExclusionList` atributu na `true` . Vyloučení modulů však může přesto vést k shromažďování dat z modulů, které nesplňují kritéria seznamu a nemusí vás zajímat, například moduly třetích stran nebo open source.

- *Existují nějaká data, která IntelliTrace neshromažďuje?*

   Ano, pokud chcete snížit dopad na výkon, IntelliTrace omezuje shromažďování dat na hodnoty primitivních datových typů předaných do a vrácených z metod a na hodnoty primitivních datových typů v polích objektů nejvyšší úrovně předaných do a vrácených z metod.

   Předpokládejme například, že máte `AlterEmployee` signaturu metody, která přijímá celé číslo `id` a `Employee` objekt `oldemployee` :

   `public Employee AlterEmployee(int id, Employee oldemployee)`

   `Employee`Typ má následující atributy: `Id` , `Name` a `HomeAddress` . Mezi a typem existuje vztah přidružení `Employee` `Address` .

   ![Vztah mezi zaměstnancem a adresou](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")

   Kolektor zaznamenává hodnoty pro `id` , `Employee.Id` `Employee.Name` a `Employee` objekt vrácený z `AlterEmployee` metody. Kolektor však nezaznamená informace o objektu, který je `Address` jiný než bez ohledu na to, zda byl null nebo ne. Kolektor také nezaznamenává data týkající se místních proměnných v `AlterEmployee` metodě, pokud jiné metody tyto místní proměnné nepoužívají jako parametry, které ukazují, že jsou zaznamenávány jako parametry metody.

## <a name="where-else-can-i-get-intellitrace-data"></a><a name="WhereElse"></a>Kde jinak můžu získat IntelliTrace data?

IntelliTrace data z relace ladění IntelliTrace můžete získat v Visual Studio Enterprise. Viz [funkce IntelliTrace](../debugger/intellitrace-features.md).

## <a name="where-can-i-get-more-information"></a>Zdroje dalších informací
 [Použití dat uložených nástrojem IntelliTrace](../debugger/using-saved-intellitrace-data.md)

 [IntelliTrace](../debugger/intellitrace.md)

### <a name="blogs"></a>Blogy
 [Vzdálené použití samostatného kolektoru IntelliTrace](https://devblogs.microsoft.com/devops/using-the-intellitrace-standalone-collector-remotely/)

 [Vytváření a přizpůsobení plánů kolekcí IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/)

 [Optimalizace kolekce IntelliTrace na produkčních serverech](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)

 [Microsoft DevOps](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>Fóra
 [Visual Studio – ladicí program](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="videos"></a>Videa
 [Video pro kanál 9: shromažďování a analýza dat IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)
