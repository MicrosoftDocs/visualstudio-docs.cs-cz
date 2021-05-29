---
title: Pokročilé funkce
description: Seznamte se s pokročilými funkcemi, které můžou být vhodnější pro zkušené vývojáře nebo vývojáře, kteří už mají Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 51b25ff5f5f71291bb1aa1fd006b60566a576d7f
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687601"
---
# <a name="features-of-visual-studio"></a>Funkce Visual Studio

Základní [Visual Studio integrovaného vývojového prostředí (IDE)](../get-started/visual-studio-ide.md) obsahuje základní Visual Studio. Tento článek popisuje funkce, které můžou být vhodnější pro zkušené vývojáře nebo vývojáře, kteří už mají zkušenosti s Visual Studio.

## <a name="modular-installation"></a>Modulární instalace

Visual Studio modulární instalační program umožňuje zvolit a nainstalovat *úlohy.* Úlohy jsou skupiny funkcí potřebné pro programovací jazyk nebo platformu, které dáváte přednost. Tato strategie pomáhá zajistit menší nároky na Visual Studio, což znamená, že instalace a aktualizace jsou také rychlejší.

::: moniker range="vs-2017"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho zdarma.

::: moniker-end

Další informace o nastavení Visual Studio systému najdete v tématu [Instalace Visual Studio](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Vytváření aplikací s podporou cloudu pro Azure

Visual Studio nabízí sadu nástrojů, které umožňují snadno vytvářet cloudové aplikace využívající Microsoft Azure. Aplikace a služby můžete konfigurovat, sestavovat, ladit, zabalovat a nasazovat Microsoft Azure přímo z integrovaného vývojového prostředí.) Pokud chcete získat šablony projektů a nástrojů Azure, vyberte úlohu **Vývoj pro Azure** při instalaci Visual Studio.

![Úloha Vývoj pro Azure](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

Po instalaci úlohy **Vývoj pro Azure** jsou v dialogovém okně Nový projekt k dispozici následující **cloudové** šablony pro jazyk C#: 

![Šablony cloudových projektů pro Visual Studio](media/cloud-project-templates.png)

::: moniker-end

Visual Studio Průzkumník [cloudu umožňuje](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) zobrazit a spravovat cloudové prostředky založené na Azure v rámci Visual Studio. Tyto prostředky mohou zahrnovat virtuální počítače, tabulky, databáze SQL a další. **Průzkumník cloudu** zobrazuje prostředky Azure ve všech účtech spravovaných v rámci předplatného Azure, ke kterému jste se přihlásili. A pokud konkrétní operace vyžaduje Azure Portal, **Průzkumník cloudu** poskytuje odkazy, které vás zajímají na místo na portálu, kde potřebujete přejít.

![Průzkumník cloudu v aplikaci Visual Studio](media/cloud-explorer.png)

Můžete využívat služby Azure pro své aplikace pomocí **propojených služeb** , jako je:

- [Připojená služba Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service) , aby uživatelé mohli používat své účty z [Azure Active Directory](/azure/active-directory/active-directory-whatis) pro připojení k webovým aplikacím
- [Azure Storage připojená služba](/azure/vs-azure-tools-connected-services-storage) pro úložiště objektů blob, fronty a tabulky
- [Key Vault připojená služba](/azure/key-vault/vs-key-vault-add-connected-service) pro správu tajných kódů pro webové aplikace

Dostupné **připojené služby** závisí na typu projektu. Přidejte službu kliknutím pravým tlačítkem myši na projekt v **Průzkumník řešení** a výběrem možnosti **Přidat**  >  **připojenou službu**.

![Připojené služby sady Visual Studio](media/connected-services.png)

Další informace najdete v tématu [Přesun do cloudu pomocí sady Visual Studio a Azure](https://visualstudio.microsoft.com/vs/azure-tools/).

## <a name="create-apps-for-the-web"></a>Vytváření aplikací pro web

Webové jednotky našeho moderního světa a Visual Studio vám může pomáhat s psaním aplikací. Můžete vytvářet webové aplikace s využitím ASP.NET, Node.js, Pythonu, JavaScriptu a TypeScript. Visual Studio rozumí webovým rozhraním, jako jsou úhlová, jQuery, Express a další. ASP.NET Core a .NET Core běží na operačních systémech Windows, Mac a Linux. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) je hlavní aktualizace pro MVC, WebApi a Signal a běží v systémech Windows, Mac a Linux.  ASP.NET Core je od základu navržená tak, aby vám poskytovala štíhlou a sestavitelnou sadu .NET Stack pro vytváření moderních cloudových webových aplikací a služeb.

Další informace najdete v tématu [moderní webové nástroje](https://visualstudio.microsoft.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Vytváření aplikací a her pro různé platformy

Pomocí nástroje Visual Studio vytvářet aplikace a hry pro macOS, Linux a Windows a také pro Android, iOS a další [mobilní zařízení.](https://visualstudio.microsoft.com/vs/mobile-app-development/)

- [Vytvářete aplikace .NET Core,](/dotnet/core/) které běží na Windows, macOS a Linuxu.

- Vytváření mobilních aplikací pro iOS, Android a Windows v jazyce C# a F# pomocí [Xamarinu](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/)

- Vytváření 2D a 3D her v jazyce C# pomocí [Visual Studio Tools for Unity](/gamedev/unity/get-started/visual-studio-tools-for-unity.md).

- Vytváření nativních aplikací C++ pro zařízení s iOSem, Androidem a Windows Sdílejte společný kód v knihovnách sestavených pro iOS, Android a Windows pomocí [jazyka C++ pro vývoj pro více platforem.](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development)

## <a name="connect-to-databases"></a>Připojení k databázím

**Průzkumník serveru** vám pomůže procházet a spravovat SQL Server a prostředky místně, vzdáleně a v Azure, Salesforce.com, Microsoft 365 a webech. Pokud chcete **Průzkumník serveru**, v hlavní nabídce zvolte **Zobrazit** Průzkumník serveru  >  . Další informace o používání služby Průzkumník serveru tématu [Přidání nových připojení.](../data-tools/add-new-connections.md)

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) je výkonné vývojové prostředí pro SQL Server, Azure SQL Database a Azure SQL Data Warehouse. Umožňuje sestavovat, ladit, udržovat a refaktorovat databáze. Můžete pracovat s databázovým projektem nebo přímo s připojenou instancí databáze místně nebo mimo něj.

**Průzkumník objektů systému SQL Server** v Visual Studio poskytuje zobrazení databázových objektů podobně jako SQL Server Management Studio. Průzkumník objektů systému SQL Server umožňuje nenároční správu databází a návrh. Mezi pracovní příklady patří úpravy tabulkových dat, porovnání schémat, spouštění dotazů pomocí kontextových nabídek přímo Průzkumník objektů systému SQL Server a další.

![Průzkumník objektů systému SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Ladění, testování a vylepšování kódu

Když píšete kód, musíte ho spustit a otestovat, jestli nesnídá chyby a výkon. Visual Studio špičkový systém ladění umožňuje ladit kód spuštěný v místním projektu, na vzdáleném zařízení nebo v [emulátoru zařízení.](../cross-platform/visual-studio-emulator-for-android.md) Můžete procházet kód po jednom příkazu a kontrolovat proměnné, jak chcete. Můžete nastavit zarážky, které budou k dispozice pouze v případě, že je zadaná podmínka pravdivá. Možnosti ladění lze spravovat v editoru kódu samotném, takže nemusíte opustit kód. Další informace o ladění v aplikaci Visual Studio naleznete v tématu [první pohled na ladicí program](../debugger/debugger-feature-tour.md).

Chcete-li získat další informace o vylepšení výkonu aplikací, Zarezervujte funkci [profilace](../profiling/profiling-feature-tour.md) sady Visual Studio.

Pro [testování](../test/improve-code-quality.md)nabízí Visual Studio testování částí, Live Unit Testing, IntelliTest, zátěžové a výkonnostní testování a další. Visual Studio má také pokročilé možnosti [analýzy kódu](../code-quality/code-analysis-for-managed-code-overview.md) pro zachycení návrhu, zabezpečení a dalších typů vad.

## <a name="deploy-your-finished-application"></a>Nasazení dokončené aplikace

Když je vaše aplikace připravená k nasazení pro uživatele nebo zákazníky, Visual Studio poskytuje nástroje, které to dělají. Mezi možnosti nasazení patří Microsoft Store, na web služby SharePoint nebo pomocí technologie InstallShield nebo Instalační služba systému Windows. Vše je přístupné prostřednictvím integrovaného vývojového prostředí (IDE). Další informace najdete v tématu [nasazení aplikací, služeb a součástí](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Spravujte zdrojový kód a spolupracujte s ostatními

Zdrojový kód můžete spravovat v úložištích Git hostovaných libovolným poskytovatelem, včetně GitHubu. Nebo použijte [Azure DevOps Services](/azure/devops/index) ke správě kódu společně s chybami a pracovními položkami pro celý projekt. Další informace o správě úložišť Git v aplikaci Visual Studio pomocí Team Explorer najdete v tématu [Začínáme s Git a Azure Repos](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) . Visual Studio také obsahuje další integrované funkce správy zdrojového kódu. Další informace o těchto [funkcích naleznete v tématu nové funkce Git v aplikaci Visual Studio (blog)](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/).

Azure DevOps Services jsou cloudové služby pro plánování, hostování, automatizaci a nasazení softwaru a umožňují spolupráci v týmech. Azure DevOps Services podporuje úložiště Git (distribuovaná správa verzí) i Správa verzí Team Foundation (centralizované řízení verzí). Podporují kanály pro průběžné sestavování a vydávání kódu (CI/CD), který je uložený v systémech správy verzí. Azure DevOps Services také podporuje metodologie vývoje Pro Scrum, CMMI a Agilní vývoj.

Team Foundation Server (TFS) je centrum správy životního cyklu aplikací pro Visual Studio. Umožňuje všem uživatelům zapojeným do procesu vývoje účastnit se používání jednoho řešení. Sada TFS je užitečná také pro správu heterogenních týmů a projektů.

Pokud máte ve Azure DevOps organizaci nebo Team Foundation Server, připojíte se k ní prostřednictvím okna **Team Explorer** v Visual Studio. V tomto okně můžete kontrolovat kód do nebo ze správy zdrojového kódu, spravovat pracovní položky, začít vytvářet buildy a přistupovat k týmových místnostem a pracovním prostorům. Můžete otevřít **Team Explorer** z vyhledávacího pole nebo v hlavní nabídce v části **Zobrazit** Team Explorer nebo v části  >     >  **Týmová správa připojení**.

Následující obrázek ukazuje okno **Team Explorer** řešení, které je hostované v Azure DevOps Services.

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer_devops.png)

Můžete také automatizovat proces sestavení a sestavit kód, který vývojáři ve vašem týmu přihlásili ke kontrole verzí. Lze například sestavit jeden nebo více projektů v noci nebo pokaždé, když je kód vrácen se změnami. Další informace najdete v tématu [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

## <a name="extend-visual-studio"></a>Rozšiřování sady Visual Studio

Pokud Visual Studio přesně tu funkci, kterou potřebujete, můžete ji přidat. Integrované vývojové prostředí můžete přizpůsobit na základě pracovního postupu a stylu, přidat podporu externích nástrojů, které ještě nejsou integrované s Visual Studio, a upravit stávající funkce pro zvýšení produktivity. Pokud chcete najít nejnovější verzi sady Visual Studio Extensibility Tools (VS SDK), podívejte se [na Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

Pomocí sady .NET Compiler Platform (Roslyn) můžete psát vlastní analyzátory kódu a generátory kódu. Všechno, co potřebujete, najdete [v roslynu.](https://github.com/dotnet/Roslyn)

Najděte [stávající rozšíření](https://marketplace.visualstudio.com/vs) pro Visual Studio, která vytvořili vývojáři Microsoftu, a také naši komunitu vývojářů.

Další informace o rozšíření Visual Studio najdete v tématu [Rozšíření Visual Studio IDE.](https://visualstudio.microsoft.com/vs/extend/)

## <a name="see-also"></a>Viz také

- [Visual Studio integrovaného vývojového prostředí (IDE)](../get-started/visual-studio-ide.md)
- [Novinky v sadě Visual Studio 2017](../ide/whats-new-visual-studio-2017.md)
- [Co je nového v Visual Studio 2019](../ide/whats-new-visual-studio-2019.md)
