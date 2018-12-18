---
title: Použití samostatného kolektoru IntelliTrace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.historicaldebug.collectdataoutsideVS
helpviewer_keywords:
- IntelliTrace, debugging applications in production
ms.assetid: 1bde9807-8219-4a2a-a440-ac5ee5178159
caps.latest.revision: 111
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2e2fc006874316974dc92ea45b112399f6f5aad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792880"
---
# <a name="using-the-intellitrace-stand-alone-collector"></a>Použití samostatného kolektoru IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Samostatného kolektoru IntelliTrace** umožňuje shromažďovat diagnostická data IntelliTrace pro vaše aplikace na provozních serverech nebo v jiných prostředích, bez nutnosti instalace sady Visual Studio na cílovém počítači a beze změny cílové prostředí systému. Samostatný kolektor IntelliTrace funguje pro aplikace z webu služby SharePoint, WPF a Windows Forms. Po dokončení shromažďování dat, stačí kolektor odstraňte a odinstalujte ho.  
  
 Sledujte nástroj IntelliTrace v akci: [shromažďování a analýza dat IntelliTrace v produkčním prostředí pro ladění (video Channel 9)](http://go.microsoft.com/fwlink/?LinkID=251851)  
  
> [!NOTE]
>  Může také shromažďovat stejná data IntelliTrace pro webové aplikace a aplikace služby SharePoint spuštěna na vzdálených počítačích pomocí **agenta Microsoft Monitoring Agent** v **trasování** režimu.  
>   
>  Události související s výkonem v IntelliTrace data může shromažďovat spuštěním agenta v **monitorování** režimu. **Monitorování** režim má menší dopad na výkon než **trasování** režimu nebo **samostatného kolektoru IntelliTrace**. Agenta Microsoft Monitoring Agent změnit prostředí cílového systému, když je nainstalovaná. Zobrazit [pomocí agenta Microsoft Monitoring Agent](../debugger/using-the-microsoft-monitoring-agent.md).  
  
 **Požadavky**  
  
- Rozhraní .NET framework 3.5, 4 nebo 4.5  
  
- Visual Studio Enterprise (ale ne Professional nebo Community edice) na vývojovém počítači nebo jiném počítači pro otevření souborů .iTrace  
  
  > [!NOTE]
  >  Ujistěte se, že chcete ukládat symbolu (.pdb) soubory. Chcete-li ladit pomocí nástroje IntelliTrace a krokovat kód, musíte mít odpovídající zdrojové soubory a soubory symbolů. Zobrazit [Diagnostika problémů po nasazení](../debugger/diagnose-problems-after-deployment.md).  
  
  **NEJČASTĚJŠÍ DOTAZY**  
  
- [Jaké aplikace fungují s kolektorem?](#WhatApps)  
  
- [Jak mám začít?](#GetStarted)  
  
- [Jak lze získat většinu dat bez zpomalení aplikace?](#Minimizing)  
  
- [Kde jinde lze získat IntelliTrace data?](#WhereElse)  
  
##  <a name="WhatApps"></a> Jaké aplikace fungují s kolektorem?  
  
-   Webové aplikace ASP.NET hostované v Internetové informační služby (IIS) verze 7.0, 7.5 a 8.0  
  
-   Aplikace služby SharePoint 2010 a SharePoint 2013  
  
-   Windows Presentation Foundation (WPF) a Windows Forms aplikací.  
  
##  <a name="GetStarted"></a> Jak mám začít?  
  
1.  [Instalace kolekce](#BKMK_Install_the_IntelliTrace_Stand_Alone_Collector)  
  
2.  [Nastavení oprávnění pro adresář kolekce](#ConfigurePermissionsRunningCollector)  
  
3.  [Instalace rutin prostředí PowerShell pro IntelliTrace ke shromažďování dat pro webové aplikace nebo aplikace služby SharePoint](#BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets)  
  
4.  [Nastavení oprávnění pro adresář souboru .iTrace](#BKMK_Create_and_Configure_a_Log_File_Directory)  
  
5.  [Shromažďování dat z webové aplikace nebo aplikace služby SharePoint](#BKMK_Collect_Data_from_IIS_Application_Pools)  
  
     -nebo-  
  
     [Shromažďování dat ze spravovaných aplikací](#BKMK_Collect_Data_from_Executables)  
  
6.  [Otevřete soubor .iTrace v sadě Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)  
  
##  <a name="BKMK_Install_the_IntelliTrace_Stand_Alone_Collector"></a> Instalace kolekce  
  
1. Na serveru vaší aplikace vytvořte adresář kolektoru, například: **C:\IntelliTraceCollector**  
  
2. Stáhněte si kolektor z webu Microsoft Download Center nebo z instalační složky sady Visual Studio 2103 s aktualizací Update 3. [IntelliTrace Collector for Visual Studio 2013 Update 4](https://www.microsoft.com/download/details.aspx?id=44909)::  
  
   - **Microsoft Download Center**:  
  
     1. Vedle položky **IntelliTraceCollector.exe**, zvolte **Stáhnout**.  
  
     2. Uložte IntelliTraceCollector.exe do adresáře kolektoru, například: **C:\IntelliTraceCollector**  
  
     3. Spusťte IntelliTraceCollector.exe. To vyextrahuje je extrahován soubor IntelliTraceCollection.cab.  
  
        \- nebo –  
  
   - **Visual Studio Instalační složka**:  
  
     1.  Zkopírujte soubor IntelliTraceCollection.cab z následující složky:  
  
          **.\Microsoft Visual Studio 12.0\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace\12.0.0**  
  
     2.  Vložte soubor IntelliTraceCollection.cab do adresáře kolektoru, například: **C:\IntelliTraceCollector**  
  
3. Rozbalte soubor IntelliTraceCollection.cab:  
  
   1.  Na serveru aplikace otevřete okno příkazového řádku jako správce.  
  
   2.  Přejděte do adresáře kolektoru, například: **C:\IntelliTraceCollector**  
  
   3.  Použití **rozbalte** příkaz, včetně tečky (**.**) na konci, a rozbalte soubor IntelliTraceCollection.cab:  
  
        `expand  /f:* IntelliTraceCollection.cab .`  
  
       > [!NOTE]
       >  Období (**.**) zachovává podsložky obsahující lokalizované plány sběru.  
  
##  <a name="ConfigurePermissionsRunningCollector"></a> Nastavení oprávnění pro adresář kolekce  
  
1.  Na serveru aplikace otevřete okno příkazového řádku jako správce.  
  
2.  Použít Windows **icacls** příkaz serveru poskytnout úplné oprávnění správce k adresáři kolektoru. Příklad:  
  
     `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\AdministratorID >* `":F`  
  
3.  Sběr dat pro webovou aplikaci nebo aplikaci služby SharePoint:  
  
    1.  Poskytněte uživateli, který bude spouštět rutiny prostředí IntelliTrace PowerShell, úplná oprávnění k adresáři kolektoru.  
  
         Příklad:  
  
         `icacls "C:\IntelliTraceCollector" /grant "` *\<Doména\ID_uživatele >* `":F`  
  
    2.  Udělte fondu aplikací pro webovou aplikaci nebo aplikaci služby SharePoint oprávnění číst a spouštět obsah adresáře kolektoru.  
  
         Příklad:  
  
        -   Pro webovou aplikaci v **DefaultAppPool** fondu aplikací:  
  
             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\DefaultAppPool":RX`  
  
        -   Pro aplikaci služby SharePoint ve **SharePoint - 80** fondu aplikací:  
  
             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\SharePoint - 80":RX`  
  
##  <a name="BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets"></a> Instalace rutin prostředí PowerShell pro IntelliTrace ke shromažďování dat pro webové aplikace nebo aplikace služby SharePoint  
  
1.  Ujistěte se, že je povolené prostředí PowerShell na serveru aplikace. Ve většině verzí systému Windows Server, můžete přidat tuto funkci **správce serveru** nástroje pro správu.  
  
     ![Přidání prostředí PowerShell pomocí Správce serveru](../debugger/media/intellitrace-servermanager-addpowershell.png "INTELLITRACE_ServerManager_AddPowerShell")  
  
2.  Instalace rutin prostředí PowerShell pro IntelliTrace.  
  
    1.  Otevřete příkazové okno Powershellu jako správce.  
  
        1.  Zvolte **Start**, **všechny programy**, **Příslušenství**, **prostředí Windows PowerShell**.  
  
        2.  Vyberte jednu z následujících kroků:  
  
            -   V 64bitových operačních systémech otevřete místní nabídku pro **prostředí Windows PowerShell**. Zvolte **spustit jako správce**.  
  
            -   Na 32bitové operační systémy, otevřete místní nabídku pro **prostředí Windows PowerShell (x86)**. Zvolte **spustit jako správce**.  
  
    2.  V příkazovém okně prostředí PowerShell, použijte **Import-Module** příkaz pro import **Microsoft.VisualStudio.IntelliTrace.PowerShell.dll**.  
  
         Příklad:  
  
         `Import-Module "C:\IntelliTraceCollector\Microsoft.VisualStudio.IntelliTrace.PowerShell.dll"`  
  
##  <a name="BKMK_Create_and_Configure_a_Log_File_Directory"></a> Nastavení oprávnění pro adresář souboru .iTrace  
  
1. Na serveru vaší aplikace vytvořte adresář souboru .iTrace, například: **C:\IntelliTraceLogFiles**  
  
   > [!NOTE]
   > - Aby se zabránilo zpomalení vaší aplikace, vyberte umístění na místním vysokorychlostním disku, který není velmi aktivní.  
   >   -   Soubory .iTrace a soubory kolektoru lze umístit na stejném místě. Ale pokud máte webovou aplikaci nebo aplikaci služby SharePoint, ujistěte se, že je toto umístění mimo adresář, který je hostitelem aplikace.  
   > 
   > [!IMPORTANT]
   > - Omezte adresář souboru .iTrace jenom na ty identity, které musí s kolektorem pracovat. Soubor .iTrace může obsahovat citlivé informace, jako jsou data od uživatelů, databáze, další zdrojová umístění a připojovací řetězce, protože nástroj IntelliTrace umí zaznamenat libovolná data předaná parametrům metod nebo jako návratové hodnoty.  
   >   -   Ujistěte se, že ty, kdo mohou otevírat soubory .iTrace jsou oprávněni prohlížet citlivá data. Při sdílení souborů .iTrace buďte opatrní. Pokud se ostatní uživatelé musí mít přístup, zkopírujte soubory do zabezpečeného sdíleného umístění.  
  
2. Pro webovou aplikaci nebo aplikaci služby SharePoint udělte jejich fondu aplikací úplná oprávnění k adresáři souboru .iTrace. Můžete použít Windows **icacls** příkaz % $n nebo pomocí Průzkumníka Windows (nebo Průzkumníka souborů).  
  
    Příklad:  
  
   - Nastavení oprávnění se Windows **icacls** příkaz:  
  
     - Pro webovou aplikaci v **DefaultAppPool** fondu aplikací:  
  
        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\DefaultAppPool":F`  
  
     - Pro aplikaci služby SharePoint ve **SharePoint - 80** fondu aplikací:  
  
        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\SharePoint - 80":F`  
  
       -nebo-  
  
   - Nastavení oprávnění pomocí Průzkumníka Windows (nebo Průzkumníka souborů):  
  
     1.  Otevřít **vlastnosti** pro adresář souboru .iTrace.  
  
     2.  Na **zabezpečení** kartě **upravit**, **přidat**.  
  
     3.  Ujistěte se, že **zabudované objekty zabezpečení** se zobrazí v **vyberte typ objektu** pole. Pokud ji má, možnost **typy objektů** a přidejte ji.  
  
     4.  Ujistěte se, že se zobrazí v místním počítači **z tohoto umístění** pole. Pokud ji má, možnost **umístění** ho změnit.  
  
     5.  V **zadejte názvy objektů k výběru** pole, přidat fond aplikací pro webovou aplikaci nebo aplikaci služby SharePoint.  
  
     6.  Zvolte **Kontrola názvů** přeložit název. Zvolte **OK**.  
  
     7.  Ujistěte se, že má fond aplikací **úplné řízení**.  
  
##  <a name="BKMK_Collect_Data_from_IIS_Application_Pools"></a> Shromažďování dat z webové aplikace nebo aplikace služby SharePoint  
  
1.  Pokud chcete začít, shromažďování dat, otevřete příkazové okno Powershellu jako správce a spuštěním tohoto příkazu:  
  
     `Start-IntelliTraceCollection` `"` *\<ApplicationPool >* `"`  *\<PathToCollectionPlan >*  *\<FullPathToITraceFileDirectory >*  
  
    > [!IMPORTANT]
    >  Po spuštění tohoto příkazu zadejte **Y** potvrďte, že chcete zahájit shromažďování data.  
  
     Chcete-li například shromažďovat data z aplikace služby SharePoint ve **SharePoint - 80** fondu aplikací:  
  
     `Start-IntelliTraceCollection "SharePoint - 80" "C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogFiles"`  
  
    |||  
    |-|-|  
    |*ApplicationPool*|Název fondu aplikací, kde běží aplikace|  
    |*PathToCollectionPlan*|Cesta k plánu sběru, soubor .xml konfigurující nastavení kolektoru.<br /><br /> Můžete zadat plán dodávaný spolu s kolektorem. Následující plány fungují pro webové aplikace a aplikace služby SharePoint:<br /><br /> -plán collection_plan.ASP.NET.default.xml<br />     Shromažďuje pouze události IntelliTrace a události služby SharePoint, včetně výjimek, volání databáze a požadavky na webový server.<br />-collection_plan.ASP.NET.trace.xml<br />     Shromažďuje volání funkcí a všechna data v plánu collection_plan.ASP.NET.default.xml. Tento plán je vhodný pro podrobnou analýzu, ale může zpomalit vaši aplikaci více než plán collection_plan.ASP.NET.default.xml.<br /><br /> Chcete-li nedocházelo ke zpomalování vaší aplikace, přizpůsobte tyto plány nebo vytvořte vlastní plán. Z důvodů zabezpečení umístěte vlastní plány do stejného zabezpečeného umístění jako soubory kolektoru. Zobrazit [vytváření a přizpůsobení plánů kolekce IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=227871) a [jak lze získat nejvíce dat bez zpomalení aplikace?](#Minimizing) **Poznámka:** ve výchozím nastavení je maximální velikost souboru .iTrace 100 MB. Dosáhne-li soubor .iTrace tohoto limitu, odstraní kolektor nejstarší položky v souboru uvolnilo místo pro novější položky. Chcete-li tento limit změnit, upravte plán shromažďování `MaximumLogFileSize` atribut. <br /><br /> *Kde lze najít lokalizované verze těchto plánů shromažďování dat?*<br /><br /> Lokalizované plány lze najít v podsložkách kolektoru.|  
    |*FullPathToITraceFileDirectory*|Úplná cesta k adresáři souboru .iTrace. **Poznámka k zabezpečení:** zadat úplnou cestu, nikoli relativní cestu.|  
  
     Kolektor se připojí k fondu aplikací a spustí shromažďování dat.  
  
     *V tuto chvíli, otevřete soubor .iTrace?* Ne, soubor je během shromažďování dat uzamčen.  
  
2.  Reprodukujte problém.  
  
3.  K vytvoření snímku ze souboru .iTrace, použijte následující syntaxi:  
  
     `Checkpoint-IntelliTraceCollection` `"` *\<ApplicationPool >* `"`  
  
4.  Pokud chcete zkontrolovat stav shromažďování, použijte následující syntaxi:  
  
     `Get-IntelliTraceCollectionStatus`  
  
5.  Chcete-li zastavit shromažďování dat, použijte následující syntaxi:  
  
     `Stop-IntelliTraceCollection` `"` *\<ApplicationPool >* `"`  
  
    > [!IMPORTANT]
    >  Po spuštění tohoto příkazu zadejte **Y** potvrďte, že chcete shromažďování dat ukončit. Jinak kolektor může pokračovat ve shromažďování dat, iTrace soubor zůstane uzamčen nebo soubor nemusí obsahovat žádná užitečná data.  
  
6.  [Otevřete soubor .iTrace v sadě Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)  
  
##  <a name="BKMK_Collect_Data_from_Executables"></a> Shromažďování dat ze spravovaných aplikací  
  
1.  Chcete-li spustit aplikaci a shromažďování dat ve stejnou dobu, použijte následující syntaxi:  
  
     *\<FullPathToIntelliTraceCollectorExecutable>* `\IntelliTraceSC.exe launch /cp:` *\<PathToCollectionPlan>* `/f:` *\<FullPathToITraceFileDirectoryAndFileName>* *\<PathToAppExecutableFileAndFileName>*  
  
     Například pro shromažďování dat z aplikace s názvem **MyApp**:  
  
     `C:IntelliTraceCollectorIntelliTraceSC.exe launch /cp:"C:IntelliTraceCollectorcollection_plan.ASP.NET.default.xml" /f:"C:IntelliTraceLogFilesMyApp.itrace" "C:MyAppMyApp.exe"`  
  
    |||  
    |-|-|  
    |*FullPathToIntelliTraceCollectorExecutable*|Úplná cesta ke spustitelnému souboru kolektoru IntelliTraceSC.exe|  
    |*PathToCollectionPlan*|Cesta k plánu sběru, soubor .xml konfigurující nastavení kolektoru.<br /><br /> Můžete zadat plán dodávaný spolu s kolektorem. Následující plány fungují pro spravované aplikace:<br /><br /> -plán collection_plan.ASP.NET.default.xml<br />     Shromažďuje jenom události IntelliTrace, včetně výjimek, volání databáze a požadavky na webový server.<br />-collection_plan.ASP.NET.trace.xml<br />     Shromažďuje volání funkcí a všechna data v plánu collection_plan.ASP.NET.default.xml. Tento plán je vhodný pro podrobnou analýzu, ale může zpomalit vaši aplikaci více než plán collection_plan.ASP.NET.default.xml.<br /><br /> Chcete-li nedocházelo ke zpomalování vaší aplikace, přizpůsobte tyto plány nebo vytvořte vlastní plán. Z důvodů zabezpečení umístěte vlastní plány do stejného zabezpečeného umístění jako soubory kolektoru. Zobrazit [vytváření a přizpůsobení plánů kolekce IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=227871) a [jak lze získat nejvíce dat bez zpomalení aplikace?](#Minimizing) **Poznámka:** ve výchozím nastavení je maximální velikost souboru .iTrace 100 MB. Dosáhne-li soubor .iTrace tohoto limitu, odstraní kolektor nejstarší položky v souboru uvolnilo místo pro novější položky. Chcete-li tento limit změnit, upravte plán shromažďování `MaximumLogFileSize` atribut. <br /><br /> *Kde lze najít lokalizované verze těchto plánů shromažďování dat?*<br /><br /> Lokalizované plány lze najít v podsložkách kolektoru.|  
    |*FullPathToITraceFileDirectoryAndFileName*|Úplná cesta k adresáři souboru .iTrace a název souboru .iTrace **.itrace** rozšíření. **Poznámka k zabezpečení:** zadat úplnou cestu, nikoli relativní cestu.|  
    |*PathToAppExecutableFileAndFileName*|Cesta a název souboru spravované aplikace|  
  
2.  Zastavte shromažďování dat ukončením aplikace.  
  
3.  [Otevřete soubor .iTrace v sadě Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)  
  
##  <a name="BKMK_View_IntelliTrace_Log_Files"></a> Otevřete soubor .iTrace v sadě Visual Studio Enterprise  
  
> [!NOTE]
>  Chcete-li ladit pomocí nástroje IntelliTrace a krokovat kód, musíte mít odpovídající zdrojové soubory a soubory symbolů. Zobrazit [Diagnostika problémů po nasazení](../debugger/diagnose-problems-after-deployment.md).  
  
1.  Přesunout soubor .iTrace nebo ho zkopírujte do počítače s Visual Studio Enterprise (ale ne Professional nebo Community edice).  
  
2.  Poklikejte na soubor .iTrace mimo sadu Visual Studio, nebo otevřete soubor v rámci sady Visual Studio.  
  
     Sada Visual Studio zobrazí **IntelliTrace – Souhrn** stránky. Ve většině částí lze prohlížet události nebo jiné položky, zvolte položku a začít ladit nástrojem IntelliTrace v okamžiku, kde a kdy k události došlo. Zobrazit [použití uložených dat řešení IntelliTrace](../debugger/using-saved-intellitrace-data.md).  
  
    > [!NOTE]
    >  Chcete-li ladit pomocí nástroje IntelliTrace a krokovat kód, musíte mít odpovídající zdrojové soubory a soubory na svém vývojovém počítači symbolů. Zobrazit [Diagnostika problémů po nasazení](../debugger/diagnose-problems-after-deployment.md).  
  
##  <a name="Minimizing"></a> Jak lze získat většinu dat bez zpomalení aplikace?  
 Nástroj IntelliTrace dokáže shromáždit velké množství dat, takže dopad na výkon aplikace závisí na data, která nástroj IntelliTrace shromažďuje a typu kódu, který analyzuje. Zobrazit [optimalizace kolekce IntelliTrace na provozních serverech](http://go.microsoft.com/fwlink/?LinkId=255233).  
  
 Tady jsou některé způsoby, jak získat většinu dat bez zpomalení vaší aplikace:  
  
- Spuštění kolektoru, pouze pokud si myslíte, že dojde k nějakému problému, nebo pokud dokážete problém reprodukovat.  
  
   Spustit shromažďování, reprodukujte problém a poté shromažďování zastavte. Otevřete soubor .iTrace v sadě Visual Studio Enterprise a prozkoumejte data. Zobrazit [otevřete soubor .iTrace v sadě Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files).  
  
- Webových aplikací a aplikací služby SharePoint kolektor zaznamenává data pro každou aplikaci, která sdílí určený fond aplikací. To může zpomalit jakékoli aplikaci, která sdílí stejný fond aplikací, i když můžete zadat pouze moduly pro jednotlivé aplikace v plánu shromažďování.  
  
   Aby kolektor zpomalil ostatní aplikace, hostujte každou aplikaci v jejím vlastním fondu aplikací.  
  
- Zkontrolujte události v plánu shromažďování, pro které nástroj IntelliTrace shromažďuje data. Upravte plán shromažďování a zakažte události, které nejsou důležité nebo vás nezajímají.  
  
   Chcete-li zakázat událost, nastavte `enabled` atribut pro `<DiagnosticEventSpecification>` elementu `false`:  
  
   `<DiagnosticEventSpecification enabled="false">`  
  
   Pokud `enabled` atribut neexistuje, je událost povolena.  
  
   *Jak to zlepší výkon?*  
  
  -   Zakázáním událostí, které nejsou relevantní pro danou aplikaci, můžete zkrátit dobu spouštění. Například zakažte události pracovního postupu Windows pro aplikace, které nepoužívají Windows Workflow.  
  
  -   Zakázáním událostí registru pro aplikace, které přístup k registru, ale nemají problémy s nastavením registru můžete zvýšit rychlost spouštění i výkon.  
  
- Zkontrolujte moduly v plánu shromažďování, pro které nástroj IntelliTrace shromažďuje data. Upravte plán kolekce umožňuje zahrnout pouze moduly, které vás zajímají:  
  
  1. Otevřete plán shromažďování. Najít `<ModuleList>` elementu.  
  
  2. V `<ModuleList>`, nastavte `isExclusionList` atribut `false`.  
  
  3. Použití `<Name>` – element pro určení každého modulu s některou z následujících akcí: název souboru, Řetězcová hodnota pro zahrnutí každého modulu, jehož název obsahuje daný řetězec, nebo veřejný klíč.  
  
     Například pro shromažďování dat z právě hlavního webového modulu nebo webové aplikace Fabrikam Fiber, vytvořte seznam podobný následujícímu:  
  
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
  
   *Jak to zlepší výkon?*  
  
   To snižuje množství informací o volání metody a dalších instrumentačních dat, která nástroj IntelliTrace shromažďuje při spuštění a spuštění aplikace. Tato data vám umožní:  
  
  - Krokovat kód po shromáždění dat.  
  
  - Zkontrolujte hodnoty předané a vrácené z volání funkce.  
  
    *Proč namísto toho Nevyloučit moduly?*  
  
    Ve výchozím nastavení plány shromažďování dat vylučují moduly nastavením `isExclusionList` atribut `true`. Ale vyloučení modulů však může stále dojít shromažďování dat z modulů, které nesplňují kritéria v seznamu a vás nemusejí zajímat, například moduly třetích stran nebo open source.  
  
- *Existuje všechna data, která nástroj IntelliTrace neshromažďuje?*  
  
   Ano, pro snížení vlivu na výkon omezuje nástroj IntelliTrace shromažďování dat na hodnoty primitivních datových typů předávané a vracené z metod a na hodnoty primitivních datových typů v polích objektů nejvyšší úrovně předávané a vracené z metod.  
  
   Předpokládejme například, že máte `AlterEmployee` podpis metody, která přijímá celočíselné `id` a `Employee` objekt `oldemployee`:  
  
   `public Employee AlterEmployee(int id, Employee oldemployee)`  
  
   `Employee` Typ má následující atributy: `Id`, `Name`, a `HomeAddress`. Existuje vztah přidružení mezi `Employee` a `Address` typu.  
  
   ![Vztah mezi zaměstnanci a adresa](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")  
  
   Kolektor zaznamenává hodnoty `id`, `Employee.Id`, `Employee.Name` a `Employee` objekt vrácený z `AlterEmployee` metody. Kolektor však nezaznamenává informace o `Address` objektu, než zda měl hodnotu null nebo ne. Kolektor také nezaznamenává data o místních proměnných v `AlterEmployee` metoda Pokud jiné metody nepoužívají tyto místní proměnné jako parametry v tomto okamžiku jsou zaznamenávány jako parametry metod.  
  
##  <a name="WhereElse"></a> Kde jinde lze získat IntelliTrace data?  
  
-   V relaci v sadě Visual Studio Enterprise ladění IntelliTrace, zobrazit [funkce IntelliTrace](../debugger/intellitrace-features.md).  
  
-   Z testovací relace v nástroji Microsoft Test Manager, najdete v článku [postupy: shromažďování dat technologie IntelliTrace pro pomáhají ladění složitých problémů](~/E:/Repos/visualstudio-docs-pr/docs/test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).  
  
## <a name="where-can-i-get-more-information"></a>Kde lze získat další informace?  
 [Použití uložených dat řešení IntelliTrace](../debugger/using-saved-intellitrace-data.md)  
  
 [IntelliTrace](../debugger/intellitrace.md)  
  
### <a name="blogs"></a>Blogy  
 [Použití samostatného sběrače IntelliTrace vzdáleně](http://go.microsoft.com/fwlink/?LinkId=262277)  
  
 [Vytvoření a úprava plánů kolekce IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=227871)  
  
 [Optimalizace kolekce IntelliTrace na provozních serverech](http://go.microsoft.com/fwlink/?LinkId=255233)  
  
 [Visual Studio ALM + TFS Blog](http://go.microsoft.com/fwlink/?LinkID=201340)  
  
### <a name="forums"></a>Diskuzní fóra  
 [Ladicí program sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
### <a name="videos"></a>Videa  
 [Video pro kanál 9: shromažďování a analýza dat IntelliTrace](http://go.microsoft.com/fwlink/?LinkID=251851)





