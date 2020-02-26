---
title: Vytvoření webové aplikace v ASP.NET CoreC#
description: Zjistěte, jak vytvořit jednoduchou webovou aplikaci Hello World v sadě Visual Studio s C# a ASP.NET Core, krok za krokem.
ms.custom: mvc,seodec18
ms.date: 11/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 1873c11d8f2e6243a0dc0f867e579f1927cd1607
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579960"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Rychlý start: Použití sady Visual Studio k vytvoření vaší první webové aplikace ASP.NET Core

V tomto úvodu 5 až 10 minut na tom, jak pomocí sady Visual Studio vytvoříte jednoduchou webovou aplikaci "Hello World" pomocí šablony projektu ASP.NET a programovací jazyk C#.

## <a name="before-you-begin"></a>Než začnete

### <a name="install-visual-studio"></a>Instalace sady Visual Studio

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Zvolte motiv (volitelné)

Tento rychlý úvodní kurz obsahuje snímky obrazovky, použít tmavý motiv. Pokud nepoužíváte tmavý motiv, ale chcete, přečtěte si téma [přizpůsobení stránky IDE a editoru sady Visual Studio](quickstart-personalize-the-ide.md) , kde se dozvíte, jak.

## <a name="create-a-project"></a>Vytvoření projektu

Pokud chcete začít, vytvoříte projekt webové aplikace ASP.NET Core. Typ projektu obsahuje všechny soubory šablon pro vytvoření webové aplikace, než dokonce cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek vyberte **soubor** > **Nový** > **projekt**.

1. V levém podokně dialogového okna **Nový projekt** rozbalte položku **C#Visual**a pak zvolte možnost **.NET Core**. V prostředním podokně vyberte **ASP.NET Core webová aplikace**. <br/><br/>Pak název souboru `HelloWorld` a zvolte **OK**.

   ![Vytvořit nový projekt ASP.NET Core webové aplikace proC#](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Pokud nevidíte kategorii šablony projektu **.NET Core** , klikněte na odkaz **otevřít instalační program pro Visual Studio** v levém podokně. (V závislosti na nastavení zobrazení může být potřeba stránku posunout, aby ji.)
   >
   > ![Otevřít instalační program sady Visual Studio z dialogového okna Nový projekt](../ide/media/open-visual-studio-installer.png)
   >
   > Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje ASP.NET a webu** a pak zvolte možnost **Upravit**.
   >
   > ![Úlohy technologie ASP.NET v instalačním programu VS](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Může mít ukončit sadu Visual Studio, abyste mohli pokračovat v instalaci nové úlohy.)

1. V dialogovém okně **Nová webová aplikace ASP.NET Core** v horním rozevíracím seznamu vyberte **ASP.NET Core 2,1** . V dalším kroku zvolte možnost **Webová aplikace**a pak klikněte na **tlačítko OK**.

   ![Dialogové okno Nová webová aplikace ASP.NET Core](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Pokud nevidíte **ASP.NET Core 2,1**, ujistěte se, že používáte nejnovější verzi sady Visual Studio. Další informace o tom, jak aktualizovat instalaci, najdete na stránce o [aktualizaci sady Visual Studio na nejnovější verzi](../install/update-visual-studio.md) .

Brzy NATO Visual Studio otevře soubor projektu.

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete sadu Visual Studio.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   ![Zobrazit okno vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **vytvořit nový projekt** zadejte nebo do vyhledávacího pole zadejte *ASP.NET* . Dále zvolte **C#** ze seznamu jazyk a v seznamu platforma zvolte možnost **Windows** .

   Po použití filtrů jazyků a platforem zvolte šablonu **ASP.NET Core webové aplikace** a klikněte na tlačítko **Další**.

   ![Zvolit C# šablonu pro ASP.NET Core webovou aplikaci](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **ASP.NET Core webové aplikace** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .
   >
   > ![Odkaz pro instalaci dalších nástrojů a funkcí v okně vytvořit nový projekt v části nenajít, co hledáte?](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Pak v Instalační program pro Visual Studio zvolte úlohu **vývoje ASP.NET a web** .
   >
   > ![ASP.NET Core úlohy webové aplikace v Instalační program pro Visual Studio](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Potom klikněte na tlačítko **Upravit** v instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce; Pokud ano, udělejte to. V dalším kroku vyberte **pokračovat** a nainstalujte úlohu. Pak se vraťte ke kroku 2 v tomto postupu "[Vytvoření projektu](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *HelloWorld* do pole **název projektu** . Pak zvolte **vytvořit**.

   ![v okně Konfigurovat nový projekt pojmenujte svůj projekt HelloWorld.](../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png)

1. V okně **vytvořit novou webovou aplikaci ASP.NET Core** ověřte, zda se v horní rozevírací nabídce zobrazí **ASP.NET Core 3,0** . Pak zvolte **Webová aplikace**, která obsahuje například Razor Pages. Pak vyberte **vytvořit**.

   ![Okno vytvořit novou ASP.NET Core webovou aplikaci](../get-started/csharp/media/vs-2019/csharp-create-aspnet-razor-pages-app.png)

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-and-run-the-app"></a>Vytvoření a spuštění aplikace

::: moniker range="vs-2017"

1. V **Průzkumník řešení**rozbalte složku **stránky** a zvolte možnost **o. cshtml**.

   ![Zvolte soubor About.cshtml z Průzkumníka řešení](../ide/media/csharp-aspnet-about-page-html-file.png)

   Tento soubor odpovídá stránce s názvem **o** ve webové aplikaci, která běží ve webovém prohlížeči.

   ![Na stránce o ve webové aplikaci](../ide/media/csharp-aspnet-about-page.png)

   V editoru uvidíte kód HTML v oblasti "Další informace" na stránce **About** .

   ![Kód HTML pro doplňkovou oblast informací v editoru sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Změnou textu "Další informace" Přečtěte "**Hello World!** ".

   ![Změna výchozího kódu HTML pro další informace o oblasti v editoru sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. V **Průzkumník řešení**rozbalte položku **About. cshtml**a pak zvolte možnost **About.cshtml.cs**. (Tento soubor také odpovídá stránce **o** stránku ve webovém prohlížeči.)

   ![Zvolte soubor About.cshtml z Průzkumníka řešení](../ide/media/csharp-aspnet-about-page-code-file.png)

   V editoru uvidíte C# kód, který obsahuje text pro oblast Popis aplikace na stránce **o produktu** .

   ![C# Kód oblasti Popis aplikace v editoru sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Změňte text zprávy "Popis aplikace", abyste si přečetli "**co je moje zpráva?** ".

   ![Změna výchozího textu zprávy pro oblast popisu aplikace v editoru sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Zvolte **IIS Express** nebo stiskněte **CTRL**+**F5** a spusťte aplikaci a otevřete ji ve webovém prohlížeči.

   ![Výběr tlačítka IIS Express v aplikaci Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Pokud se zobrazí chybová zpráva s oznámením, že se **nelze připojit k webovému serveru ' IIS Express '** nebo chybová zpráva, která uvádí certifikát protokolu SSL, ukončete aplikaci Visual Studio. Dále otevřete aplikaci Visual Studio pomocí možnosti **Spustit jako správce** z místní nabídky klikněte pravým tlačítkem myši. Spusťte aplikaci znovu.

1. Ve webovém prohlížeči ověřte, zda stránka **o produktu** obsahuje aktualizovaný text.

   ![Zobrazit aktualizované informace o stránce, která obsahuje změny, které jste provedli](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Zavřete webový prohlížeč.

### <a name="review-your-work"></a>Kontrola práce

Prohlédněte si následující animaci a zkontrolujte práci, kterou jste dokončili v předchozí části.

  ![Podívejte se na animovaný soubor. gif, který ukazuje, jak vytvořit a spustit C# jednoduchou webovou aplikaci ASP.NET Core v aplikaci Visual Studio.](../ide/media/csharp-aspnet-animated-hello-world.gif)

Blahopřejeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli ještě něco o jazyce C#, ASP.NET Core a Visual Studio IDE (integrované vývojové prostředí).

::: moniker-end

::: moniker range="vs-2019"

1. V **Průzkumník řešení**rozbalte složku **stránky** a pak zvolte **index. cshtml**.

   ![Vyberte soubor index. cshtml z Průzkumník řešení](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Tento soubor odpovídá stránce s názvem **Domů** ve webové aplikaci, která běží ve webovém prohlížeči.

   ![Na stránce o ve webové aplikaci](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   V editoru uvidíte kód HTML pro text, který se zobrazí na **domovské** stránce.

   ![Kód HTML v souboru index. cshtml pro domovskou stránku v editoru sady Visual Studio](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. Změňte úvodní text tak, aby se načetl**Hello World!** .

   ![V editoru sady Visual Studio změňte výchozí kód HTML, který říká úvodní Hello World místo toho.](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Zvolte **IIS Express** nebo stiskněte **CTRL**+**F5** a spusťte aplikaci a otevřete ji ve webovém prohlížeči.

   ![Výběr tlačítka IIS Express v aplikaci Visual Studio](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > Pokud se zobrazí chybová zpráva s oznámením, že se **nelze připojit k webovému serveru ' IIS Express '** nebo chybová zpráva, která uvádí certifikát protokolu SSL, ukončete aplikaci Visual Studio. Dále otevřete aplikaci Visual Studio pomocí možnosti **Spustit jako správce** z místní nabídky klikněte pravým tlačítkem myši. Spusťte aplikaci znovu.

1. Ve webovém prohlížeči ověřte, zda je na **domovské** stránce zahrnut aktualizovaný text.

   ![Zobrazit aktualizovanou domovskou stránku, která obsahuje změny, které jste provedli](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Zavřete webový prohlížeč.

::: moniker-end

## <a name="next-steps"></a>Další kroky

Další informace najdete v následujícím kurzu:

> [!div class="nextstepaction"]
> [Začínáme s C# a ASP.NET v prostředí Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Viz také

[Publikování webové aplikace pro Azure App Service pomocí sady Visual Studio](../deployment/quickstart-deploy-to-azure.md)
