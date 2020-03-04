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
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78235196"
---
# <a name="features-of-visual-studio"></a>Funkce sady Visual Studio

Článek [Přehled integrovaného vývojového prostředí sady Visual Studio](../get-started/visual-studio-ide.md) poskytuje základní Úvod do sady Visual Studio. Tento článek popisuje funkce, které by mohly být vhodnější pro zkušené vývojáře, nebo vývojáře, kteří už jsou obeznámeni se sadou Visual Studio.

## <a name="modular-installation"></a>Modulární instalace

Modulární instalační program sady Visual Studio umožňuje zvolit a nainstalovat *úlohy*. Úlohy jsou skupiny funkcí potřebných pro programovací jazyk nebo platformu, které dáváte přednost. Tato strategie pomáhá, aby nárokům na místo instalace sady Visual Studio, která je menší, což znamená, že instalace a aktualizace moc rychlejší.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

Další informace o nastavení sady Visual Studio v systému najdete v tématu [instalace sady Visual Studio](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Vytvářejte aplikace s povolenou podporu cloudu pro Azure

Visual Studio nabízí sadu nástrojů, které vám umožní snadno vytvářet aplikace s povolenou podporu cloudu využívající Microsoft Azure. Můžete nakonfigurovat, sestavení, ladění, zabalení a nasazení aplikací a služeb na Microsoft Azure přímo z integrovaného vývojového prostředí. Pokud chcete získat šablony nástrojů a projektů Azure, vyberte při instalaci sady Visual Studio úlohu **vývoj pro Azure** .

![Úloha vývoj pro Azure](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

Po instalaci úlohy **vývoj** pro C# Azure jsou v dialogovém okně **Nový projekt** k dispozici následující šablony **cloudu** :

![Cloud šablony projektů pro Visual Studio](media/cloud-project-templates.png)

::: moniker-end

[Průzkumník cloudu](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) sady Visual Studio umožňuje zobrazit a spravovat cloudové prostředky založené na Azure v sadě Visual Studio. Tyto prostředky mohou zahrnovat virtuální počítače, tabulek, databází SQL a další. **Průzkumník cloudu** zobrazuje prostředky Azure ve všech účtech spravovaných v rámci předplatného Azure, ke kterému jste se přihlásili. A pokud konkrétní operace vyžaduje Azure Portal, **Průzkumník cloudu** poskytuje odkazy, které vás zajímají na místo na portálu, kde potřebujete přejít.

![Průzkumník cloudu v sadě Visual Studio](media/cloud-explorer.png)

Můžete využívat služby Azure pro své aplikace pomocí **propojených služeb** , jako je:

- [Připojená služba Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service) , aby uživatelé mohli používat své účty z [Azure Active Directory](/azure/active-directory/active-directory-whatis) pro připojení k webovým aplikacím
- [Azure Storage připojená služba](/azure/vs-azure-tools-connected-services-storage) pro úložiště objektů blob, fronty a tabulky
- [Key Vault připojená služba](/azure/key-vault/vs-key-vault-add-connected-service) pro správu tajných kódů pro webové aplikace

Dostupné **připojené služby** závisí na typu projektu. Přidejte službu kliknutím pravým tlačítkem myši na projekt v **Průzkumník řešení** a výběrem možnosti **Přidat** **připojenou službu** > .

![Připojenými službami sady Visual Studio](media/connected-services.png)

Další informace najdete v tématu [Přesun do cloudu pomocí sady Visual Studio a Azure](https://visualstudio.microsoft.com/vs/azure-tools/).

## <a name="create-apps-for-the-web"></a>Vytvářejte aplikace pro web

Na webu jednotek našem moderním světě a Visual Studio vám pomůže psát aplikace pro něj. Můžete vytvořit web apps s využitím ASP.NET, Node.js, Python, JavaScript a TypeScript. Visual Studio plně chápe webové architektury, jako je Angular, jQuery, Express a další. ASP.NET Core a .NET Core, poběží v operačních systémech Windows, Mac a Linux. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) je hlavní aktualizace pro MVC, WebApi a Signal a běží v systémech Windows, Mac a Linux.  ASP.NET Core byly navržené zdola nahoru zajistit, že jste s využitím .NET štíhlý a sestavitelný zásobník pro vývoj moderních webových cloudových aplikací a služeb.

Další informace najdete v tématu [moderní webové nástroje](https://visualstudio.microsoft.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Vytvářejte multiplatformní aplikace a hry

Pomocí sady Visual Studio můžete vytvářet aplikace a hry pro macOS, Linux a Windows i pro Android, iOS a další [mobilní zařízení](https://visualstudio.microsoft.com/vs/mobile-app-development/).

- Sestavujte aplikace [.NET Core](/dotnet/core/) , které běží na Windows, MacOS a Linux.

- Vytvářejte mobilní aplikace pro iOS, Android a Windows v C# systémech a F# pomocí [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/).

- Používejte standardní webové technologie&mdash;HTML, CSS a JavaScriptu&mdash;k vytváření mobilních aplikací pro iOS, Android a Windows pomocí [Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/).

- Vytvářejte 2D a 3D hry v C# nástroji pomocí [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md).

- Vytvářejte nativní C++ aplikace pro zařízení s iOS, Androidem a Windows. Sdílejte společný kód v knihovnách postavených pro iOS, Android a Windows s využitím [ C++ pro vývoj pro různé platformy](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development).

- Nasazení, testování a ladění aplikací pro Android pomocí [emulátoru Androidu](../cross-platform/visual-studio-emulator-for-android.md).

## <a name="connect-to-databases"></a>Připojení k databázím

**Průzkumník serveru** vám pomůže najít a spravovat SQL Server instance a prostředky místně, vzdáleně a v Azure, Salesforce.com, Office 365 a websites. Chcete-li otevřít **Průzkumník serveru**, v hlavní nabídce vyberte možnost **Zobrazit** > **Průzkumník serveru**. Další informace o použití Průzkumník serveru naleznete v tématu [Add New Connections](../data-tools/add-new-connections.md).

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) je výkonné vývojové prostředí pro SQL Server, Azure SQL Database a Azure SQL Data Warehouse. Umožňuje sestavovat, ladit, udržovat a Refaktorovat databází. Můžete pracovat s projektem databáze, nebo přímo s připojeném databázovém instance nebo vypnout místně.

**Průzkumník objektů systému SQL Server** v aplikaci Visual Studio poskytuje zobrazení databázových objektů podobně jako SQL Server Management Studio. Průzkumník objektů systému SQL Server vám umožní provádět návrh a práci v databázi pro světlé řízení. Mezi příklady práce patří úpravy dat tabulek, porovnávání schémat a provádění dotazů pomocí kontextových nabídek přímo z Průzkumník objektů systému SQL Server a dalších.

![Průzkumník objektů systému SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Ladit, testovat a zlepšování kódu

Při psaní kódu, musíte ji spustit a otestovat chyb a výkonu. Špičkové ladicí systém sady Visual Studio umožňuje ladit kód spuštěný v místním projektu, na vzdáleném zařízení nebo v [emulátoru zařízení](../cross-platform/visual-studio-emulator-for-android.md). Můžete krokovat kód jeden příkaz najednou a kontrolovat proměnné, co využijete. Můžete nastavit zarážky, které jsou pouze přístupů, když je zadaná podmínka pravdivá. Možnosti ladění lze spravovat v editoru kódu samotném, takže nemusíte opustit kód. Další informace o ladění v aplikaci Visual Studio naleznete v tématu [první pohled na ladicí program](../debugger/debugger-feature-tour.md).

Chcete-li získat další informace o vylepšení výkonu aplikací, Zarezervujte funkci [profilace](../profiling/profiling-feature-tour.md) sady Visual Studio.

Pro [testování](../test/improve-code-quality.md)nabízí Visual Studio testování částí, Live Unit Testing, IntelliTest, zátěžové a výkonnostní testování a další. Visual Studio má také pokročilé možnosti [analýzy kódu](../code-quality/code-analysis-for-managed-code-overview.md) pro zachycení návrhu, zabezpečení a dalších typů vad.

## <a name="deploy-your-finished-application"></a>Nasazení dokončené aplikace

Když je vaše aplikace připravená k nasazení pro uživatele nebo zákazníky, Visual Studio poskytuje nástroje, které to dělají. Mezi možnosti nasazení patří Microsoft Store, na web služby SharePoint nebo pomocí technologie InstallShield nebo Instalační služba systému Windows. To je vše je přístupné prostřednictvím rozhraní IDE. Další informace najdete v tématu [nasazení aplikací, služeb a součástí](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Spravovat zdrojový kód a spolupracovat s ostatními

Můžete spravovat zdrojový kód v úložištích Git, jejichž hostitelem je libovolný poskytovatel, včetně Githubu. Nebo použijte [Azure DevOps Services](/azure/devops/index) ke správě kódu společně s chybami a pracovními položkami pro celý projekt. Další informace o správě úložišť Git v aplikaci Visual Studio pomocí Team Explorer najdete v tématu [Začínáme s Git a Azure Repos](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) . Visual Studio také poskytuje jiné funkce správy vestavěné zdrojového kódu. Další informace o těchto [funkcích naleznete v tématu nové funkce Git v aplikaci Visual Studio (blog)](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/).

Azure DevOps Services jsou cloudové služby pro plánování, hostování, automatizaci a nasazení softwaru a umožňují spolupráci v týmech. Azure DevOps Services podporuje úložiště Git (distribuovaná správa verzí) i Správa verzí Team Foundation (centralizované řízení verzí). Podporují kanály pro průběžné sestavování a vydávání kódu (CI/CD), který je uložený v systémech správy verzí. Služby Azure DevOps také podporu metodologie Scrum, CMMI a agilní vývoj.

Team Foundation Server (TFS) je Centrum správy životního cyklu aplikace pro sadu Visual Studio. Umožňuje všem uživatelům zapojené do procesu vývoje se zúčastnit prostřednictvím jediného řešení. TFS je užitečné při správě heterogenních týmům a projektům, příliš.

Pokud máte ve vaší síti organizaci Azure DevOps nebo Team Foundation Server, připojíte se k ní prostřednictvím okna **Team Explorer** v aplikaci Visual Studio. Z tohoto okna můžete zkontrolovat kód do nebo ze správy zdrojového kódu, správě pracovních položek, spusťte sestavení a přístup týmové místnosti a pracovní prostory. **Team Explorer** můžete otevřít z vyhledávacího pole nebo v hlavní nabídce ze **zobrazení** > **Team Explorer** nebo z **týmu** > **Spravovat připojení**.

Následující obrázek ukazuje okno **Team Explorer** pro řešení hostované v Azure DevOps Services.

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer_devops.png)

Můžete automatizovat proces sestavení k sestavení kódu, který ověří vývojáři ve vašem týmu do správy verzí. Lze například sestavit jeden nebo více projektů v noci nebo pokaždé, když je kód vrácen se změnami. Další informace najdete v tématu [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="extend-visual-studio"></a>Rozšíření sady Visual Studio

Pokud aplikace Visual Studio nemá přesně funkce, které potřebujete, můžete ho přidat! Přizpůsobení integrovaného vývojového prostředí založené na pracovním postupům a stylu, přidat podporu pro externí nástroje, které zatím nejsou se sadou Visual Studio integrované a upravit stávající funkce pro zvýšení produktivity. Nejnovější verzi Visual Studio Extensibility Tools (VS SDK) najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

.NET Compiler Platform ("Roslyn") můžete použít k tvorbě vlastních analyzátorů kódu a generátory kódu. Všechno, co potřebujete, najdete na adrese [Roslyn](https://github.com/dotnet/Roslyn).

Najděte [existující rozšíření](https://marketplace.visualstudio.com/vs) pro Visual Studio vytvořená vývojáři Microsoftu a naši vývojovou komunitou.

Další informace o rozšíření sady Visual Studio najdete v tématu [rozšíření integrovaného vývojového prostředí sady Visual Studio](https://visualstudio.microsoft.com/vs/extend/).

## <a name="see-also"></a>Viz také

- [Přehled integrovaného vývojového prostředí sady Visual Studio](../get-started/visual-studio-ide.md)
- [Co je nového v aplikaci Visual Studio 2017](../ide/whats-new-visual-studio-2017.md)
- [Co je nového v aplikaci Visual Studio 2019](../ide/whats-new-visual-studio-2019.md)
