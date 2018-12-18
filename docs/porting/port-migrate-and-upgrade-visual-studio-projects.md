---
title: Přenos, migrace a upgrade projektů
description: Referenční informace pro podporu projektů vytvořených v dřívějších verzích sady Visual Studio a jak Visual Studio rozhodne, když je potřeba migrovat projekt v sadě Visual Studio 2017.
ms.date: 10/09/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload: multiple
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
ms.openlocfilehash: a8161fd7534554da0ad45b3aa2b985a68dd9e49d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067058"
---
# <a name="project-migration-and-upgrade-reference-for-visual-studio-2017"></a>Migrace a upgrade odkaz na projekt pro Visual Studio 2017

Každá nová verze sady Visual Studio obecně podporuje většinu typů předchozích projektů, souborů a dalších zdrojů. Můžete pracovat s nimi [jako vám vždy mít](../ide/solutions-and-projects-in-visual-studio.md), a za předpokladu, že nejsou závislé na novější funkce, Visual Studio se pokusí obecně pro zachování zpětné kompatibility s předchozími verzemi, jako je Visual Studio 2015, Visual Studio 2013 a Visual Studio 2012. (Viz [zpráva k vydání verze](https://visualstudio.microsoft.com/vs/release-notes/) u funkcí, které jsou specifické pro verze.)

Podpora pro některé typy projektů také mění v průběhu času. Novější verze sady Visual Studio může už nepodporují vůbec některých projektů nebo vyžaduje aktualizaci projektu tak, aby už nejsou zpětně kompatibilní. Aktuální stav na problémy s migrací, najdete [web komunity vývojářů v aplikaci Visual Studio](https://developercommunity.visualstudio.com).

Tento článek k dispozici obsahuje podrobnosti pouze pro typy projektů, které lze migrovat Visual Studio 2017. Tento článek nezahrnuje typy projektů, které již nejsou podporovány v sadě Visual Studio 2017 a proto není možné migrovat. Tento článek také nezahrnuje podporované typy projektů, které mají žádné problémy s migrací; Tento seznam se nachází na [cílení platformy nebo Kompatibilita](/visualstudio/productinfo/vs2017-compatibility-vs).

> [!Important]
> Některé typy projektů vyžadují instalaci odpovídající úloh prostřednictvím instalačního programu sady Visual Studio. Pokud nemáte nainstalovaná úloha, sada Visual Studio hlásí typ projektu neznámé nebo nekompatibilní. V takovém případě zkontrolujte vaše možnosti instalace a zkuste to znovu. Znovu, se zobrazí [cílení platformy nebo Kompatibilita](/visualstudio/productinfo/vs2017-compatibility-vs) , kde najdete podrobnosti o podpoře project v sadě Visual Studio 2017.

## <a name="project-types"></a>Typy projektů

Následující seznam popisuje podporu v sadě Visual Studio 2017 pro projekty, které byly vytvořeny v dřívějších verzích.

Pokud nevidíte projekt nebo typ souboru zde uvedeny, který by měl být, najdete [Visual Studio 2015 verze tohoto článku](https://docs.microsoft.com/visualstudio/porting/porting-migrating-and-upgrading-visual-studio-projects?view=vs-2015) a pomocí možnosti "Poskytnout názor na dokumentaci" v dolní části této stránky můžete zadat podrobnosti vašeho projektu. (Pokud byste o ni odpověď, použijte názor na dokumentaci a ne anonymní "je tato stránka užitečná?" ovládací prvek.)

| Typ projektu | Podpora |
| --- | --- |
| Projekty .NET core (xproj) | Projekty vytvořené pomocí sady Visual Studio 2015 používá nástroje ve verzi preview, zahrnující souboru projektu xproj. Při otevření souboru xproj se sadou Visual Studio 2017, zobrazí se výzva k migraci soubor na formát csproj (provést zálohu souboru xproj). Tento formát csproj pro projekty .NET Core není podporován v sadě Visual Studio 2015 a starší.  Formát xproj není podporován v sadě Visual Studio 2017 jiných než pro migraci do souboru csproj. Další informace najdete v tématu [projekty .NET Core migrace na formát csproj](/dotnet/core/migration/#visual-studio-2017).|
| Webová aplikace ASP.NET a webové aplikace ASP.NET Core s Application Insights aktivovaných | Pro každého uživatele sady Visual Studio je prostředek informace uloženy v registru na uživatelskou instanci. Tyto informace se používá, když uživatel nemá projekt otevřít a chce prohledávat data Azure Application Insights. Visual Studio 2015 používá umístění registru jiné než Visual Studio 2017 a není v konfliktu.<br/><br/>Jakmile uživatel vytvoří webovou aplikaci ASP.NET nebo webové aplikace ASP.NET Core, uloží se prostředek do souboru .suo. Uživatel můžete projekt otevřít v sadě Visual Studio 2015 nebo 2017 a informace o prostředku se používá pro obě tak dlouho, dokud Visual Studio podporuje projekty a řešení, které se používají v obou verzích. Uživatelé potřebují k ověření jednou pro každý produkt. Například pokud projekt je vytvořen pomocí sady Visual Studio 2015 a otevřít v sadě Visual Studio 2017, uživatel se musí ověřit v sadě Visual Studio 2017. |
| Webový formulář nebo formulář Windows v jazyce C# nebo Visual Basic | Otevřete projekt v sadě Visual Studio 2017 a Visual Studio 2015. |
| Projekty testů jednotky databáze (csproj, VBPROJ) | Starší datová jednotka testovací projekty se načítají v sadě Visual Studio 2017, ale použít GAC'd verzi závislosti. Upgrade projektu testování částí, aby používaly nejnovější závislosti, klikněte pravým tlačítkem na projekt v Průzkumníku řešení a vyberte **převést na projekt testování částí SQL Server...** . |
| F# | Visual Studio 2017 můžete otevřít projekty vytvořené v sadě Visual Studio 2013 a 2015. K povolení funkcí sady Visual Studio 2017 v těchto projektech, ale otevřete vlastnosti projektu a změňte cíl fsharp.core pro F# 4.1. Všimněte si také, že  **F# jazykovou podporu** není vybraná možnost v instalačním programu sady Visual Studio ve výchozím nastavení se sady funkcí .NET, je třeba jej zahrnout vyberete tuto možnost pro úlohy, nebo výběrem ze  **Jednotlivé komponenty** kartu **vývojových aktivit**. |
| InstallShield<br/>Instalační program MSI | Instalační program projekty vytvořené v sadě Visual Studio 2010 můžete otevřít v novější verze ve spolupráci [rozšíření projektů instalačního programu sady Visual Studio](https://marketplace.visualstudio.com/items?itemName=UnniRavindranathan-MSFT.MicrosoftVisualStudio2013InstallerProjects). Viz také [rozšíření Visual Studio 2017 WiX Toolset](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension). InstallShield Limited Edition je již součástí sady Visual Studio. Obraťte se na [Flexera softwaru](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) o dostupnosti pro Visual Studio 2017. |
| LightSwitch | Aplikace LightSwitch je již nejsou podporovány v sadě Visual Studio 2017. Projekty vytvořené pomocí sady Visual Studio 2012 a starší otevřený v sadě Visual Studio 2013 nebo Visual Studio 2015 jsou upgradovány a lze je otevřít pouze v sadě Visual Studio 2013 nebo Visual Studio 2015 po tomto datu. |
| Nástroje Microsoft Azure pro sadu Visual Studio | Chcete-li otevřít tyto typy projektů, nejdřív nainstalovat [sady Azure SDK for .NET](http://azure.microsoft.com/downloads/), pak otevřete projekt. V případě potřeby váš projekt se aktualizuje. |
| Framework Model-View-Controller (MVC technologie ASP.NET) | Podpora pro verze MVC a sady Visual Studio:<ul><li>Visual Studio 2010 SP1 podporuje MVC 2 a MVC 3; Prostřednictvím je přidána podpora MVC 4 [ASP.NET 4 MVC 4 ke stažení Visual Studio 2010 SP1](https://www.microsoft.com/download/details.aspx?id=30683)</li><li>Visual Studio 2012 podporuje pouze MVC 3 a MVC 4</li><li>Visual Studio 2013 podporuje pouze MVC 4 a MVC 5</li><li>Visual Studio 2017 a Visual Studio 2015 podporuje MVC 4 (můžete otevřít stávající projekty ale nikoli vytvářet nové) a MVC 5</li></ul><br/>Upgrade verze MVC:<ul><li>Informace o tom, jak automaticky aktualizovat z MVC 2 na MVC 3 naleznete v tématu [ASP.NET MVC 3 aplikace Upgrader](http://go.microsoft.com/fwlink/?LinkID=238178).</li><li>Informace o tom, jak ručně aktualizovat z MVC 2 na MVC 3 naleznete v tématu [aktualizace projektu ASP.NET MVC 2 na ASP.NET MVC 3 nástroje Update](http://go.microsoft.com/fwlink/?linkid=238178).</li><li>Informace o tom, jak ručně aktualizaci z MVC3 na mvc4 naleznete v tématu [upgrade projektu ASP.NET MVC 3 na ASP.NET MVC 4](http://www.asp.net/whitepapers/mvc4-release-notes). Pokud váš projekt cílí na rozhraní .NET Framework 3.5 SP1, je nutné cíl změnit na použití rozhraní .NET Framework 4.</li><li>Informace o manuální aktualizaci z MVC 4 na MVC 5 najdete v tématu [pokyny k upgradu ASP.NET MVC 4 a projektem webového rozhraní API technologie ASP.NET MVC 5 a webovým rozhraním API 2](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2).</li></ul> |
| Modelování | Pokud umožníte softwaru Visual Studio automaticky aktualizovat projekt, lze jej otevřít v sadě Visual Studio 2015, Visual Studio 2013 nebo Visual Studio 2012.<br/><br/>Formát projektu modelování nedošlo ke změně mezi Visual Studio 2015 a Visual Studio 2017 a projekt lze otevřít a upravit v libovolné verzi. Nicméně existují rozdíly v chování v sadě Visual Studio 2017:<ul><li>Projekty modelování jsou dnes označovány jako "Ověřování závislostí" projekty v nabídkách a šablony.</li><li>Diagramy UML jsou již nejsou podporovány v sadě Visual Studio 2017. Soubory UML jsou uvedeny v Průzkumníku řešení jako před, ale jsou otevřené jako soubory XML. Pomocí Visual Studio 2015 můžete zobrazit, vytvořit nebo upravit diagramy UML.</li><li>V sadě Visual Studio 2017 se ověřování závislostí architektury už provádí při sestavení projektu modelování. Místo toho jako je předdefinovaný všech projektů kódu, se provádí ověřování. Tato změna nemá vliv na projekt modelování, ale vyžaduje změny do kódové projekty se ověřují. Visual Studio 2017 můžete automaticky proveďte potřebné změny do kódové projekty ([informace](http://go.microsoft.com/fwlink/?LinkId=827800)).</li></ul> |
| Instalační program MSI (vdproj) | Projekty InstallShield. |
| Sada Office 2007 VSTO | Vyžaduje jednosměrnou aktualizaci pro Visual Studio 2017. |
| Office 2010 VSTO | Pokud je projekt zaměřen na rozhraní .NET Framework 4, lze jej otevřít v aplikaci Visual Studio 2010 SP1 a novější. Všechny ostatní projekty vyžadují jednosměrnou aktualizaci. |
| Service Fabric (sfproj) | Aplikace Service Fabricu projektů lze otevřít v sadě Visual Studio 2015 nebo Visual Studio 2017, pokud projekt aplikace Service Fabric odkazuje na projekt služby ASP.NET Core. Projekty Service Fabricu ze sady Visual Studio 2015, které jsou otevřeny v sadě Visual Studio 2017 jsou jednosměrné migrovat z formátu xproj na csproj. Viz "Projekty .NET Core (xproj)" dříve v této tabulce. |
| SharePoint 2010 | Při otevření projektu řešení služby SharePoint pomocí sady Visual Studio 2017, dojde k upgradu na službu SharePoint 2013 nebo SharePoint 2016. Úloha ".NET Desktop Development" musí být nainstalován v sadě Visual Studio 2017 pro upgrade.<br/><br/>Další informace o tom, jak upgradovat projekty služby SharePoint, naleznete v tématu [upgradovat na službu SharePoint 2013](https://technet.microsoft.com/library/cc303420.aspx), [pracovního postupu aktualizace v SharePoint serveru 2013](https://technet.microsoft.com/library/dn133867.aspx), a [Vytvoření farmy serverů SharePoint Server 2016 pro databázi připojte upgrade](https://technet.microsoft.com/library/cc263026(v=office.16).aspx). |
| SharePoint 2016 | SharePoint Add-In projekty vytvořené v Office Developer Tools ve verzi Preview 2 nelze otevřít v sadě Visual Studio 2017. Pokud chcete toto omezení obejít, aktualizujte `MinimumVisualStudioVersion` k 12.0 a `MinimumOfficeToolsVersion` k 12.2 v souboru csproj vbproj. |
| Silverlight | Projekty technologie Silverlight v sadě Visual Studio 2017 není podporován. Chcete-li udržovat aplikace Silverlight, používejte nadále Visual Studio 2015. |
| SQL Server Reporting Services a SQL Server Analysis Services (SSRS, rozšíření SSDT, SSAS, účty spravované služby) | Pro tyto typy projektů je poskytována prostřednictvím podpory dvě rozšíření v Galerii Visual Studio: [projekty modelování služby Microsoft Analysis Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) a [Microsoft Reporting Services projekty](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio). Podpora rozšíření SSDT je také součástí úloze ukládání a zpracování v sadě Visual Studio 2017. |
| SQL Server Integration Services (SSIS) | Podpora pro Visual Studio 2017 je k dispozici prostřednictvím SQL Server Data Tools (SSDT). Další informace najdete v tématu [blog služby SQL Server Integration Services](https://blogs.msdn.microsoft.com/ssis/2017/08/23/ssis-designer-is-now-available-for-visual-studio-2017/). |
| Visual C++ | Visual Studio 2017 můžete použít pro práci v projektech, které byly vytvořeny v dřívějších verzích sady Visual Studio zpět do sady Visual Studio 2010. Při prvním otevření projektu, máte možnost upgradu na nejnovější kompilátoru a nástrojů, nebo pokračovat v používání původního. Pokud se rozhodnete používat i nadále původního, Visual Studio 2017 neprovede žádné změny souboru projektu a sady nástrojů z dřívější instalace sady Visual Studio používá k sestavení projektu. Zachovat původní možnosti prostředky můžete i nadále otevřít projekt v původní verzi sady Visual Studio v případě potřeby. Další informace najdete v tématu [pomocí nativního cílení na více platforem v sadě Visual Studio sestavení starých projektů](/cpp/porting/use-native-multi-targeting). |
| Rozšiřitelnost sady Visual Studio/souboru VSIX | Projekty s MinimumVersion 14.0 nebo méně aktualizují deklarovat MinimumVersion 15.0, což zabrání projektu se otevře v dřívějších verzích sady Visual Studio. Povolit projekt otevřít ve starších verzích, nastavte na MinimumVersion `$(VisualStudioVersion)`. Viz také [postupy: migrace projektů rozšíření do sady Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md). |
| Visual Studio Lab Management | Můžete použít nástroje Microsoft Test Manager nebo Visual Studio 2010 SP1 a novější k otevření prostředí, které jsou vytvořeny v některé z těchto verzí. Ale pro Visual Studio 2010 SP1 verze nástroje Microsoft Test Manager musí odpovídat verzi serveru Team Foundation Server než budete moct vytvořit prostředí. |
| Visual Studio Tools pro Apache Cordova | Projekty lze otevřít v sadě Visual Studio 2017, ale nejsou zpětně kompatibilní. Při otevření projektu ze sady Visual Studio 2015, se zobrazí výzva k cílem umožnit úpravy do projektu. Tuto úpravu inovuje projekt na používání sady nástrojů místo `taco.json` souboru ke správě verzí Cordova knihovny, jeho platformy, jeho moduly plug-in a jeho závislosti uzlů/npm. Zobrazit [Průvodce migrací](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/first-steps/migrate-from-visual-studio-2015) Další informace. |
| Nasazení webu (wdproj) | Podpora pro nasazení webu byla odebrána projekty v sadě Visual Studio 2012 a uveďte podpora profilů publikování. Protože neexistuje žádný ekvivalent v sadě Visual Studio 2017, neexistuje žádný způsob automatického migrace pro tyto projekty. Místo toho v textovém editoru otevřete soubor wdproj a jakékoli vlastní nastavení do pubxml kopírování a vkládání (profil publikování) souboru, jak je popsáno na [StackOverflow](https://stackoverflow.com/a/12061065/1203388). Viz také [plány týkající se webu a webové projekty nasazení](https://blogs.msdn.microsoft.com/webdev/2012/08/06/plans-regarding-website-projects-and-web-deployment-projects/). |
| Windows Communication Foundation, Windows Workflow Foundation | Tento projekt lze otevřít v sadě Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 a Visual Studio 2012 |
| Windows Presentation Foundation | Tento projekt lze otevřít v sadě Visual Studio 2013, Visual Studio 2012 a Visual Studio 2010 SP1. |
| Aplikace pro Windows Store a Phone | Projekty pro Windows Store 8.1 a 8.0 a Windows Phone 8.1 a 8.0 se nepodporují v sadě Visual Studio 2017. Chcete-li tyto aplikace udržovat, používejte nadále Visual Studio 2015. Chcete-li udržovat projekty pro Windows Phone 7.x, používejte Visual Studio 2012. |

## <a name="how-visual-studio-decides-when-to-migrate-a-project"></a>Jak Visual Studio Určuje, kdy migrovat projekt

Každá nová verze sady Visual Studio se obecně snaží udržovat kompatibilitu s předchozími verzemi, tak, že stejný projekt lze otevřít, upravit a integrované napříč různými verzemi. Existují však nevyhnutelné změny postupně tak, že některé typy projektů může již nejsou podporovány. (Viz [cílení platformy nebo Kompatibilita](/visualstudio/productinfo/vs2017-compatibility-vs) pro jaký projekt jsou podporovány typy v sadě Visual Studio 2017.) V těchto případech se novější verze sady Visual Studio nebude načtení projektu a nenabízí způsob migrace; je třeba spravovat tento projekt v předchozí verzi sady Visual Studio, které ho podporují.

V ostatních případech novější verze sady Visual Studio můžete otevřít projekt, ale musí aktualizovat nebo migrovat projekt takovým způsobem, který může vykreslit kompatibilní s předchozími verzemi. Visual Studio používá řadu kritéria k určení, zda je nutné provést takové migraci:

- Kompatibilita s verzí cílové platformy, zpět do Visual Studio 2013 RTM.

- Kompatibilita aktiv návrhu s předchozími verzemi sady Visual Studio. (Konkrétně různé kanály sady Visual Studio 2017; Visual Studio 2015 RTM a Update 3; Visual Studio 2013 RTM a Update 5; Visual Studio 2012 Update 4; Visual Studio 2010 s aktualizací SP 1.) Visual Studio 2017, zaměřuje na řádně selhat s nepoužívané návrhu prostředky bez poškození, je tak, že předchozí verze lze projekt otevřít.

- Určuje, zda by nové prvky návrhu čas přerušení kompatibility s předchozími verzemi na Visual Studio 2013 RTM a Update 5.

Engineering vlastník typu projektu dotyčný zabývá tato kritéria a provádí volání, kde podpory kompatibility, a migrace mají obavy z toho. Visual Studio opět snaží udržovat transparentní kompatibilitu mezi verzemi sady Visual Studio Pokud je to možné, což znamená, že jedna můžete vytvářet a upravovat projekty v jedné verzi sady Visual Studio a prostě to funguje v dalších verzích.

Pokud takové kompatibility není možné, ale jako u některých typů projektů, které jsou popsané v tomto článku, pak Visual Studio otevře Průvodce upgradem provést nezbytné změny jednosměrná.

Tyto změny jednosměrné může zahrnovat změnu `ToolsVersion` vlastnost v souboru projektu, který označuje, která verze nástroje MSBuild můžete vypnout zdrojový kód projektu do spustitelných a nasaditelné artefakty, takže v konečném důsledku požadované. To znamená, co vykreslí projekt není kompatibilní s předchozími verzemi sady Visual Studio není *sady Visual Studio* verze, ale *MSBuild* verze, počítáno od `ToolsVersion`. Tak dlouho, dokud vaše verze sady Visual Studio obsahuje sada nástrojů MSBuild, který odpovídá `ToolsVersion` v projektu, pak Visual Studio můžete vyvolat tuto sadu nástrojů k sestavení projektu.

Pokud chcete zachovat maximální kompatibilitu s projekty vytvořené ve starších verzích, Visual Studio 2017 obsahuje nezbytné sady nástrojů MSBuild pro podporu `ToolsVersion` 15, 14, 12 a 4. Projekty, které používají některá z těchto `ToolsVersion` hodnot by měl mít za následek úspěšné sestavení. (Na základě práv subjektů, znovu na tom, jestli se Visual Studio 2017 podporuje typ projektu vůbec, jak je popsáno v [cílení platformy nebo Kompatibilita](/visualstudio/productinfo/vs2017-compatibility-vs).)

V tomto kontextu dotaz přirozeně, zda by měl akci k ruční aktualizaci nebo migrovat projekt na novější `ToolsVersion` hodnotu. Tato změna není nutný a pravděpodobně vygeneruje všechny chyby a upozornění, které je třeba opravit a získat projekt znovu sestavit. Kromě toho pokud Visual Studio klesne podporu pro konkrétní `ToolsVersion` v budoucnu, pak otevřete projekt spustí proces migrace projektu konkrétně, protože `ToolsVersion` je třeba hodnotu změnit. V takovém případě subsystém pro konkrétní projekt typu ví, přesně co je potřeba změnit a můžete provádět tyto změny automaticky, jak je popsáno výše v tomto článku.

# <a name="next-steps"></a>Další kroky

Přečtěte si další informace v následujících článcích:

- [Pokyny k hodnotě ToolsVersion](../msbuild/msbuild-toolset-toolsversion.md)
- [Pokyny k cílení na rozhraní Framework](../ide/visual-studio-multi-targeting-overview.md)

## <a name="see-also"></a>Viz také:

[Migrace a upgrade odkaz na projekt pro Visual Studio 2019 Preview](port-migrate-upgrade-visual-studio-projects-2019.md)
