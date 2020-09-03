---
title: Přenos, migrace a upgrade projektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
caps.latest.revision: 108
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 3361b04900e549d037338abfba0911b232c9e1bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919092"
---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Port, migrace a upgrade projektů sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v [referenčních informacích k migraci projektů a upgradu pro Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).

Pokud zvažujete, zda byste měli přejít na novější verzi sady Visual Studio, můžete pomocí tohoto článku zjistit, jaká řešení, projekty, soubory a další prostředky, které jste vytvořili v Visual Studio 2013, Visual Studio 2012 nebo Visual Studio 2010 SP1, budou spouštěny beze změny v Visual Studio 2013 a sady Visual Studio 2015. Nebo jste se mohli setkat s touto stránkou, pokud se při pokusu o otevření projektu, který není podporován ve verzi sady Visual Studio, který jste otevřeli v systému, nebo který vyžaduje sadu SDK nebo rozšíření, jako je například sada Azure SDK pro .NET, objevila chybová zpráva.

Mnoho široce používaných prostředků se chová stejně jako v aplikaci Visual Studio 2015, Visual Studio 2013 a dvou předchozích verzích. Například v aplikaci Visual Studio 2015 můžete otevřít projekt, který byl vytvořen v Visual Studio 2013 nebo Visual Studio 2012, změnit ho a znovu ho otevřít v aplikaci Visual Studio 2015. Vaše změny jsou trvalé a projekt se chová stejně jako v dřívější verzi. Totéž platí pro mnoho aktiv, které byly vytvořeny v aplikaci Visual Studio 2010 SP1.

V případě Visual Basic nepředstavila aplikace Visual Studio 2015 žádné změny, které zabrání aplikaci Visual Basic vytvořenou v Visual Studio 2013 kompilaci. Chování aplikace Visual Basic, které se znovu zkompiluje pomocí sady Visual Studio 2015, neovlivní chování za běhu.

Pokud používáte sadu Visual Studio 2015 společně s Visual Studio 2013, sadou Visual Studio 2012 nebo sadou Visual Studio 2010 SP1, můžete vytvářet a upravovat projekty a soubory v některé z těchto verzí. Můžete přenášet projekty a soubory mezi verzemi tak dlouho, dokud nepřidáte funkce, které nejsou podporovány v jedné nebo více verzích.

## <a name="projects"></a><a name="project"></a> Projekty

Následující seznam popisuje podporu v aplikaci Visual Studio 2015 a Visual Studio 2013 pro projekty, které byly vytvořeny v aplikaci Visual Studio 2012 nebo Visual Studio 2010 SP1. Tento seznam vám pomůže určit, zda můžete otevřít projekt "tak, jak je" v aplikaci Visual Studio 2015, Visual Studio 2013, Visual Studio 2012 nebo Visual Studio 2010 SP1 nebo zda je nutné jej změnit, aby se zajistila kompatibilita.

|Typ projektu|Kompatibilita|
|---------------------|-------------------|
|Aplikace Univerzální platforma Windows|Pokud chcete nainstalovat nástroje pro univerzální aplikace pro Windows, vyberte v instalačním programu sady Visual Studio možnost **vlastní** nebo **Upravit**a pak vyberte **Nástroje pro vývoj univerzálních aplikací pro Windows**.<br /><br /> Vývoj aplikací Univerzální platforma Windows (UWP) pro Windows 10 je podporován pouze v systému Visual Studio 2015 ve Windows 10 nebo [!INCLUDE[win81](../includes/win81-md.md)] .|
|Aplikace pro Windows Store|Vývoj aplikací pro Windows Store, včetně univerzálních aplikací, které cílí na Windows 8.1 i Windows Phone 8,1, se podporuje v [!INCLUDE[win81](../includes/win81-md.md)] systémech a Windows 10. Existující [!INCLUDE[win8](../includes/win8-md.md)] projekty mohou být nadále obsluhované, ale [!INCLUDE[win8](../includes/win8-md.md)] nelze vytvořit nové projekty. [!INCLUDE[win81](../includes/win81-md.md)] projekty mohou záviset pouze na určitých typech odkazů. Další informace naleznete v tématu [Správa odkazů v projektu](../ide/managing-references-in-a-project.md). **Poznámka:** [!INCLUDE[win81](../includes/win81-md.md)] projekty, které vytvoříte pomocí sady Visual Studio 2015 nebo Visual Studio 2013, nelze otevřít v aplikaci Visual Studio 2012.   Důvodem je, že [!INCLUDE[win81](../includes/win81-md.md)] projekty vytvořené pomocí sady Visual studio 2015 a Visual Studio 2013 cílit na tyto verze a Visual Studio 2012 podporuje pouze [!INCLUDE[win8](../includes/win8-md.md)] projekty, které cílí na [!INCLUDE[win8](../includes/win8-md.md)] .|
|[!INCLUDE[net_v451](../includes/net-v451-md.md)]|Můžete vytvořit a použít tyto projekty v sadě Visual Studio 2015 a Visual Studio 2013 po instalaci příslušného sady multi-targeting pack. Tyto projekty nejsou podporovány v aplikaci Visual Studio 2010 SP1.|
|[!INCLUDE[net_v45](../includes/net-v45-md.md)]|Tyto projekty lze vytvořit a otevřít v aplikaci Visual Studio 2015, Visual Studio 2013 a Visual Studio 2012, ale ne v aplikaci Visual Studio 2010 SP1.|
|BizTalk|Projekty BizTalk serveru nejsou kompatibilní se sadou Visual Studio 2015 nebo Visual Studio 2013.|
|Aplikace nebo knihovna tříd technologie Silverlight 4 v jazyce C# nebo Visual Basic|Pokud chcete, aby aplikace Visual Studio automaticky aktualizovala projekt, můžete ji otevřít buď v Visual Studio 2013, nebo v aplikaci Visual Studio 2012.|
|Webový formulář nebo formulář Windows v jazyce C# nebo Visual Basic|Projekt lze otevřít v Visual Studio 2013 a v aplikaci Visual Studio 2012.|
|Visual Basic 6 a Visual C++ 6|Visual Studio 2012 a Visual Studio 2013 nepodporují ladění aplikací vytvořených pomocí Visual Basic 6 nebo Visual C++ 6; Chcete-li ladit tyto aplikace, použijte dřívější verze aplikace Visual Studio.|
|Programový test UI|Pokud chcete, aby aplikace Visual Studio automaticky aktualizovala projekt, můžete ji otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|F#|Pokud aplikaci Visual Studio povolíte upgrade projektu, který byl vytvořen v aplikaci Visual Studio 2010 SP1, můžete jej otevřít v Visual Studio 2013 a Visual Studio 2012. Projekt Silverlight, který byl vytvořen ve starší verzi sady Visual Studio, však nelze upgradovat na Visual Studio 2013. Místo toho je nutné vytvořit projekt Silverlight v Visual Studio 2013 a potom do něj zkopírovat kód. Projekty Silverlight, které vytvoříte v Visual Studio 2013 cílovém programu Silverlight 5.|
|LightSwitch|Pokud aplikaci Visual Studio povolíte automatické upgrade projektu, můžete ji otevřít pouze v Visual Studio 2013.|
|Mezipaměť místní databáze|V Visual Studio 2013 není obsažena Šablona místní mezipaměti databáze a dialogové okno **Konfigurace synchronizace dat** . Můžete použít Visual Studio 2013 k otevření a spuštění projektů, které byly vytvořeny v [!INCLUDE[vs2010](../includes/vs2010-md.md)] případě, že je nainstalována služba Microsoft Synchronization Services v 1.0, ale pokud je chcete aktualizovat v Visual Studio 2013, je nutné ručně provést všechny změny v kódu. Jako alternativu můžete dál používat [!INCLUDE[vs2010](../includes/vs2010-md.md)] k údržbě a aktualizaci těchto projektů.  Pro nový vývoj je třeba použít nový synchronizační model, který je poskytován rámcem Microsoft Sync Framework. Informace naleznete v tématu [středisko pro vývojáře architektury Microsoft Sync Framework](https://msdn.microsoft.com/sync/default) .|
|Rámec MVC (Model View Controller)|Visual Studio 2010 SP1 podporuje pouze MVC 2 a MVC 3, Visual Studio 2012 podporuje pouze MVC 3 a MVC 4 a Visual Studio 2013 podporuje pouze MVC 4. Informace o tom, jak automaticky upgradovat z MVC 2 na MVC 3, najdete v tématu [ASP.NET MVC 3 Application upgrade](https://aspnet.codeplex.com/releases/view/59008). Informace o tom, jak ručně upgradovat z MVC 2 na MVC 3, najdete v tématu [upgrade projektu ASP.NET MVC 2 na ASP.NET MVC 3 Tools Update](https://aspnet.codeplex.com/releases/view/59008). Informace o tom, jak ručně upgradovat z MVC3 na MVC 4, najdete v tématu [upgrade projektu ASP.NET MVC 3 na ASP.NET MVC 4](/aspnet/whitepapers/mvc4-release-notes). Pokud je projekt cílen na rozhraní .NET Framework 3.5 SP1, je nutné cíl změnit na rozhraní .NET Framework 4.|
|Modelování|Pokud chcete, aby aplikace Visual Studio automaticky aktualizovala projekt, můžete ji otevřít v Visual Studio 2013, Visual Studio 2012 nebo Visual Studio 2010 SP1.<br /><br /> Když služba Team Foundation sestaví modelovací projekt, pokusí se ověřit vrstvy projektu. V Visual Studio 2013 Team Foundation Build nemůže ověřit vrstvy pro projekt modelování, který byl vytvořen v aplikaci Visual Studio 2010 SP1. V rámci sady Visual Studio 2010 SP1 však Team Foundation Build může ověřit vrstvy v projektu modelování, který byl vytvořen v Visual Studio 2013.|
|Ladění MPI nebo clusteru|Pokud je stejná verze modulu runtime nebo nástrojů nainstalována na počítačích se systémem Visual Studio 2013, Visual Studio 2012 nebo Visual Studio 2010 SP1, můžete tento projekt otevřít ve všech třech verzích.|
|Instalační program MSI (.vdproj)|Tento projekt nelze otevřít v Visual Studio 2013, protože nepodporuje tento typ projektu. Doporučujeme použít nástroj InstallShield Limited Edition (ISLE) pro systém Visual Studio; jedná se o řešení pro nasazení, které je zdarma a přímo podporuje většinu operačních systémů Windows a běhy aplikací. Program ISLE lze rovněž použít pro import dat a nastavení z projektů instalačního programu systému Visual Studio. .|
|Sada Office 2007 VSTO|Pokud upgradujete projekt na cílovou sadu Office 2013 a .NET Framework 4, můžete tento projekt otevřít v Visual Studio 2013, Visual Studio 2012 nebo Visual Studio 2010 SP1.|
|Office 2010 VSTO|Pokud je projekt cílen na .NET Framework 4, můžete jej otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1. Všechny ostatní projekty vyžadují jednosměrnou aktualizaci.|
|Bohaté internetové aplikace|Pokud upgradujete projekt, můžete jej otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|SharePoint 2007|Tento projekt nelze otevřít v Visual Studio 2013. Pokud však projekt upgradujete ručně na SharePoint 2010, můžete jej otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1. Další informace o tom, jak upgradovat SharePoint 2007, najdete v tématu [migrace ze sharepointu 2007 na službu sharepoint 2010 pro](https://channel9.msdn.com/Blogs/matthijs/Migrating-from-SharePoint-2007-to-SharePoint-2010-for-the-IT-Pro) Nástroj pro migraci IT pro a [SharePoint Enterprise Search pro SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ee556856(v%3Doffice.14)).|
|SharePoint 2010|Projekt lze otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|SketchFlow|Pokud aplikaci Visual Studio povolíte upgrade projektu na verzi WPF 4.5/Silverlight 5, můžete jej otevřít v aplikaci Visual Studio 2012 a Visual Studio 2013.|
|Databáze [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)]|Projekt lze otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1. Pokud máte soubor databáze (. mdf), který byl vytvořen v dřívější verzi SQL Server, je nutné jej upgradovat na, aby bylo [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] možné jej použít s SQL Server Express LocalDB, ale databáze již není kompatibilní s dřívějšími verzemi SQL Server. Pokud upgrade neuděláte, můžete pokračovat v práci s databází v Visual Studio 2013 tím, že nainstalujete a použijete [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] ve stejném počítači. Další informace najdete v tématu [upgrade souborů. mdf](../data-tools/upgrade-dot-mdf-files.md).|
|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)]Je-li v počítačích se systémem Visual Studio 2013, Visual studio 2012 a Visual studio 2010 SP1 nainstalován expresní, můžete projekt otevřít ve všech třech verzích.|
|Projekt sestavy systému SQL Server|Projekt lze otevřít v Visual Studio 2013 a v aplikaci Visual Studio 2012. Pouze pro místní režim (tj. Pokud není připojen k SQL Server) nezískáte prostředí pro ovládací prvky, které jsou spojeny s prohlížečem v nástroji [!INCLUDE[vs2010](../includes/vs2010-md.md)] , ale projekt bude pracovat správně za běhu. **Upozornění:**  Pokud přidáte funkci, která je specifická pro Visual Studio 2013, schéma sestavy bude automaticky upgradováno a projekt již nebude možné otevřít v aplikaci Visual Studio 2012.|
|Testování částí|[!INCLUDE[TCMext](../includes/tcmext-md.md)]K otevření testů, které byly vytvořeny v některé z těchto verzí, můžete použít v Visual Studio 2013, Visual studio 2012 a Visual studio 2010 SP1.|
|Visual C++|Můžete použít Visual Studio 2013 k otevření projektu C++, který byl vytvořen v aplikaci Visual Studio 2012 nebo Visual Studio 2010 SP1. Chcete-li použít prostředí Visual Studio 2013 Build pro sestavení projektu, který byl vytvořen v aplikaci Visual Studio 2012, je nutné mít nainstalovány obě verze sady Visual Studio do stejného počítače. Další informace naleznete v tématu [How to: Upgrade Visual C++ Projects to Visual Studio 2015](../porting/how-to-upgrade-visual-cpp-projects-to-visual-studio-2015.md) and [Visual C++ Transport and Upgrade Guide](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb).|
|Web systému Visual Studio 2010|Pokud aplikaci Visual Studio povolíte automatické upgrade projektu, můžete ji otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|Databáze systému Visual Studio 2010 (.dbproj)|Pokud převedete projekt na projekt databáze nástrojů SQL Server Data Tools, můžete jej otevřít v Visual Studio 2013. Visual Studio 2013 ale tyto artefakty nepodporuje:<br /><br /> -testy jednotek<br />– plány generování dat<br />-soubory porovnání dat<br />– rozšíření vlastních pravidel pro statickou analýzu kódu<br />-Server. sqlsettings<br />-. Sqlcmd – soubory<br />– vlastní rozšíření nasazení<br />-Částečné projekty (. Files)<br /><br /> Po instalaci datových nástrojů systému SQL Server lze projekt otevřít v systému Visual Studio 2010 SP1 po převodu. Další informace najdete v tématu [Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx).|
|Nástroje Visual Database Tools sady Visual Studio 2010|Tento projekt můžete otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|Visual Studio Lab Management|[!INCLUDE[TCMext](../includes/tcmext-md.md)]K otevření prostředí, která byla vytvořena v některé z těchto verzí, můžete použít, Visual Studio 2013, Visual studio 2012 a Visual studio 2010 SP1. Verze programu Microsoft Test Manager však musí před vytvořením prostředí odpovídat verzi služby Team Foundation Server.|
|Makro systému Visual Studio|Tento projekt nelze otevřít v Visual Studio 2013, protože nepodporuje typ projektu.|
|Visual Studio SDK/VSIX|Po upgradu projektu sady Visual Studio SDK na Visual Studio 2013 jej nelze otevřít v sadě Visual Studio 2012. Další informace naleznete v tématu [How to: migrace rozšiřujících projektů do sady Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md).|
|Microsoft Azure nástroje pro Visual Studio|Pokud používáte Microsoft Azure Tools for Visual Studio verze 2,1, můžete projekt otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1. Pro projekty, které jsou cíleny na starší verze, pokud aplikaci Visual Studio povolíte upgrade projektu na verzi 2,1, můžete jej otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|Windows Communication Foundation, Windows Presentation Foundation|Tento projekt můžete otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|Windows Mobile|Tento projekt nelze otevřít v Visual Studio 2013, protože nepodporuje typ projektu.|
|Windows Phone 7,1|Pokud aplikaci Visual Studio povolíte upgrade projektu na Windows Phone 8,0, můžete jej otevřít v aplikaci Visual Studio 2012 a Visual Studio 2013.|
|Další|Můžete otevřít většinu dalších typů projektů v aplikaci Visual Studio 2012, Visual Studio 2013 a Visual Studio 2010 SP1.|
|Webové servery FrontPage|Tento projekt nelze otevřít v Visual Studio 2013, protože nepodporuje typ projektu.|
|Přenosná knihovna tříd|Pokud chcete, aby aplikace Visual Studio automaticky aktualizovala projekt, můžete ji otevřít v Visual Studio 2013, Visual Studio 2012 nebo Visual Studio 2010 SP1.<br /><br /> – Projekty cílené na Silverlight 4 budou cílit na Silverlight 5.<br />-Projekty cílené Windows Phone 7,0 nebo Windows Phone 7,5 budou cílem Windows Phone 8.<br />– Projekty cílené na Xbox 360 již nebudou cílem Xbox 360.|
|Projekty Azure, jako jsou projekty cloudových služeb (rozšíření. soubor ccproj) a projekty Azure Resource Manager (projekty nasazení v cloudu) s příponou. deployproj|Chcete-li otevřít tyto typy projektů, nejprve nainstalujte [sadu Azure SDK pro .NET](https://azure.microsoft.com/downloads/)a pak otevřete projekt.|

## <a name="troubleshooting-project-compatibility-issues"></a>Řešení potíží s kompatibilitou projektu
 Tady je několik věcí, které můžete provést, když se projekt neotevře v aplikaci Visual Studio 2015 nebo Visual Studio 2013:

- Pokud se pokusíte otevřít projekt, který není podporován v aplikaci Visual Studio 2015 nebo Visual Studio 2013 a pro které není nainstalována přidružená verze sady Visual Studio, může se zobrazit zpráva, že typ projektu není podporován, a typ projektu může být uveden v dialogovém okně **Revize projektu a změny řešení** v části **nepodporované projekty**. Chcete-li tento problém vyřešit, otevřete stránku programy a funkce v **Ovládacích panelech**systému Windows, vyberte možnost **Visual Studio**a pak zvolte možnost **změnit**, **opravit**. Následně lze chybějící verzi nainstalovat.

- Pokud se pokusíte otevřít projekt aplikace klasické pracovní plochy v systému [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] , dojde k chybě a zobrazí se jedna z následujících zpráv: "Tato edice sady Visual Studio podporuje pouze [!INCLUDE[win81](../includes/win81-md.md)] aplikace" nebo "Tento projekt není kompatibilní s aktuální edicí sady Visual Studio". [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] je omezen na vývoj, testování a nasazení aplikací pro Windows Store určených pro Windows 8.1. K otevření projektu aplikace klasické pracovní plochy je nutné použít edici systému Visual Studio, která tento typ projektu podporuje.

   Další informace o edicích sady Visual Studio najdete v tématu [Microsoft Visual Studio Products](https://visualstudio.microsoft.com/products/) .

- Pokud se pokusíte otevřít projekt aplikace pro Windows Store na [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] ploše, dojde k chybě. [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Plocha se nedá použít k vytváření aplikací pro Windows Store. Pokud chcete sestavovat aplikace pro Windows Store, můžete také nainstalovat [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] . Nebo pokud chcete vyvíjet aplikace pro všechny platformy Microsoft a web, vyzkoušejte sadu Visual Studio Professional 2013.

- Pokud projekt vyžaduje funkce, které jsou specifické pro Visual Studio 2013, nelze jej otevřít v dřívější verzi.

- Pokud používáte sadu Visual Studio 2012 a chcete otevřít projekt, který byl vytvořen v Visual Studio 2013, může být možné přizpůsobit systém projektu tak, aby zahrnoval funkce Visual Studio 2013. Další informace o tom, jak to provést, najdete v tématu [vytváření vlastních projektů s podporou verzí](../misc/making-custom-projects-version-aware.md).

  Další informace o řešení problémů najdete v článku znalostní báze Knowledge Base pro [Visual Studio 2013](https://support.microsoft.com/help/2863286/roundtrip-issues-for-visual-studio-2012-and-visual-studio-2013-preview) .

## <a name="files"></a><a name="file"></a> Spis

Následující seznam určuje, zda Visual Studio 2013 podporuje jednotlivé typy souborů, zda lze soubor otevřít v aplikaci Visual Studio 2012 a Visual Studio 2010 SP1 a zda je nutné jej upravit, aby bylo zajištěno kompatibility.

|Typ souboru|Kompatibilita|
|------------------|-------------------|
|AppManifest, Inbrowsersettings, OutOfBrowserSettings (soubory .xml)|Tyto soubory lze otevřít v aplikaci Visual Studio 2012, Visual Studio 2013 a Visual Studio 2010 SP1.|
|Schémata plochých souborů BizTalk|Tato schémata můžete přidat do projektu BizTalk 2013 v Visual Studio 2013. Pokud chcete použít Visual Studio 2013 s projekty BizTalk 2010, které mají schémata plochého souboru, nainstalujte BizTalk 2013 na počítači, který má Visual Studio 2013. Při prvním otevření projektu BizTalk 2010 je automaticky upgradován na systém BizTalk 2013 nebo Visual Studio 2013 projektový systém.|
|Soubory definice sestav klienta (.rdlc)|Tyto soubory můžete otevřít v Visual Studio 2013 a schéma se automaticky upgraduje, pokud přidáte Visual Studio 2013 funkce a ovládací prvky.|
|Množiny pravidel analýzy kódu|Tyto soubory lze otevřít v aplikaci Visual Studio 2012, Visual Studio 2013 a Visual Studio 2010 SP1.|
|Soubory balíčků aplikací na úrovni datové vrstvy|Tyto soubory můžete otevřít v Visual Studio 2013, pokud jsou ve verzi 2,0 nebo 2,5.|
|Soubory s výpisem paměti ladicího programu|Tyto soubory lze otevřít v aplikaci Visual Studio 2012, Visual Studio 2013 a Visual Studio 2010 SP1.|
|Soubory diagramů jazyka přímého značení grafů (DGML)|Tyto soubory můžete otevřít v aplikaci Visual Studio 2012, Visual Studio 2013 a Visual Studio 2010 SP1 beze změny souboru.|
|Soubory Entity Data Model (EDMX)|V Visual Studio 2013 můžete otevřít soubor EDMX, který cílí na .NET Framework 4,5 nebo .NET Framework 4 beze změny souboru.|
|Soubory sestav modulu Profiler|V aplikaci Visual Studio 2012 a Visual Studio 2013 můžete otevřít soubory sestav profileru (. vsp. vsps,. psess a. vspf). Soubory .vspx nelze v systému Visual Studio 2010 SP1 otevřít.|
|Soubor řešení (.suo)|Můžete použít Visual Studio 2013 k otevření souboru řešení, který byl vytvořen v aplikaci Visual Studio 2012 nebo Visual Studio 2010 SP1|
|SQL Server Compact Edition|Visual Studio 2013 nepodporuje edici SQL Server Compact.|
|Soubory SQLX|Chcete-li otevřít tyto soubory v Visual Studio 2013, je nutné provést jednosměrný upgrade, nasadit soubor. sqlx v cílové verzi sady Visual Studio a poté znovu sestavit soubor ve formátu. DACPAC.|
|Soubory protokolu IntelliTrace z [!INCLUDE[vs2010](../includes/vs2010-md.md)]|Tyto soubory lze otevřít v aplikaci Visual Studio 2012, Visual Studio 2013 a Visual Studio 2010 SP1.|
|Soubory JavaScript Memory Analyzer (.diagsession)|Soubory vytvořené staršími verzemi sady Visual Studio lze zobrazit v Visual Studio 2013. V závislosti na shromažďovaných informacích se však soubory vytvořené v Visual Studio 2013 nemusí otevřít v aplikaci Visual Studio 2012 nebo Visual Studio 2010 SP1.|

## <a name="integration-assets"></a><a name="integration"></a> Prostředky integrace

Při použití klientů a serverů z různých verzí služby Visual Studio Team Foundation Server může dojít k problémům s kompatibilitou.

|Druh integrace|Kompatibilita|
|-------------------------|-------------------|
|Revize kódu a Má práce|Funkce revize kódu a moje práce nebude fungovat, pokud připojíte klienta nástroje [!INCLUDE[esprfound](../includes/esprfound-md.md)] k [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] .|
|[!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]|64 prostředí, jako je MSBuild nebo, se [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] nedá použít k sestavování [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikací, které jsou vytvořené v [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] .|

## <a name="see-also"></a>Viz také

- [Vytváření vlastních projektů s podporou verzí](../misc/making-custom-projects-version-aware.md)
