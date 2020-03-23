---
title: 'Vytvoření webové aplikace ASP.NET Core v C #'
description: Přečtěte si, jak vytvořit jednoduchou webovou aplikaci Hello World v Sadě Visual Studio s C# a ASP.NET Core, krok za krokem.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579960"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Úvodní příručka: Vytvoření první ASP.NET webové aplikace pomocí Visual Studia

V tomto 5-10 minut úvod, jak používat Visual Studio, vytvoříte jednoduchou webovou aplikaci "Hello World" pomocí šablony ASP.NET projektu a programovacího jazyka C#.

## <a name="before-you-begin"></a>Než začnete

### <a name="install-visual-studio"></a>Instalace sady Visual Studio

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Vyberte si motiv (volitelné)

Tento úvodní kurz obsahuje snímky obrazovky, které používají tmavý motiv. Pokud nepoužíváte tmavý motiv, ale chcete, podívejte se na [stránku Přizpůsobit ide a editor u visual ateliéru,](quickstart-personalize-the-ide.md) kde se dozvíte, jak na to.

## <a name="create-a-project"></a>Vytvoření projektu

Chcete-li začít, vytvoříte projekt webové aplikace ASP.NET Core. Typ projektu je dodáván se všemi soubory šablon pro vytvoření webové aplikace, ještě předtím, než něco přidáte!

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

1. V levém podokně dialogového okna **Nový projekt** rozbalte **položku Visual C#** a pak zvolte **.NET Core**. V prostředním podokně zvolte **ASP.NET Základní webová aplikace**. <br/><br/>Potom pojmenujte `HelloWorld` soubor a zvolte **OK**.

   ![Vytvoření nového projektu ASP.NET základní webové aplikace pro C #](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Pokud kategorii šablony projektu **.NET Core** nevidíte, zvolte v levém podokně odkaz Otevřít instalační program **sady Visual Studio.** (V závislosti na nastavení zobrazení může být nutné jej zobrazit posunutím.)
   >
   > ![Otevření Instalační služby sady Visual Studio z dialogového okna nového projektu](../ide/media/open-visual-studio-installer.png)
   >
   > Spustí se instalační program pro Visual Studio. Zvolte **ASP.NET a zatížení vývoje webu** a pak zvolte **Změnit**.
   >
   > ![ASP.NET zatížení v Instalačníslužbě VS](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Možná budete muset zavřít Visual Studio před pokračováním v instalaci nové úlohy.)

1. V dialogovém **okně Nová ASP.NET základní webová aplikace** vyberte v horní rozevírací nabídce ASP.NET **Jádrem 2.1.** Dále zvolte **Webová aplikace**a pak zvolte **OK**.

   ![Dialogové okno Nová ASP.NET základní webová aplikace](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Pokud nevidíte **ASP.NET Jádrem 2.1**, ujistěte se, že používáte nejnovější verzi sady Visual Studio. Další informace o aktualizaci instalace naleznete na [stránce Aktualizace sady Visual Studio na nejnovější](../install/update-visual-studio.md) verzi.

Brzy poté visual studio otevře soubor projektu.

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete sadu Visual Studio.

1. V počátečním okně zvolte **Vytvořit nový projekt**.

   ![Zobrazit okno Vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **Vytvořit nový projekt** zadejte nebo zadejte *ASP.NET* do vyhledávacího pole. Dále zvolte **C#** ze seznamu jazyk a pak zvolte **Windows** ze seznamu platformy.

   Po použití filtrů jazyka a platformy zvolte **šablonu ASP.NET Základní webová aplikace** a pak zvolte **Další**.

   ![Zvolte šablonu Jazyka C# pro základní ASP.NET webovou aplikaci](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > Pokud šablonu **ASP.NET základní webové aplikace** nevidíte, můžete ji nainstalovat z okna Vytvořit nový **projekt.** Ve zprávě **Install more tools and features** **Nenajít to, co hledáte?**
   >
   > ![Odkaz "Nainstalovat další nástroje a funkce" ze zprávy "Nenajít to, co hledáte" v okně "Vytvořit nový projekt"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Potom v Instalační službě sady Visual Studio zvolte **úlohu ASP.NET a vývoj webových** aplikací.
   >
   > ![ASP.NET úlohy základní webové aplikace v Instalační službě sady Visual Studio](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Poté zvolte tlačítko **Změnit** v Instalační službě sady Visual Studio. Můžete být vyzváni k uložení práce. pokud ano, uvažte tak. Dále zvolte **Pokračovat** k instalaci úlohy. Potom se vraťte ke kroku 2 v tomto postupu "[Vytvořit projekt](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *HelloWorld* do pole **Název projektu.** Potom zvolte **Vytvořit**.

   ![v okně Konfigurace nového projektu pojmenujte projekt HelloWorld](../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png)

1. V okně **Vytvořit novou ASP.NET základní webové aplikace** ověřte, zda se v horní rozevírací nabídce zobrazí ASP.NET **jádra 3.0.** Potom zvolte **Webovou aplikaci**, která obsahuje příklady Razor Pages. Dále zvolte **Vytvořit**.

   ![Okno Vytvořit novou ASP.NET základní webovou aplikaci](../get-started/csharp/media/vs-2019/csharp-create-aspnet-razor-pages-app.png)

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-and-run-the-app"></a>Vytvoření a spuštění aplikace

::: moniker range="vs-2017"

1. V **Průzkumníku řešení**rozbalte složku **Stránky** a pak zvolte **About.cshtml**.

   ![Zvolte soubor About.cshtml z Průzkumníka řešení.](../ide/media/csharp-aspnet-about-page-html-file.png)

   Tento soubor odpovídá stránce s názvem **About** ve webové aplikaci, která se spouští ve webovém prohlížeči.

   ![Stránka Informace ve webové aplikaci](../ide/media/csharp-aspnet-about-page.png)

   V editoru uvidíte html kód pro oblast "další informace" na stránce **Informace.**

   ![Kód HTML pro další informační oblast v editoru sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Změňte text "další informace" na text "**Hello World!**".

   ![Změna výchozího kódu HTML pro další informační oblast v editoru Sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. V **Průzkumníku řešení**rozbalte **položku About.cshtml**a pak zvolte **About.cshtml.cs**. (Tento soubor také odpovídá stránce **Informace** ve webovém prohlížeči.)

   ![Zvolte soubor About.cshtml z Průzkumníka řešení.](../ide/media/csharp-aspnet-about-page-code-file.png)

   V editoru uvidíte kód Jazyka C#, který obsahuje text pro oblast "popis aplikace" na stránce **O aplikaci.**

   ![Kód Jazyka C# pro oblast popisu aplikace v editoru Sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Změňte text zprávy "popis aplikace" na text "**Co je moje zpráva?**".

   ![Změna výchozího textu zprávy pro oblast popisu aplikace v editoru Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Zvolte **IIS Express** nebo stisknutím **ctrl**+**f5** spusťte aplikaci a otevřete ji ve webovém prohlížeči.

   ![Výběr tlačítka IIS Express v sadě Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Pokud se zobrazí chybová zpráva, která **říká, nelze se připojit k webovému serveru IIS Express**nebo chybová zpráva, která zmiňuje certifikát SSL, zavřete Visual Studio. Potom otevřete Visual Studio pomocí **možnosti Spustit jako správce** z kontextové nabídky po kliknutí pravým tlačítkem myši. Potom spusťte aplikaci znovu.

1. Ve webovém prohlížeči ověřte, zda stránka **Informace** obsahuje aktualizovaný text.

   ![Zobrazení aktualizované stránky Informace obsahující provedené změny](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Zavřete webový prohlížeč.

### <a name="review-your-work"></a>Kontrola práce

V následující animaci zkontrolujte práci, kterou jste dokončili v předchozí části.

  ![Zobrazení animovaného souboru GIF, který ukazuje, jak vytvořit a spustit jednoduchou webovou aplikaci C# ASP.NET Core v sadě Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

Gratulujeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli něco o C#, ASP.NET Core a IDE visual studio (integrované vývojové prostředí).

::: moniker-end

::: moniker range="vs-2019"

1. V **Průzkumníku řešení**rozbalte složku **Stránky** a pak zvolte **Index.cshtml**.

   ![Výběr souboru Index.cshtml z Průzkumníka řešení](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Tento soubor odpovídá stránce s názvem **Domů** ve webové aplikaci, která se spouští ve webovém prohlížeči.

   ![Stránka Informace ve webové aplikaci](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   V editoru uvidíte kód HTML pro text, který se zobrazí na **domovské** stránce.

   ![Kód HTML v souboru Index.cshtml pro domovskou stránku v editoru Sady Visual Studio](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. Změňte text "Vítejte" na čtení "**Hello World!**".

   ![V editoru Visual Studio změňte výchozí kód HTML s nápisem Welcome to Say World](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Zvolte **IIS Express** nebo stisknutím **ctrl**+**f5** spusťte aplikaci a otevřete ji ve webovém prohlížeči.

   ![Výběr tlačítka IIS Express v sadě Visual Studio](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > Pokud se zobrazí chybová zpráva, která **říká, nelze se připojit k webovému serveru IIS Express**nebo chybová zpráva, která zmiňuje certifikát SSL, zavřete Visual Studio. Potom otevřete Visual Studio pomocí **možnosti Spustit jako správce** z kontextové nabídky po kliknutí pravým tlačítkem myši. Potom spusťte aplikaci znovu.

1. Ve webovém prohlížeči ověřte, zda **domovská** stránka obsahuje aktualizovaný text.

   ![Zobrazení aktualizované domovské stránky obsahující provedené změny](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Zavřete webový prohlížeč.

::: moniker-end

## <a name="next-steps"></a>Další kroky

Další informace najdete v následujícím kurzu:

> [!div class="nextstepaction"]
> [Začínáme s C# a ASP.NET v Sadě Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Viz také

[Publikování webové aplikace do služby Azure App Service pomocí Visual Studia](../deployment/quickstart-deploy-to-azure.md)
