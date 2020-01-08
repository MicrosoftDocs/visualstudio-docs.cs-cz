---
title: Pokročilé funkce
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3ece317d753cb5c4b0b4e5b0e02707a088e8917
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591733"
---
# <a name="features-of-visual-studio"></a>Funkce sady Visual Studio

[Přehled Visual Studio IDE](../get-started/visual-studio-ide.md) článek obsahuje základní informace o sadě Visual Studio. Tento článek popisuje funkce, které by mohly být vhodnější pro zkušené vývojáře, nebo vývojáře, kteří už jsou obeznámeni se sadou Visual Studio.

## <a name="modular-installation"></a>Modulární instalace

Modulární instalační program sady Visual Studio umožňuje zvolit a nainstalovat *úlohy*. Úlohy jsou skupiny funkcí potřebných pro programovací jazyk nebo platformu, které dáváte přednost. Tato strategie pomáhá, aby nárokům na místo instalace sady Visual Studio, která je menší, což znamená, že instalace a aktualizace moc rychlejší.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránku a nainstalovat zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) stránku a nainstalovat zdarma.

::: moniker-end

Další informace o nastavení sady Visual Studio v systému najdete v tématu [instalace sady Visual Studio](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Vytvářejte aplikace s povolenou podporu cloudu pro Azure

Visual Studio nabízí sadu nástrojů, které vám umožní snadno vytvářet aplikace s povolenou podporu cloudu využívající Microsoft Azure. Můžete nakonfigurovat, sestavení, ladění, zabalení a nasazení aplikací a služeb na Microsoft Azure přímo z integrovaného vývojového prostředí. Pokud chcete získat Azure nástroje a šablony projektů, vyberte **vývoj pro Azure** zatížení při instalaci sady Visual Studio.

![Úloha vývoj pro Azure](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

Po instalaci **vývoj pro Azure** pracovního vytížení, následující **cloudu** šablony pro jazyk C# jsou k dispozici v **nový projekt** dialogové okno:

![Cloud šablony projektů pro Visual Studio](media/cloud-project-templates.png)

::: moniker-end

Visual Studio [Průzkumníka cloudu](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) vám umožňuje zobrazit a spravovat prostředky založené na Azure cloud v rámci sady Visual Studio. Tyto prostředky mohou zahrnovat virtuální počítače, tabulek, databází SQL a další. **Cloud Explorer** ukazuje prostředky Azure ve všech účtech spravované v rámci předplatného Azure jste přihlášeni. A pokud se na webu Azure portal, vyžaduje určité operace **Průzkumníka cloudu** obsahuje odkazy, které vás zavedou na portálu na místě, kde budete muset přejít.

![Průzkumník cloudu v sadě Visual Studio](media/cloud-explorer.png)

Můžete využít služby Azure pro vaše aplikace pomocí **připojené služby** jako například:

- [Připojená služba Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service) , uživatelé můžou používat vlastní účty z [Azure Active Directory](/azure/active-directory/active-directory-whatis) pro připojení k webovým aplikacím
- [Připojená služba Azure Storage](/azure/vs-azure-tools-connected-services-storage) pro úložiště objektů blob, fronty a tabulky
- [Připojená služba Key Vault](/azure/key-vault/vs-key-vault-add-connected-service) pro správu tajných kódů pro webové aplikace

K dispozici **připojené služby** závisí na typu vašeho projektu. Přidat službu kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** a zvolíte **přidat** > **připojenou službu**.

![Připojenými službami sady Visual Studio](media/connected-services.png)

Další informace najdete v tématu [přesunout do cloudu pomocí sady Visual Studio a Azure](https://visualstudio.microsoft.com/vs/azure-tools/).

## <a name="create-apps-for-the-web"></a>Vytvářejte aplikace pro web

Na webu jednotek našem moderním světě a Visual Studio vám pomůže psát aplikace pro něj. Můžete vytvořit web apps s využitím ASP.NET, Node.js, Python, JavaScript a TypeScript. Visual Studio plně chápe webové architektury, jako je Angular, jQuery, Express a další. ASP.NET Core a .NET Core, poběží v operačních systémech Windows, Mac a Linux. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) je hlavní aktualizace MVC, WebAPI a technologie SignalR a běží na Windows, Mac a Linux.  ASP.NET Core byly navržené zdola nahoru zajistit, že jste s využitím .NET štíhlý a sestavitelný zásobník pro vývoj moderních webových cloudových aplikací a služeb.

Další informace najdete v tématu [moderní nástroje pro web](https://visualstudio.microsoft.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Vytvářejte multiplatformní aplikace a hry

Visual Studio můžete použít k sestavení aplikací a her pro Windows, macOS a Linux, a také pro Android, iOS a další [mobilní zařízení](https://visualstudio.microsoft.com/vs/mobile-app-development/).

- Sestavení [.NET Core](/dotnet/core/) aplikací pro Windows, macOS a Linux.

- Vytvářejte mobilní aplikace pro iOS, Android a Windows v C# a F# pomocí [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/).

- Používejte standardní webové technologie&mdash;HTML, CSS a JavaScriptu&mdash;můžete vytvářet mobilní aplikace pro iOS, Android a Windows s použitím [Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/).

- Vytváření 2D a 3D hry v jazyce C# s použitím [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md).

- Vytvářejte nativní C++ aplikace pro zařízení s iOS, Androidem a Windows. Sdílejte společný kód v knihovnách postavených pro iOS, Android a Windows s využitím [ C++ pro vývoj pro různé platformy](../cross-platform/visual-cpp-for-cross-platform-mobile-development.md).

- Nasazení, testování a ladění aplikací pro Android s [emulátoru Androidu](../cross-platform/visual-studio-emulator-for-android.md).

## <a name="connect-to-databases"></a>Připojení k databázím

**Průzkumník serveru** usnadňuje procházení a správě instancí systému SQL Server a prostředky místně, vzdáleně a v Azure, Salesforce.com, Office 365 a websites. Chcete-li otevřít **Průzkumníka serveru**, v hlavní nabídce zvolte **zobrazení** > **Průzkumníka serveru**. Další informace o použití Průzkumník serveru naleznete v tématu [Add New Connections](../data-tools/add-new-connections.md).

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) je výkonné vývojové prostředí pro SQL Server, Azure SQL Database a Azure SQL Data Warehouse. Umožňuje sestavovat, ladit, udržovat a Refaktorovat databází. Můžete pracovat s projektem databáze, nebo přímo s připojeném databázovém instance nebo vypnout místně.

**Průzkumník objektů systému SQL Server** v sadě Visual Studio poskytuje přehled vaše databázové objekty, podobně jako SQL Server Management Studio. Průzkumník objektů systému SQL Server vám umožní provádět návrh a práci v databázi pro světlé řízení. Mezi příklady práce patří úpravy dat tabulek, porovnávání schémat a provádění dotazů pomocí kontextových nabídek přímo z Průzkumník objektů systému SQL Server a dalších.

![Průzkumník objektů systému SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Ladit, testovat a zlepšování kódu

Při psaní kódu, musíte ji spustit a otestovat chyb a výkonu. Špičkové ladění systému Visual Studio umožňuje ladit kód spuštěný ve vašem místním projektu na vzdáleném zařízení, nebo na [emulátor zařízení](../cross-platform/visual-studio-emulator-for-android.md). Můžete krokovat kód jeden příkaz najednou a kontrolovat proměnné, co využijete. Můžete nastavit zarážky, které jsou pouze přístupů, když je zadaná podmínka pravdivá. Možnosti ladění lze spravovat v editoru kódu samotném, takže nemusíte opustit kód. Další informace o ladění v aplikaci Visual Studio naleznete v tématu [první pohled na ladicí program](../debugger/debugger-feature-tour.md).

Další informace týkající se vylepšení výkonu aplikací, rezervaci si Visual Studio [profilace](../profiling/profiling-feature-tour.md) funkce.

Pro [testování](../test/improve-code-quality.md), Visual Studio nabízí testování částí, Live Unit Testing, Intellitestu, načítání a testování výkonu a další. Visual Studio také nabízí pokročilé [analýza kódu](../code-quality/code-analysis-for-managed-code-overview.md) možnosti pro zachycení návrh, zabezpečení a dalších typů chyby.

## <a name="deploy-your-finished-application"></a>Nasazení dokončené aplikace

Když je vaše aplikace připravená k nasazení pro uživatele nebo zákazníky, Visual Studio poskytuje nástroje, které to dělají. Mezi možnosti nasazení patří Microsoft Store, na web služby SharePoint nebo pomocí technologie InstallShield nebo Instalační služba systému Windows. To je vše je přístupné prostřednictvím rozhraní IDE. Další informace najdete v tématu [nasazení aplikací, služeb a součástí](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Spravovat zdrojový kód a spolupracovat s ostatními

Můžete spravovat zdrojový kód v úložištích Git, jejichž hostitelem je libovolný poskytovatel, včetně Githubu. Nebo použijte [Azure DevOps služby](/azure/devops/index) ke správě kódu společně s chybami a pracovními položkami pro celý projekt. Zobrazit [Začínáme s Git a úložiště Azure](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) Další informace o správě úložiště Git v sadě Visual Studio pomocí Průzkumníka týmových projektů. Visual Studio také poskytuje jiné funkce správy vestavěné zdrojového kódu. Další informace o těchto [funkcích naleznete v tématu nové funkce Git v aplikaci Visual Studio (blog)](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/).

Azure DevOps Services jsou cloudové služby pro plánování, hostování, automatizaci a nasazení softwaru a umožňují spolupráci v týmech. Azure DevOps Services podporuje úložiště Git (distribuovaná správa verzí) i Správa verzí Team Foundation (centralizované řízení verzí). Podporují kanály pro průběžné sestavování a vydávání kódu (CI/CD), který je uložený v systémech správy verzí. Služby Azure DevOps také podporu metodologie Scrum, CMMI a agilní vývoj.

Team Foundation Server (TFS) je Centrum správy životního cyklu aplikace pro sadu Visual Studio. Umožňuje všem uživatelům zapojené do procesu vývoje se zúčastnit prostřednictvím jediného řešení. TFS je užitečné při správě heterogenních týmům a projektům, příliš.

Pokud máte v síti organizace Azure DevOps nebo Team Foundation Server, k němu připojíte pomocí **Team Exploreru** okna v sadě Visual Studio. Z tohoto okna můžete zkontrolovat kód do nebo ze správy zdrojového kódu, správě pracovních položek, spusťte sestavení a přístup týmové místnosti a pracovní prostory. **Team Explorer** můžete otevřít z vyhledávacího pole nebo v hlavní nabídce ze **zobrazení** > **Team Explorer** nebo z **týmu** > **Spravovat připojení**.

Na následujícím obrázku **Team Exploreru** okna pro řešení, které je hostované v Azure DevOps služby.

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer_devops.png)

Můžete automatizovat proces sestavení k sestavení kódu, který ověří vývojáři ve vašem týmu do správy verzí. Lze například sestavit jeden nebo více projektů v noci nebo pokaždé, když je kód vrácen se změnami. Další informace najdete v tématu [kanály Azure](/azure/devops/pipelines/index?view=vsts).

## <a name="extend-visual-studio"></a>Rozšíření sady Visual Studio

Pokud aplikace Visual Studio nemá přesně funkce, které potřebujete, můžete ho přidat! Přizpůsobení integrovaného vývojového prostředí založené na pracovním postupům a stylu, přidat podporu pro externí nástroje, které zatím nejsou se sadou Visual Studio integrované a upravit stávající funkce pro zvýšení produktivity. Nejnovější verzi sady Visual Studio Extensibility Tools (VS SDK), najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

.NET Compiler Platform ("Roslyn") můžete použít k tvorbě vlastních analyzátorů kódu a generátory kódu. Najít vše, co je potřeba mít [Roslyn](https://github.com/dotnet/Roslyn).

Najít [existující rozšíření](https://marketplace.visualstudio.com/vs) pro Visual Studio vytvořili vývojáři Microsoftu, stejně jako naší komunity vývojářů.

Další informace o rozšíření sady Visual Studio najdete v tématu [rozšíření Visual Studio IDE](https://visualstudio.microsoft.com/vs/extend/).

## <a name="see-also"></a>Viz také:

- [Visual Studio IDE – přehled](../get-started/visual-studio-ide.md)
- [Co je nového v sadě Visual Studio 2017](../ide/whats-new-visual-studio-2017.md)
- [Co je nového v aplikaci Visual Studio 2019](../ide/whats-new-visual-studio-2019.md)
