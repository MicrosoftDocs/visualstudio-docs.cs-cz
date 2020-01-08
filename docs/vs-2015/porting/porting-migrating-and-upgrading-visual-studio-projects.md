---
title: Přenosy, migrace a upgrade projektů | Dokumentace Microsoftu
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
ms.openlocfilehash: e78062acfa95c48f0e95f18f42b2c1b26d1f3fa2
ms.sourcegitcommit: 86e1b3eca4633c7522b48282ff7a2be7a09296dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548226"
---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Port, migrace a upgrade projektů sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v [referenčních informacích k migraci projektů a upgradu pro Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).

Pokud zvažujete, zda byste měli přejít na novější verzi sady Visual Studio, můžete použít tento článek k zjištění, která řešení, projekty, soubory a další prostředky, které jste vytvořili v Visual Studio 2013, Visual Studio 2012 nebo Visual Studio 2010 SP1 budou spouštěny bez úprav v Visual Studio 2013 a Visual Studio 2015. Nebo jste se mohli setkat s touto stránkou, pokud se při pokusu o otevření projektu, který není podporován ve verzi sady Visual Studio, který jste otevřeli v systému, nebo který vyžaduje sadu SDK nebo rozšíření, jako je například sada Azure SDK pro .NET, objevila chybová zpráva.

Mnoho široce používaných prostředků se chová stejně jako v aplikaci Visual Studio 2015, Visual Studio 2013 a dvou předchozích verzích. Například v aplikaci Visual Studio 2015 můžete otevřít projekt, který byl vytvořen v Visual Studio 2013 nebo Visual Studio 2012, změnit ho a znovu ho otevřít v aplikaci Visual Studio 2015. Vaše změny jsou trvalé a projekt se chová stejně jako v dřívější verzi. Totéž platí pro mnoho aktiv, které byly vytvořeny v aplikaci Visual Studio 2010 SP1.

V případě Visual Basic nepředstavila aplikace Visual Studio 2015 žádné změny, které zabrání aplikaci Visual Basic vytvořenou v Visual Studio 2013 kompilaci. Chování aplikace Visual Basic, které se znovu zkompiluje pomocí sady Visual Studio 2015, neovlivní chování za běhu.

Pokud používáte sadu Visual Studio 2015 společně s Visual Studio 2013, sadou Visual Studio 2012 nebo sadou Visual Studio 2010 SP1, můžete vytvářet a upravovat projekty a soubory v některé z těchto verzí. Můžete přenášet projekty a soubory mezi verzemi tak dlouho, dokud nepřidáte funkce, které nejsou podporovány v jedné nebo více verzích.

## <a name="project"></a> Projekty

Následující seznam popisuje podporu v aplikaci Visual Studio 2015 a Visual Studio 2013 pro projekty, které byly vytvořeny v aplikaci Visual Studio 2012 nebo Visual Studio 2010 SP1. Tento seznam vám pomůže určit, zda můžete otevřít projekt "tak, jak je" v aplikaci Visual Studio 2015, Visual Studio 2013, Visual Studio 2012 nebo Visual Studio 2010 SP1 nebo zda je nutné jej změnit, aby se zajistila kompatibilita.

|Typ projektu|Kompatibilita|
|---------------------|-------------------|
|Universal Windows Platform apps|Instalace nástrojů Universal Windows apps, v instalačním programu sady Visual Studio, vyberte **vlastní** nebo **změnit**a pak vyberte **univerzální nástroje pro vývoj aplikací Windows**.<br /><br /> Vývoj aplikací Univerzální platforma Windows (UWP) pro Windows 10 je podporován pouze v systému Visual Studio 2015 ve Windows 10 nebo [!INCLUDE[win81](../includes/win81-md.md)].|
|Aplikace pro Windows Store|Vývoj aplikací pro Windows Store, včetně univerzálních aplikací pro Windows 8.1 a Windows Phone 8.1, je podporována v [!INCLUDE[win81](../includes/win81-md.md)] a Windows 10. Existující [!INCLUDE[win8](../includes/win8-md.md)] projektů mohou být nadále servisovány, ale nové [!INCLUDE[win8](../includes/win8-md.md)] projekty nelze vytvořit. [!INCLUDE[win81](../includes/win81-md.md)] projekty mohou záviset pouze na určitých typech referencí. Další informace najdete v tématu [Správa odkazů v projektu](../ide/managing-references-in-a-project.md). **Poznámka:** [!INCLUDE[win81](../includes/win81-md.md)] projekty vytvořené pomocí sady visual Studio 2015 nebo Visual Studio 2013 nelze otevřít v aplikaci visual Studio 2012. Důvodem je, že [!INCLUDE[win81](../includes/win81-md.md)] projekty vytvořené pomocí sady Visual Studio 2015 a Visual Studio 2013 cílit na tyto verze a Visual Studio 2012 podporuje pouze [!INCLUDE[win8](../includes/win8-md.md)] projekty, které cílí na [!INCLUDE[win8](../includes/win8-md.md)].|
|[!INCLUDE[net_v451](../includes/net-v451-md.md)]|Můžete vytvořit a použít tyto projekty v sadě Visual Studio 2015 a Visual Studio 2013 po instalaci příslušného sady multi-targeting pack. Tyto projekty nejsou podporovány v aplikaci Visual Studio 2010 SP1.|
|[!INCLUDE[net_v45](../includes/net-v45-md.md)]|Tyto projekty lze vytvořit a otevřít v aplikaci Visual Studio 2015, Visual Studio 2013 a Visual Studio 2012, ale ne v aplikaci Visual Studio 2010 SP1.|
|BizTalk|Projekty BizTalk serveru nejsou kompatibilní se sadou Visual Studio 2015 nebo Visual Studio 2013.|
|Aplikace nebo knihovna tříd technologie Silverlight 4 v jazyce C# nebo Visual Basic|Pokud chcete, aby aplikace Visual Studio automaticky aktualizovala projekt, můžete ji otevřít buď v Visual Studio 2013, nebo v aplikaci Visual Studio 2012.|
|Webový formulář nebo formulář Windows v jazyce C# nebo Visual Basic|Projekt lze otevřít v Visual Studio 2013 a v aplikaci Visual Studio 2012.|
|Visual Basic 6 a Visual C++ 6|Visual Studio 2012 a Visual Studio 2013 nepodporují ladění aplikací vytvořených pomocí Visual Basic 6 nebo Visual C++ 6; Chcete-li ladit tyto aplikace, použijte dřívější verze aplikace Visual Studio.|
|Programový test UI|Pokud chcete, aby aplikace Visual Studio automaticky aktualizovala projekt, můžete ji otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|F#|Pokud aplikaci Visual Studio povolíte upgrade projektu, který byl vytvořen v aplikaci Visual Studio 2010 SP1, můžete jej otevřít v Visual Studio 2013 a Visual Studio 2012. Projekt Silverlight, který byl vytvořen ve starší verzi sady Visual Studio, však nelze upgradovat na Visual Studio 2013. Místo toho je nutné vytvořit projekt Silverlight v Visual Studio 2013 a potom do něj zkopírovat kód. Projekty Silverlight, které vytvoříte v Visual Studio 2013 cílovém programu Silverlight 5.|
|LightSwitch|Pokud aplikaci Visual Studio povolíte automatické upgrade projektu, můžete ji otevřít pouze v Visual Studio 2013.|
|Mezipaměť místní databáze|V Visual Studio 2013 není obsažena Šablona místní mezipaměti databáze a dialogové okno **Konfigurace synchronizace dat** . Můžete použít Visual Studio 2013 k otevření a spuštění projektů, které byly vytvořeny v [!INCLUDE[vs2010](../includes/vs2010-md.md)], pokud je nainstalována služba Microsoft Synchronization Services v 1.0, ale pokud je chcete aktualizovat v Visual Studio 2013, je nutné ručně provést všechny změny v kódu. Jako alternativu můžete dál používat [!INCLUDE[vs2010](../includes/vs2010-md.md)] pro správu a aktualizaci těchto projektů.  Pro nový vývoj je třeba použít nový synchronizační model, který je poskytován rámcem Microsoft Sync Framework. Informace najdete v tématu [Microsoft Sync Framework Developer Center](https://msdn.microsoft.com/sync/default)|
|Rámec MVC (Model View Controller)|Visual Studio 2010 SP1 podporuje pouze MVC 2 a MVC 3, Visual Studio 2012 podporuje pouze MVC 3 a MVC 4 a Visual Studio 2013 podporuje pouze MVC 4. Informace o tom, jak automaticky aktualizovat z MVC 2 na MVC 3 naleznete v tématu [ASP.NET MVC 3 aplikace Upgrader](https://go.microsoft.com/fwlink/?LinkID=238178). Informace o tom, jak ručně aktualizovat z MVC 2 na MVC 3 naleznete v tématu [aktualizace projektu ASP.NET MVC 2 na ASP.NET MVC 3 nástroje Update](https://go.microsoft.com/fwlink/?linkid=238178). Informace o tom, jak ručně aktualizaci z MVC3 na mvc4 naleznete v tématu [upgrade projektu ASP.NET MVC 3 na ASP.NET MVC 4](https://docs.microsoft.com/aspnet/whitepapers/mvc4-release-notes). Pokud je projekt cílen na rozhraní .NET Framework 3.5 SP1, je nutné cíl změnit na rozhraní .NET Framework 4.|
|Modelování|Pokud chcete, aby aplikace Visual Studio automaticky aktualizovala projekt, můžete ji otevřít v Visual Studio 2013, Visual Studio 2012 nebo Visual Studio 2010 SP1.<br /><br /> Když služba Team Foundation sestaví modelovací projekt, pokusí se ověřit vrstvy projektu. V Visual Studio 2013 Team Foundation Build nemůže ověřit vrstvy pro projekt modelování, který byl vytvořen v aplikaci Visual Studio 2010 SP1. V rámci sady Visual Studio 2010 SP1 však Team Foundation Build může ověřit vrstvy v projektu modelování, který byl vytvořen v Visual Studio 2013.|
|Ladění MPI nebo clusteru|Pokud je stejná verze modulu runtime nebo nástrojů nainstalována na počítačích se systémem Visual Studio 2013, Visual Studio 2012 nebo Visual Studio 2010 SP1, můžete tento projekt otevřít ve všech třech verzích.|
|Instalační program MSI (.vdproj)|Tento projekt nelze otevřít v Visual Studio 2013, protože nepodporuje tento typ projektu. Doporučujeme použít nástroj InstallShield Limited Edition (ISLE) pro systém Visual Studio; jedná se o řešení pro nasazení, které je zdarma a přímo podporuje většinu operačních systémů Windows a běhy aplikací. Program ISLE lze rovněž použít pro import dat a nastavení z projektů instalačního programu systému Visual Studio. .|
|Sada Office 2007 VSTO|Pokud upgradujete projekt na cílovou sadu Office 2013 a .NET Framework 4, můžete tento projekt otevřít v Visual Studio 2013, Visual Studio 2012 nebo Visual Studio 2010 SP1.|
|Office 2010 VSTO|Pokud je projekt cílen na .NET Framework 4, můžete jej otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1. Všechny ostatní projekty vyžadují jednosměrnou aktualizaci.|
|Bohaté internetové aplikace|Pokud upgradujete projekt, můžete jej otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|SharePoint 2007|Tento projekt nelze otevřít v Visual Studio 2013. Pokud však projekt upgradujete ručně na SharePoint 2010, můžete jej otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1. Další informace o tom, jak upgradovat SharePoint 2007, najdete v tématu [migrace ze sharepointu 2007 na službu sharepoint 2010 pro](https://go.microsoft.com/fwlink/?LinkId=238224) Nástroj pro migraci IT pro a [SharePoint Enterprise Search pro SharePoint Server 2010](https://docs.microsoft.com/previous-versions/office/developer/sharepoint-2010/ee556856(v%3Doffice.14)).|
|SharePoint 2010|Projekt lze otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|SketchFlow|Pokud aplikaci Visual Studio povolíte upgrade projektu na verzi WPF 4.5/Silverlight 5, můžete jej otevřít v aplikaci Visual Studio 2012 a Visual Studio 2013.|
|[!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] Databáze|Projekt lze otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1. Pokud máte soubor databáze (MDF), který byl vytvořen v dřívější verzi serveru SQL Server, je nutné upgradovat na [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] předtím, než ho můžete použít s verzí SQL serveru Express LocalDB, ale databáze již není kompatibilní s předchozími verzemi serveru SQL Server. Pokud upgrade neuděláte, můžete pokračovat v práci s databází v Visual Studio 2013 tím, že nainstalujete a použijete [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] ve stejném počítači. Další informace najdete v tématu [Upgrade souborů .mdf](../data-tools/upgrade-dot-mdf-files.md).|
|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express|Pokud je [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express nainstalován na počítačích, na kterých běží Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1, můžete projekt otevřít ve všech třech verzích.|
|Projekt sestavy systému SQL Server|Projekt lze otevřít v Visual Studio 2013 a v aplikaci Visual Studio 2012. Pro místní režim pouze (když není připojení k SQL serveru), nebudete získáte možnosti času návrhu pro ovládací prvky asociované s prohlížečem v [!INCLUDE[vs2010](../includes/vs2010-md.md)], ale bude program fungovat správně v době běhu. **Upozornění:**  Pokud přidáte funkci, která je specifická pro Visual Studio 2013, schéma sestavy bude automaticky upgradováno a projekt již nebude možné otevřít v aplikaci Visual Studio 2012.|
|Testování částí|K otevření testů, které byly vytvořeny v některé z těchto verzí, můžete použít [!INCLUDE[TCMext](../includes/tcmext-md.md)] v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|Visual C++ –|Můžete použít Visual Studio 2013 k otevření C++ projektu, který byl vytvořen v aplikaci visual Studio 2012 nebo visual Studio 2010 SP1. Chcete-li použít prostředí Visual Studio 2013 Build pro sestavení projektu, který byl vytvořen v aplikaci Visual Studio 2012, je nutné mít nainstalovány obě verze sady Visual Studio do stejného počítače. Další informace najdete v tématu [postupy: Upgrade projekty Visual C++ pro Visual Studio 2015](../porting/how-to-upgrade-visual-cpp-projects-to-visual-studio-2015.md) a [průvodce Visual C++ přenosem a upgradováním](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb).|
|Web systému Visual Studio 2010|Pokud aplikaci Visual Studio povolíte automatické upgrade projektu, můžete ji otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|Databáze systému Visual Studio 2010 (.dbproj)|Pokud převedete projekt na projekt databáze nástrojů SQL Server Data Tools, můžete jej otevřít v Visual Studio 2013. Visual Studio 2013 ale tyto artefakty nepodporuje:<br /><br /> -testy jednotek<br />-plány generování dat<br />– soubory porovnání dat<br />– rozšíření vlastního pravidla pro statickou analýzu kódu<br />-server.sqlsettings<br />– soubory .sqlcmd<br />– rozšíření vlastního nasazení<br />-dílčí projekty (.files)<br /><br /> Po instalaci datových nástrojů systému SQL Server lze projekt otevřít v systému Visual Studio 2010 SP1 po převodu. Další informace najdete v tématu [Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx).|
|Nástroje Visual Database Tools sady Visual Studio 2010|Tento projekt lze otevřít v sadě Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|Visual Studio Lab Management|K otevření prostředí, která byla vytvořena v některé z těchto verzí, můžete použít [!INCLUDE[TCMext](../includes/tcmext-md.md)], Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1. Verze programu Microsoft Test Manager však musí před vytvořením prostředí odpovídat verzi služby Team Foundation Server.|
|Makro systému Visual Studio|Tento projekt nelze otevřít v Visual Studio 2013, protože nepodporuje typ projektu.|
|Visual Studio SDK/VSIX|Po upgradu projektu sady Visual Studio SDK na Visual Studio 2013 jej nelze otevřít v sadě Visual Studio 2012. Další informace najdete v tématu [postupy: migrace projektů rozšíření do sady Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md).|
|Nástroje Microsoft Azure pro sadu Visual Studio|Pokud používáte Microsoft Azure Tools for Visual Studio verze 2,1, můžete projekt otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1. Pro projekty, které jsou cíleny na starší verze, pokud aplikaci Visual Studio povolíte upgrade projektu na verzi 2,1, můžete jej otevřít v Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|Windows Communication Foundation, Windows Presentation Foundation|Tento projekt lze otevřít v sadě Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1.|
|Windows Mobile|Tento projekt nelze otevřít v Visual Studio 2013, protože nepodporuje typ projektu.|
|Windows Phone 7.1|Pokud aplikaci Visual Studio povolíte upgrade projektu na Windows Phone 8,0, můžete jej otevřít v aplikaci Visual Studio 2012 a Visual Studio 2013.|
|Další|Můžete otevřít většinu dalších typů projektů v aplikaci Visual Studio 2012, Visual Studio 2013 a Visual Studio 2010 SP1.|
|Webové servery FrontPage|Tento projekt nelze otevřít v Visual Studio 2013, protože nepodporuje typ projektu.|
|Přenosná knihovna tříd|Pokud chcete, aby aplikace Visual Studio automaticky aktualizovala projekt, můžete ji otevřít v Visual Studio 2013, Visual Studio 2012 nebo Visual Studio 2010 SP1.<br /><br /> -Projekty, které jsou cíleny na technologii Silverlight 4 budou cíleny na technologii Silverlight 5.<br />-Projekty, které jsou cíleny na Windows Phone 7.0 nebo Windows Phone 7.5 budou cíleny na Windows Phone 8.<br />-Projekty, které jsou cíleny na Xbox 360 nebudou cíleny na Xbox 360.|
|Projekty Azure, jako je například cloudové služby s příponou .deployproj projekty (ccproj rozšíření) a Azure Resource Manageru projekty (projekty cloudových nasazení)|Chcete-li otevřít tyto typy projektů, nejdřív nainstalovat [sady Azure SDK for .NET](https://azure.microsoft.com/downloads/), pak otevřete projekt.|

## <a name="troubleshooting-project-compatibility-issues"></a>Řešení potíží s kompatibilitou projektu
 Tady je několik věcí, které můžete provést, když se projekt neotevře v aplikaci Visual Studio 2015 nebo Visual Studio 2013:

- Pokud se pokusíte otevřít projekt, který není podporován v aplikaci Visual Studio 2015 nebo Visual Studio 2013 a pro které není nainstalována přidružená verze sady Visual Studio, může se zobrazit zpráva, že typ projektu není podporován, a typ projektu může být uveden v dialogovém okně **Revize projektu a změny řešení** v části **nepodporované projekty**. Pokud chcete tento problém vyřešit, otevřete stránku programů a funkcí v Windows **ovládací panely**vyberte **sady Visual Studio**a klikněte na tlačítko **změnu**, **opravy** . Následně lze chybějící verzi nainstalovat.

- Pokud se pokusíte otevřít projekt aplikace klasické pracovní plochy v [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)], dojde k chybě a zobrazí se jedna z následujících zpráv: "Tato verze sady Visual Studio podporuje pouze [!INCLUDE[win81](../includes/win81-md.md)] aplikace" nebo "Tento projekt není kompatibilní s aktuální verzí sady Visual Studio." [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] je omezen na vývoj, testování a nasazení aplikací pro Windows Store pro Windows 8.1. K otevření projektu aplikace klasické pracovní plochy je nutné použít edici systému Visual Studio, která tento typ projektu podporuje.

   Další informace o vydáních sady Visual Studio najdete v tématu [produkty Microsoft Visual Studio](https://visualstudio.microsoft.com/products/)

- Pokud se pokusíte otevřít projekt aplikace Windows Store v [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop, dojde k chybě. [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop nelze použít k vytváření aplikací pro Windows Store. Pokud chcete vytvářet aplikace pro Windows Store, můžete také nainstalovat [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]. Nebo pokud chcete vyvíjet aplikace pro všechny platformy Microsoft a web, vyzkoušejte sadu Visual Studio Professional 2013.

- Pokud projekt vyžaduje funkce, které jsou specifické pro Visual Studio 2013, nelze jej otevřít v dřívější verzi.

- Pokud používáte sadu Visual Studio 2012 a chcete otevřít projekt, který byl vytvořen v Visual Studio 2013, může být možné přizpůsobit systém projektu tak, aby zahrnoval funkce Visual Studio 2013. Informace o tom, jak to provést, najdete v tématu [provádění vlastní projekty podporující verze](../misc/making-custom-projects-version-aware.md).

  Další informace o odstraňování potíží, najdete v článku [Kompatibilita sady Visual Studio 2013](https://support.microsoft.com/help/2863286/roundtrip-issues-for-visual-studio-2012-and-visual-studio-2013-preview) článku znalostní BÁZE.

## <a name="file"></a> Soubory

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
|Soubory protokolů IntelliTrace ze [!INCLUDE[vs2010](../includes/vs2010-md.md)]|Tyto soubory lze otevřít v aplikaci Visual Studio 2012, Visual Studio 2013 a Visual Studio 2010 SP1.|
|Soubory JavaScript Memory Analyzer (.diagsession)|Soubory vytvořené staršími verzemi sady Visual Studio lze zobrazit v Visual Studio 2013. V závislosti na shromažďovaných informacích se však soubory vytvořené v Visual Studio 2013 nemusí otevřít v aplikaci Visual Studio 2012 nebo Visual Studio 2010 SP1.|

## <a name="integration"></a> Integrační aktiva

Při použití klientů a serverů z různých verzí služby Visual Studio Team Foundation Server může dojít k problémům s kompatibilitou.

|Druh integrace|Kompatibilita|
|-------------------------|-------------------|
|Revize kódu a Má práce|Funkce revize kódu a má práce nebudou fungovat, pokud připojení klienta z [!INCLUDE[esprfound](../includes/esprfound-md.md)] k [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)].|
|[!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]|64bitové prostředí jako MSBuild nebo [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] nelze použít k sestavení [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace, které jsou vytvořené v [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)].|

## <a name="see-also"></a>Viz také:

- [Vytváření vlastních projektů s ohledem na verzi](../misc/making-custom-projects-version-aware.md)
