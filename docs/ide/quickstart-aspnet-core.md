---
title: 'Vytvoření webové aplikace v ASP.NET Core v jazyce C #'
description: Naučte se, jak vytvořit jednoduchou webovou aplikaci Hello World v aplikaci Visual Studio pomocí C# a ASP.NET Core, krok za krokem.
ms.custom: acquisition, mvc,seodec18
ms.date: 11/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 61fc3f0cf1e23dcf0f9e22ed7e10050fb84c9ba6
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308061"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Rychlý Start: použití sady Visual Studio k vytvoření první ASP.NET Core webové aplikace

V této 5-10 minut Úvod k používání sady Visual Studio vytvoříte jednoduchou webovou aplikaci "Hello World" pomocí šablony projektu ASP.NET a programovacího jazyka C#.

## <a name="before-you-begin"></a>Než začnete

### <a name="install-visual-studio"></a>Instalace sady Visual Studio

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2022"

Pokud jste ještě nenainstalovali Visual Studio 2022 Preview, nainstalujte ho zdarma na stránku [Visual studio 2022 Preview ke stažení](https://visualstudio.microsoft.com/vs/preview/vs2022) .

::: moniker-end

### <a name="choose-your-theme-optional"></a>Vyberte svůj motiv (volitelné).

Tento rychlý úvodní kurz obsahuje snímky obrazovky, které používají tmavý motiv. Pokud nepoužíváte tmavý motiv, ale chcete, přečtěte si téma [přizpůsobení stránky IDE a editoru sady Visual Studio](quickstart-personalize-the-ide.md) , kde se dozvíte, jak.

## <a name="create-a-project"></a>Vytvoření projektu

Začněte tím, že vytvoříte projekt webové aplikace ASP.NET Core. Typ projektu obsahuje všechny soubory šablon pro vytvoření webové aplikace, než dokonce cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek vyberte **soubor** > **Nový** > **projekt**.

1. V levém podokně dialogového okna **Nový projekt** rozbalte položku **Visual C#** a pak zvolte možnost **.NET Core**. V prostředním podokně vyberte **ASP.NET Core webová aplikace**. <br/><br/>Pak zadejte název souboru `HelloWorld` a zvolte **OK**.

   ![Vytvoření nového projektu webové aplikace ASP.NET Core pro jazyk C #](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Pokud nevidíte kategorii šablony projektu **.NET Core** , klikněte na odkaz **otevřít instalační program pro Visual Studio** v levém podokně. (V závislosti na nastaveních zobrazení se možná budete muset posouvat, abyste ho viděli.)
   >
   > ![Otevření Instalační program pro Visual Studio z dialogového okna Nový projekt](../ide/media/open-visual-studio-installer.png)
   >
   > Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje ASP.NET a webu** a pak zvolte možnost **Upravit**.
   >
   > ![ASP.NET úlohy v instalačním programu VS](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Před pokračováním v instalaci nové úlohy může být nutné zavřít Visual Studio.)

1. V dialogovém okně **Nová webová aplikace ASP.NET Core** v horním rozevíracím seznamu vyberte **ASP.NET Core 2,1** . V dalším kroku zvolte možnost **Webová aplikace** a pak klikněte na **tlačítko OK**.

   ![Dialogové okno Nová webová aplikace ASP.NET Core](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Pokud nevidíte **ASP.NET Core 2,1**, ujistěte se, že používáte nejnovější verzi sady Visual Studio. Další informace o tom, jak aktualizovat instalaci, najdete na stránce o [aktualizaci sady Visual Studio na nejnovější verzi](../install/update-visual-studio.md) .

Brzy poté aplikace Visual Studio otevře soubor projektu.

::: moniker-end

::: moniker range=">=vs-2019"

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   :::image type="content" source="../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="Zobrazit okno vytvořit nový projekt":::

1. V okně **vytvořit nový projekt** vyberte v seznamu jazyk položku **C#** . V dalším kroku vyberte možnost **Windows** ze seznamu platforem a **Web** ze seznamu typy projektů.

      Po použití filtrů typu jazyk, platforma a typ projektu vyberte šablonu **ASP.NET Core webové aplikace** a klikněte na tlačítko **Další**.

   :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="Zvolit šablonu C# pro ASP.NET Core webovou aplikaci":::

   > [!NOTE]
   > Pokud nevidíte šablonu **ASP.NET Core webové aplikace** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .
   >
   > ![Odkaz pro instalaci dalších nástrojů a funkcí v okně vytvořit nový projekt v části nenajít, co hledáte?](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Pak v Instalační program pro Visual Studio zvolte úlohu **vývoje ASP.NET a web** .
   >
   > ![Úlohy vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Potom klikněte na tlačítko **Upravit** v instalační program pro Visual Studio. Pokud budete vyzváni k uložení práce, udělejte to. V dalším kroku vyberte **pokračovat** a nainstalujte úlohu. Pak se vraťte ke kroku 2 v tomto postupu "[Vytvoření projektu](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *HelloWorld* do pole **název projektu** . Pak klikněte na tlačítko **Další**.

    :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png" alt-text="v okně Konfigurovat nový projekt pojmenujte projekt ' MyCoreApp '.":::

1. V okně **Další informace** ověřte, že se v horní rozevírací nabídce zobrazuje **.NET Core 3,1** . Všimněte si, že se můžete rozhodnout povolit podporu Docker zaškrtnutím políčka. Podporu ověřování můžete také přidat kliknutím na tlačítko změnit ověřování. Odtud si můžete vybrat z těchto:
    - Žádné: žádné ověřování.
    - Jednotlivé účty: tyto jsou uložené v místní databázi nebo databázi založené na Azure.
    - Microsoft Identity Platform: Tato možnost pro ověřování používá službu Active Directory, Azure AD nebo Microsoft 365.
    - Windows: vhodné pro intranetové aplikace.
    
    Nechejte políčko **Povolit Docker** nezaškrtnuté a jako typ ověřování vyberte **žádné** . Potom vyberte **Vytvořit**.

   :::image type="content" source="../get-started/csharp/media/vs-2019/aspnet-core-additional-information.png" alt-text="v okně Další informace se ujistěte, že je vybraná možnost .NET Core 3,1 a ponechání všech výchozích hodnot.":::

   V aplikaci Visual Studio se otevře nový projekt.

::: moniker-end

## <a name="create-and-run-the-app"></a>Vytvoření a spuštění aplikace

::: moniker range="vs-2017"

1. V **Průzkumník řešení** rozbalte složku **stránky** a zvolte možnost **o. cshtml**.

   ![Snímek obrazovky sady Visual Studio Průzkumník řešení zobrazení souborů v projektu HelloWorld Složka stránky je rozbalena a je vybrána možnost o. cshtml.](../ide/media/csharp-aspnet-about-page-html-file.png)

   Tento soubor odpovídá stránce s názvem **o** ve webové aplikaci, která běží ve webovém prohlížeči.

   ![Stránka o službě ve webové aplikaci](../ide/media/csharp-aspnet-about-page.png)

   V editoru uvidíte kód HTML v oblasti "Další informace" na stránce **About** .

   ![Kód HTML pro doplňkovou oblast informací v editoru sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Změnou textu "Další informace" Přečtěte "**Hello World!**".

   ![Změna výchozího kódu HTML pro další informace o oblasti v editoru sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. V **Průzkumník řešení** rozbalte položku **About. cshtml** a potom zvolte **About. cshtml. cs**. (Tento soubor také odpovídá stránce **o** stránku ve webovém prohlížeči.)

   ![Snímek obrazovky sady Visual Studio Průzkumník řešení zobrazení souborů v projektu HelloWorld O. cshtml je rozbalený a je v něm vybraná možnost About. cshtml. cs.](../ide/media/csharp-aspnet-about-page-code-file.png)

   V editoru uvidíte kód C#, který obsahuje text pro oblast Popis aplikace na stránce **o produktu** .

   ![Kód jazyka C# pro oblast popisu aplikace v editoru sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Změňte text zprávy "Popis aplikace", abyste si přečetli "**co je moje zpráva?**".

   ![Změna výchozího textu zprávy pro oblast popisu aplikace v editoru sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Zvolte **IIS Express** nebo stiskněte **klávesu CTRL** + **F5** a spusťte aplikaci a otevřete ji ve webovém prohlížeči.

   ![Výběr tlačítka IIS Express v aplikaci Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Pokud se zobrazí chybová zpráva s oznámením, že se **nelze připojit k webovému serveru ' IIS Express '** nebo chybová zpráva, která uvádí certifikát protokolu SSL, ukončete aplikaci Visual Studio. Dále otevřete aplikaci Visual Studio pomocí možnosti **Spustit jako správce** z místní nabídky klikněte pravým tlačítkem myši. Pak aplikaci spusťte znovu.

1. Ve webovém prohlížeči ověřte, zda stránka **o produktu** obsahuje aktualizovaný text.

   ![Zobrazit aktualizované informace o stránce, která obsahuje změny, které jste provedli](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Zavřete webový prohlížeč.

### <a name="review-your-work"></a>Kontrola práce

Prohlédněte si následující animaci a zkontrolujte práci, kterou jste dokončili v předchozí části.

  ![Zobrazit animovaný .gif soubor, který ukazuje, jak vytvořit a spustit jednoduchou webovou aplikaci v C# ASP.NET Core v aplikaci Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

Blahopřejeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli trochu o jazyce C#, ASP.NET Core a integrovaném vývojovém prostředí (IDE) sady Visual Studio (integrované vývojové prostředí).

::: moniker-end

::: moniker range=">=vs-2019"

1. V **Průzkumník řešení** rozbalte složku **stránky** a pak zvolte **index. cshtml**.

   ![Vyberte soubor index. cshtml z Průzkumník řešení](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Tento soubor odpovídá stránce s názvem **Domů** ve webové aplikaci, která běží ve webovém prohlížeči.

   ![Stránka o službě ve webové aplikaci](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   V editoru uvidíte kód HTML pro text, který se zobrazí na **domovské** stránce.

   ![Kód HTML v souboru index. cshtml pro domovskou stránku v editoru sady Visual Studio](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. Změňte úvodní text tak, aby se načetl **Hello World!**.

   ![V editoru sady Visual Studio změňte výchozí kód HTML, který říká úvodní Hello World místo toho.](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Zvolte **IIS Express** nebo stiskněte **klávesu CTRL** + **F5** a spusťte aplikaci a otevřete ji ve webovém prohlížeči.

   ![Výběr tlačítka IIS Express v aplikaci Visual Studio](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > Pokud se zobrazí chybová zpráva s oznámením, že se **nelze připojit k webovému serveru ' IIS Express '** nebo chybová zpráva, která uvádí certifikát protokolu SSL, ukončete aplikaci Visual Studio. Dále otevřete aplikaci Visual Studio pomocí možnosti **Spustit jako správce** z místní nabídky klikněte pravým tlačítkem myši. Pak aplikaci spusťte znovu.

1. Ve webovém prohlížeči ověřte, zda je na **domovské** stránce zahrnut aktualizovaný text.

   ![Zobrazit aktualizovanou domovskou stránku, která obsahuje změny, které jste provedli](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Zavřete webový prohlížeč.

::: moniker-end

## <a name="next-steps"></a>Další kroky

Další informace najdete v následujícím kurzu:

> [!div class="nextstepaction"]
> [Začínáme s C# a ASP.NET v aplikaci Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Viz také

[Publikování webové aplikace pro Azure App Service pomocí sady Visual Studio](../deployment/quickstart-deploy-to-azure.md)
