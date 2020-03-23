---
title: Pokročilé funkce
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f65ce2b986114dc553b87db846262c931d74b4c0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78235196"
---
# <a name="features-of-visual-studio"></a>Funkce sady Visual Studio

Visual [Studio IDE přehled](../get-started/visual-studio-ide.md) článek poskytuje základní úvod do sady Visual Studio. Tento článek popisuje funkce, které mohou být vhodnější pro zkušené vývojáře nebo vývojáře, kteří jsou již obeznámeni s Visual Studio.

## <a name="modular-installation"></a>Modulární instalace

Modulární instalační program sady Visual Studio umožňuje zvolit a nainstalovat *úlohy*. Úlohy jsou skupiny funkcí potřebných pro programovací jazyk nebo platformu, které dáváte přednost. Tato strategie pomáhá udržet menší nároky na instalaci sady Visual Studio, což znamená, že se také instaluje a aktualizuje rychleji.

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

Další informace o nastavení sady Visual Studio v systému naleznete v [tématu Instalace sady Visual Studio](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Vytváření cloudových aplikací pro Azure

Visual Studio nabízí sadu nástrojů, které vám umožní snadno vytvářet cloudové aplikace využívající Microsoft Azure. Můžete konfigurovat, vytvářet, ladit, balit a nasazovat aplikace a služby v Microsoft Azure přímo z IDE. Pokud chcete získat nástroje Azure a šablony projektů, vyberte při instalaci Visual Studia vývojové úlohy **Azure.**

![Pracovní vytížení pro vývoj Azure](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

Po instalaci **úlohy vývoje Azure** jsou v dialogovém okně **Nový projekt** k dispozici následující šablony **cloudu** pro C#:

![Šablony cloudových projektů pro Visual Studio](media/cloud-project-templates.png)

::: moniker-end

Visual Studio [Cloud Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) umožňuje zobrazit a spravovat vaše cloudové prostředky založené na Azure v rámci Sady Visual Studio. Tyto prostředky mohou zahrnovat virtuální počítače, tabulky, databáze SQL a další. **Cloud Explorer** zobrazuje prostředky Azure ve všech účtech spravovaných v rámci předplatného Azure, ke které jste přihlášení. A pokud konkrétní operace vyžaduje portál Azure, **Cloud Explorer** poskytuje odkazy, které vás přenese na místo na portálu, kam potřebujete jít.

![Průzkumník cloudu v Sadě Visual Studio](media/cloud-explorer.png)

Služby Azure můžete využít pro své aplikace pomocí **připojených služeb,** jako jsou:

- [Služba připojená ke službě Active Directory,](/azure/active-directory/develop/vs-active-directory-add-connected-service) aby uživatelé mohli používat své účty z [Azure Active Directory](/azure/active-directory/active-directory-whatis) pro připojení k webovým aplikacím
- [Služba připojená k Azure Storage](/azure/vs-azure-tools-connected-services-storage) pro úložiště objektů blob, fronty a tabulky
- [Služba key vault připojená](/azure/key-vault/vs-key-vault-add-connected-service) ke správě tajných kódů pro webové aplikace

Dostupné **připojené služby** závisí na typu projektu. Přidejte službu kliknutím pravým tlačítkem myši na projekt v **Průzkumníku řešení** a výběrem **možnosti Přidat** > **připojenou službu**.

![Propojené služby Visual Studia](media/connected-services.png)

Další informace najdete v [tématu Přechod do cloudu s Visual Studio a Azure](https://visualstudio.microsoft.com/vs/azure-tools/).

## <a name="create-apps-for-the-web"></a>Vytváření aplikací pro web

Web řídí náš moderní svět a Visual Studio vám může pomoct psát aplikace pro něj. Webové aplikace můžete vytvářet pomocí ASP.NET, Node.js, Pythonu, JavaScriptu a TypeScriptu. Visual Studio rozumí webovým architekturám, jako je Angular, jQuery, Express a další. ASP.NET Core a .NET Core běží na operačních systémech Windows, Mac a Linux. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) je hlavní aktualizace MVC, WebAPI a SignalR a běží na Windows, Mac a Linux.  ASP.NET Core byl od základu navržen tak, aby vám poskytl štíhlý a kompozitelný zásobník .NET pro vytváření moderních cloudových webových aplikací a služeb.

Další informace naleznete v [tématu Moderní webové nástroje](https://visualstudio.microsoft.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Vytváření aplikací a her pro různé platformy

Pomocí Sady Visual Studio můžete vytvářet aplikace a hry pro macOS, Linux a Windows, stejně jako pro Android, iOS a další [mobilní zařízení](https://visualstudio.microsoft.com/vs/mobile-app-development/).

- Vytvářejte aplikace [.NET Core,](/dotnet/core/) které běží na Windows, macOS a Linuxu.

- Vytvářejte mobilní aplikace pro iOS, Android a Windows v C# a F# pomocí [Xamarinu](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/).

- Pomocí standardních&mdash;webových technologií HTML,&mdash;CSS a JavaScriptu můžete vytvářet mobilní aplikace pro iOS, Android a Windows pomocí [Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/).

- Vytvářejte 2D a 3D hry v jazyce C# pomocí [nástrojů Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md).

- Vytvářejte nativní aplikace C++ pro zařízení se systémem iOS, Android a Windows. Sdílejte společný kód v knihovnách vytvořených pro iOS, Android a Windows pomocí [jazyka C++ pro vývoj napříč platformami](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development).

- Nasazení, testování a ladění aplikací pro Android pomocí [emulátoru Android](../cross-platform/visual-studio-emulator-for-android.md).

## <a name="connect-to-databases"></a>Připojení k databázím

**Průzkumník serveru** vám pomůže procházet a spravovat instance a datové zdroje serveru SQL Server místně, vzdáleně a na Azure, Salesforce.com, Office 365 a na webech. Chcete-li otevřít **Průzkumníka serveru**, zvolte v hlavní nabídce **možnost Zobrazit** > **Průzkumníka serveru**. Další informace o použití Průzkumníka serveru naleznete v tématu [Přidání nových připojení](../data-tools/add-new-connections.md).

[Datové nástroje SQL Serveru (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) je výkonné vývojové prostředí pro SQL Server, Azure SQL Database a Azure SQL Data Warehouse. Umožňuje vytvářet, ladit, udržovat a refaktorovat databáze. Můžete pracovat s databázovým projektem nebo přímo s připojenou instanci databáze v místním nebo mimo něj.

**Průzkumník objektů serveru SQL Server** v sadě Visual Studio poskytuje zobrazení databázových objektů podobných aplikaci SQL Server Management Studio. Průzkumník objektů SQL Serveru umožňuje provést lehkou správu databáze a návrh. Mezi příklady práce patří úpravy dat tabulky, porovnání schémat, provádění dotazů pomocí kontextových nabídek přímo z Průzkumníka objektů serveru SQL Server a další.

![Průzkumník objektů systému SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Ladění, testování a vylepšování kódu

Při psaní kódu je třeba jej spustit a otestovat na chyby a výkon. Systém ladění sady Visual Studio umožňuje ladit kód spuštěný v místním projektu, na vzdáleném zařízení nebo v [emulátoru zařízení](../cross-platform/visual-studio-emulator-for-android.md). Můžete krokovat kód jeden příkaz najednou a kontrolovat proměnné as you go. Zarážky, které jsou přístupů pouze v případě, že je splněna zadaná podmínka. Možnosti ladění lze spravovat v samotném editoru kódu, takže nemusíte opustit kód. Další podrobnosti o ladění v sadě Visual Studio najdete v [tématu První pohled na ladicí program](../debugger/debugger-feature-tour.md).

Další informace o zlepšení výkonu aplikací najdete v části [Profilování](../profiling/profiling-feature-tour.md) aplikace Visual Studio.

Pro [testování](../test/improve-code-quality.md)visual studio nabízí testování částí, živé testování částí, IntelliTest, testování zatížení a výkonu a další. Visual Studio má také pokročilé možnosti [analýzy kódu](../code-quality/code-analysis-for-managed-code-overview.md) zachytit návrh, zabezpečení a další typy chyb.

## <a name="deploy-your-finished-application"></a>Nasazení dokončené aplikace

Když je vaše aplikace připravená k nasazení pro uživatele nebo zákazníky, Visual Studio k tomu poskytuje nástroje. Možnosti nasazení zahrnují microsoft store, sharepointový web nebo technologie InstallShield nebo Instalační služby systému Windows. Je to všechno přístupné prostřednictvím IDE. Další informace naleznete v [tématu Nasazení aplikací, služeb a součástí](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Správa zdrojového kódu a spolupráce s ostatními

Zdrojový kód můžete spravovat v úložištích Git hostovaných libovolným poskytovatelem, včetně GitHubu. Nebo použijte [Služby Azure DevOps](/azure/devops/index) ke správě kódu vedle chyb a pracovních položek pro celý projekt. Další informace o správě úložiště Gitu ve Visual Studiu pomocí Průzkumníka týmů najdete v tématu Začínáme s [Gitem a Azure Repos.](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) Visual Studio má také další integrované funkce správy zdrojového kódu. Další informace o nich najdete [v tématu Nové funkce Gitu v Sadě Visual Studio (blog).](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/)

Služby Azure DevOps jsou cloudové služby pro plánování, hostování, automatizaci a nasazení softwaru a umožnění spolupráce v týmech. Azure DevOps Services podporují úložiště Git (distribuované správu verzí) i řízení verzí Team Foundation (centralizované správu verzí). Podporují kanály pro průběžné sestavení a vydání (CI/CD) kódu uloženého v systémech správy verzí. Služby Azure DevOps také podporují metodiky vývoje Scrum, CMMI a Agile.

Team Foundation Server (TFS) je centrum pro správu životního cyklu aplikace pro Visual Studio. Umožňuje všem, kteří se podílejí na procesu vývoje, účastnit se pomocí jediného řešení. TFS je také užitečné pro správu heterogenních týmů a projektů.

Pokud máte v síti organizaci Azure DevOps nebo team foundation server, připojíte se k ní prostřednictvím okna **Průzkumníka týmu** v sadě Visual Studio. Z tohoto okna můžete kód zkontrolovat do nebo z správy zdrojového kódu, spravovat pracovní položky, zahájit sestavení a přistupovat k týmovým místnostem a pracovním prostorům. **Průzkumníka týmu** můžete otevřít z vyhledávacího pole nebo v hlavní nabídce v **průzkumníku** > **týmu** nebo v okně Správa**připojení** **týmu** > .

Následující obrázek znázorňuje okno **Průzkumníka týmu** pro řešení, které je hostované ve službách Azure DevOps Services.

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer_devops.png)

Můžete také automatizovat proces sestavení k sestavení kódu, který devs ve vašem týmu mají vráceny se změnami do správy verzí. Lze například sestavit jeden nebo více projektů v noci nebo pokaždé, když je kód vrácen se změnami. Další informace najdete v tématu [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="extend-visual-studio"></a>Rozšíření sady Visual Studio

Pokud Visual Studio nemá přesné funkce, které potřebujete, můžete ji přidat! Integrované vývojové prostředí můžete přizpůsobit na základě pracovního postupu a stylu, přidat podporu pro externí nástroje, které ještě nejsou integrovány s visual studio, a upravit stávající funkce, abyste zvýšili produktivitu. Nejnovější verzi nástroje rozšíření sady Visual Studio (VS SDK) naleznete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Pomocí platformy kompilátoru .NET ("Roslyn") můžete napsat vlastní analyzátory kódu a generátory kódu. Najděte vše, co potřebujete, v [Roslyn](https://github.com/dotnet/Roslyn).

Najděte [existující rozšíření](https://marketplace.visualstudio.com/vs) pro Visual Studio vytvořená vývojáři Microsoftu i naší vývojářskou komunitou.

Další informace o rozšíření sady Visual Studio najdete [v tématu Rozšíření ide sady Visual Studio](https://visualstudio.microsoft.com/vs/extend/).

## <a name="see-also"></a>Viz také

- [Přehled ide sady Visual Studio](../get-started/visual-studio-ide.md)
- [Co je nového ve Visual Studiu 2017](../ide/whats-new-visual-studio-2017.md)
- [Novinky v sadě Visual Studio 2019](../ide/whats-new-visual-studio-2019.md)
