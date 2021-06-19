---
title: 'Kurz: Začínáme s C# a ASP.NET Core'
titleSuffix: ''
description: Naučte se, jak vytvořit webovou aplikaci ASP.NET Core v aplikaci Visual Studio pomocí jazyka C#, krok za krokem.
ms.custom: vs-acquisition, get-started
ms.date: 06/12/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 25840b820a92925c3d7434d0c76b0138b533b2dc
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388110"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Kurz: Začínáme s C# a ASP.NET Core v aplikaci Visual Studio

V tomto kurzu pro vývoj v jazyce C# s ASP.NET Core pomocí sady Visual Studio vytvoříte webovou aplikaci v C# ASP.NET Core, provedete změny, prozkoumáte některé funkce rozhraní IDE a pak aplikaci spustíte.

## <a name="prerequisites"></a>Požadavky

1. Instalace sady Visual Studio
   ::: moniker range="vs-2017"
   
   Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.
   
   ::: moniker-end
   
   ::: moniker range="vs-2019"
   
   Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.
   
   ::: moniker-end

   ::: moniker range="vs-2022"

   Pokud jste ještě nenainstalovali Visual Studio 2022 Preview, nainstalujte ho zdarma na stránku [Visual studio 2022 Preview ke stažení](https://visualstudio.microsoft.com/vs/preview/vs2022) .

   ::: moniker-end

1. Aktualizace sady Visual Studio – Pokud už máte nainstalovanou aplikaci Visual Studio, ujistěte se, že používáte nejnovější verzi. Další informace o tom, jak aktualizovat instalaci, najdete na stránce o [aktualizaci sady Visual Studio na nejnovější verzi](../../install/update-visual-studio.md) .

1. Volba motivu (volitelné) – Tento kurz obsahuje snímky obrazovky, které používají tmavý motiv. Můžete [Přizpůsobit stránku IDE a editor sady Visual Studio](../../ide/quickstart-personalize-the-ide.md) , abyste se dozvěděli, jak.

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt ASP.NET Core. Typ projektu se dodává se všemi soubory šablon, které budete potřebovat pro plně funkční web, než dokonce cokoli přidáte!

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek vyberte **soubor** > **Nový** > **projekt**.

3. V dialogovém okně **Nový projekt** v levém podokně rozbalte položku **Visual C#**, rozbalte položku **Web** a pak zvolte možnost **.NET Core**. V prostředním podokně vyberte **ASP.NET Core webová aplikace**. Pak název souboru *MyCoreApp* a zvolte **OK**.

   ![Šablona projektu webové aplikace ASP.NET Core v dialogovém okně Nový projekt v integrovaném vývojovém prostředí sady Visual Studio](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>Přidat úlohu (volitelné)

Pokud nevidíte šablonu projektu **ASP.NET Core webové aplikace** , můžete ji získat přidáním úlohy **vývoje pro ASP.NET a web** . Tuto úlohu můžete přidat jedním ze dvou způsobů, v závislosti na tom, které aktualizace sady Visual Studio 2017 jsou nainstalovány na vašem počítači.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Možnost 1: použití dialogového okna Nový projekt

1. V levém podokně dialogového okna **Nový projekt** vyberte odkaz **otevřít instalační program pro Visual Studio** . (V závislosti na nastaveních zobrazení se možná budete muset posouvat, abyste ho viděli.)

   ![Vyberte odkaz otevřít Instalační program pro Visual Studio z dialogového okna Nový projekt.](../media/open-visual-studio-installer-mycoreapp.png)

1. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje ASP.NET a webu** a pak zvolte možnost **Upravit**.

   ![Úlohy vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../media/tutorial-aspnet-workload.png)

   (Před pokračováním v instalaci nové úlohy může být nutné zavřít Visual Studio.)

#### <a name="option-2-use-the-tools-menu-bar"></a>Možnost 2: použití panelu nabídky nástroje

1. Zruší se dialogové okno **Nový projekt** . Pak na horním panelu nabídek zvolte **nástroje**  >  **získat nástroje a funkce**.

1. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje ASP.NET a webu** a pak zvolte možnost **Upravit**.

   (Před pokračováním v instalaci nové úlohy může být nutné zavřít Visual Studio.)

### <a name="add-a-project-template"></a>Přidání šablony projektu

1. V dialogovém okně **Nová webová aplikace ASP.NET Core** vyberte šablonu projektu **Webová aplikace** .

1. Ověřte, že se v horní rozevírací nabídce zobrazuje **ASP.NET Core 2,1** . Pak klikněte na **tlačítko OK**.

   ![Dialogové okno Nová webová aplikace ASP.NET Core](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Pokud v horní rozevírací nabídce nevidíte **ASP.NET Core 2,1** , ujistěte se, že používáte nejnovější verzi sady Visual Studio. Další informace o tom, jak aktualizovat instalaci, najdete na stránce o [aktualizaci sady Visual Studio na nejnovější verzi](../../install/update-visual-studio.md) .

::: moniker-end

::: moniker range=">=vs-2019"

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   :::image type="content" source="../../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="Zobrazit okno vytvořit nový projekt":::

1. V okně **vytvořit nový projekt** vyberte v seznamu jazyk položku **C#** . V dalším kroku vyberte možnost **Windows** ze seznamu platforem a **Web** ze seznamu typy projektů.

      Po použití filtrů typu jazyk, platforma a typ projektu vyberte šablonu **ASP.NET Core webové aplikace** a klikněte na tlačítko **Další**.

   :::image type="content" source="./media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="Zvolit šablonu C# pro ASP.NET Core webovou aplikaci":::

   > [!NOTE]
   > Pokud nevidíte šablonu **ASP.NET Core webové aplikace** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .
   >
   > ![Odkaz pro instalaci dalších nástrojů a funkcí v okně vytvořit nový projekt v části nenajít, co hledáte?](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Pak v Instalační program pro Visual Studio zvolte úlohu **vývoje ASP.NET a web** .
   >
   > ![Úlohy vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Potom klikněte na tlačítko **Upravit** v instalační program pro Visual Studio. Pokud budete vyzváni k uložení práce, udělejte to. V dalším kroku vyberte **pokračovat** a nainstalujte úlohu. Pak se vraťte ke kroku 2 v tomto postupu "[Vytvoření projektu](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *MyCoreApp* do pole **název projektu** . Pak klikněte na tlačítko **Další**.

   :::image type="content" source="./media/vs-2019/csharp-name-your-aspnet-app.png" alt-text="v okně Konfigurovat nový projekt pojmenujte projekt ' MyCoreApp '.":::

1. V okně **Další informace** ověřte, že se v horní rozevírací nabídce zobrazuje **.NET Core 3,1** . Všimněte si, že se můžete rozhodnout povolit podporu Docker zaškrtnutím políčka. Podporu ověřování můžete také přidat kliknutím na tlačítko změnit ověřování. Odtud si můžete vybrat z těchto:
    - Žádné: žádné ověřování.
    - Jednotlivé účty: tyto jsou uložené v místní databázi nebo databázi založené na Azure.
    - Microsoft Identity Platform: Tato možnost pro ověřování používá službu Active Directory, Azure AD nebo Microsoft 365.
    - Windows: vhodné pro intranetové aplikace.
    
    Nechejte políčko **Povolit Docker** nezaškrtnuté a jako typ ověřování vyberte **žádné** . Potom vyberte **Vytvořit**.

   :::image type="content" source="./media/vs-2019/aspnet-core-additional-information.png" alt-text="v okně Další informace se ujistěte, že je vybraná možnost .NET Core 3,1 a ponechání všech výchozích hodnot.":::

   V aplikaci Visual Studio se otevře nový projekt.

::: moniker-end

### <a name="about-your-solution"></a>O řešení

Toto řešení se řídí vzorem návrhu **stránky Razor** . Je jiný než vzor návrhu [MVC (Model-View-Controller)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x&preserve-view=true) v tom, že je zjednodušený tak, aby zahrnoval model a kód kontroleru v rámci samotné stránky Razor.

::: moniker range="vs-2017"
## <a name="tour-your-solution"></a>Projděte si řešení

 1. Šablona projektu vytvoří řešení s jedním ASP.NET Core projektem s názvem _MyCoreApp_. Kliknutím na kartu **Průzkumník řešení** zobrazíte její obsah.

    ![ASP.NET Průzkumník řešení v aplikaci Visual Studio pro Razor Pages řešení s názvem MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Rozbalte složku **stránky** a poté rozbalte položku *o. cshtml*.

     ![Soubor About. cshtml v Průzkumník řešení v aplikaci Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Prohlédněte si soubor **About. cshtml** v editoru kódu.

     ![Snímek obrazovky zobrazující prvních deset řádků souboru About. cshtml v editoru kódu sady Visual Studio.](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. Vyberte soubor **About. cshtml. cs** .

     ![Výběr souboru About. cshtml. cs v editoru kódu sady Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Prohlédněte si soubor **About. cshtml. cs** v editoru kódu.

     ![Snímek obrazovky zobrazující prvních 18 řádků souboru About. cshtml. cs v editoru kódu sady Visual Studio. ](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Projekt obsahuje složku **wwwroot** , která je kořenem vašeho webu. Rozbalte složku pro zobrazení jejího obsahu.

     ![Složka wwwroot v Průzkumník řešení v aplikaci Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Statický obsah webu, jako &mdash; jsou CSS, obrázky a knihovny JavaScriptu, můžete umístit &mdash; přímo do cest, kde je chcete.

 1. Projekt také obsahuje konfigurační soubory, které spravují webovou aplikaci v době běhu. Výchozí [Konfigurace](/aspnet/core/fundamentals/configuration) aplikace je uložena v *appsettings.js*. Tato nastavení však můžete přepsat pomocí *appsettings.Development.jsna*. Rozbalením **appsettings.jsv** souboru zobrazíte **appsettings.Development.jsv** souboru.

     ![Konfigurační soubory v Průzkumník řešení v aplikaci Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Spuštění, ladění a provedení změn

1. Zvolte tlačítko **IIS Express** v integrovaném vývojovém prostředí a sestavte a spusťte aplikaci v režimu ladění. (Případně stiskněte klávesu **F5** nebo zvolte **Ladit.**  >  **Spusťte ladění** z řádku nabídek.)

     ![Vyberte tlačítko IIS Express v Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Pokud se zobrazí chybová zpráva s oznámením Nelze se připojit k webovému serveru **IIS Express,** zavřete Visual Studio a pak ho otevřete pomocí možnosti Spustit jako správce v místní nabídce nebo kliknutí pravým tlačítkem myši.  Pak aplikaci znovu spusťte.
     >
     > Může se také zobrazit zpráva s dotazem, jestli chcete přijmout certifikát IIS SSL Express. Pokud chcete zobrazit kód ve webovém prohlížeči, zvolte **Ano** a pak zvolte Ano, pokud se zobrazí následná zpráva s upozorněním zabezpečení. 

1. Visual Studio se otevře okno prohlížeče. Na řádku nabídek **by** **se** měly zobrazit stránky **Domů,** O aplikaci a Kontakt. (Pokud ne, zvolte položku hamburgerové nabídky a zobrazte ji.)

    ![V řádku nabídek ve webové aplikaci vyberte položku hamburgerové nabídky.](media/csharp-aspnet-razor-browser-page.png)

1. Na **řádku** nabídek zvolte O systému.

   ![V řádku nabídek okna prohlížeče pro vaši aplikaci vyberte O aplikaci.](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Kromě jiného stránka **O aplikaci** v prohlížeči vykreslí text, který je nastavený v souboru *About.cshtml.*

   ![Zobrazení textu na stránce O službě](media/csharp-aspnet-razor-browser-page-about.png)

1. Vraťte se Visual Studio a stisknutím **kláves Shift+F5** zastavte režim ladění. Tím se také zavře projekt v okně prohlížeče.

1. V Visual Studio soubor **About.cshtml.** Potom odstraňte slovo _additional a_ na jeho místo přidejte soubor slov _a adresář_.

    ![Změna textu v souboru About.cshtml](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. Zvolte **About.cshtml.cs.** Pak pomocí následujícího `using` zástupce vyčistěte direktivy v horní části souboru:

   Zvolte některý z direktiv se zašedlou šedou výsečí a žárovka Rychlé akce se zobrazí přímo pod výsečí `using` nebo na levém okraji. [](../../ide/quick-actions.md) Zvolte žárovku a pak zvolte **Odebrat nepotřebné použití**.

   ![Odebrání nepotřebných usingů v souboru About.cshtml.cs](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Visual Studio odstraní nepotřebné `using` direktivy ze souboru .

1. Dále v `OnGet()` metodě změňte text na následující kód:

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
         Message = String.Format("Your directory is {0}.", directory);
     }
    ```

1. Všimněte si, že pod Environment (Prostředí) a String (Řetězec) se **zobrazují** dvě **podtržení vlnovkou.** Podtržení vlnovkou se zobrazí, protože tyto typy nejsou v oboru.

   ![Chyby označené podtržením vlnovkou v metodě OnGet](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Otevřete panel **Seznam chyb,** na který se zobrazí stejné chyby. (Pokud se tento panel  nástrojů Seznam chyb, zvolte **Zobrazení.**  >  **Seznam chyb** horním řádku nabídek.)

   ![Seznam chyb v Visual Studio](media/csharp-aspnet-razor-error-list.png)

1. Pojďme to napravit. V editoru kódu umístěte kurzor na řádek, který obsahuje chybu, a pak na levém okraji zvolte žárovku Rychlé akce. Potom v rozevírací nabídce zvolte using **System;** (Systém). Tím přidáte tuto direktivu na začátek souboru a vyřešíte chyby.

   ![Přidání direktivy using System;](media/csharp-aspnet-razor-add-usings.png)

1. Stisknutím **kláves Ctrl** S uložte změny a stisknutím +  **klávesy F5** otevřete projekt ve webovém prohlížeči.

1. V horní části webu zvolte O aplikaci **a** zobrazte změny.

   ![Podívejte se na aktualizovanou stránku O službě, která obsahuje změny, které jste provedli.](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Zavřete webový prohlížeč, stisknutím **klávesy Shift** F5 zastavte režim ladění a pak +  zavřete Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="tour-your-solution"></a>Prohlídka vašeho řešení

 1. Šablona projektu vytvoří řešení s jedním projektem ASP.NET Core s názvem _MyCoreApp._ Zvolte kartu **Průzkumník řešení** a zobrazte její obsah.

    ![ASP.NET Průzkumník řešení v Visual Studio pro Razor Pages s názvem MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Rozbalte **složku** Pages.

     ![Složka Pages v Průzkumník řešení](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Prohlédněte **si soubor Index.cshtml** v editoru kódu.

     ![Zobrazení souboru Index.cshtml v editoru Visual Studio kódu](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. Každý soubor .cshtml má přidružený soubor kódu. Pokud chcete soubor kódu otevřít v editoru, rozbalte uzel **Index.cshtml** v Průzkumník řešení a zvolte **soubor Index.cshtml.cs.**

     ![Zvolte soubor Index.cshtml.cs v editoru Visual Studio kódu.](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. V editoru kódu zobrazte soubor **Index.cshtml.cs.**

     ![Zobrazení souboru About.cshtml v editoru Visual Studio kódu](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Projekt obsahuje složku **wwwroot,** která je kořenem vašeho webu. Rozbalte složku a zobrazte její obsah.

     ![Složka wwwroot v Průzkumník řešení v Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Statický obsah webu, jako jsou šablony stylů CSS, obrázky a javascriptové knihovny, můžete umístit přímo do &mdash; &mdash; cest, kde je chcete.

 1. Projekt obsahuje také konfigurační soubory, které spravují webovou aplikaci za běhu. Výchozí konfigurace aplikace [je uložená](/aspnet/core/fundamentals/configuration) v *appsettings.jsna .* Tato nastavení však můžete přepsat pomocí příkazuappsettings.Development.js *na .* Rozbalte **appsettings.jssoubor** a zobrazte souborappsettings.Development.js **on.**

     ![Konfigurační soubory v Průzkumník řešení Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Spuštění, ladění a provedení změn

1. Zvolte tlačítko **IIS Express** v integrovaném vývojovém prostředí a sestavte a spusťte aplikaci v režimu ladění. (Případně stiskněte klávesu **F5** nebo zvolte **Ladit.**  >  **Spusťte ladění** z řádku nabídek.)

     ![Vyberte tlačítko IIS Express v Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Pokud se zobrazí chybová zpráva s oznámením Nelze se připojit k webovému serveru **IIS Express,** zavřete Visual Studio a pak ho otevřete pomocí možnosti Spustit jako správce v místní nabídce nebo kliknutí pravým tlačítkem myši.  Pak aplikaci znovu spusťte.
     >
     > Může se také zobrazit zpráva s dotazem, jestli chcete přijmout certifikát IIS SSL Express. Pokud chcete zobrazit kód ve webovém prohlížeči, zvolte **Ano** a pak zvolte Ano, pokud se zobrazí následná zpráva s upozorněním zabezpečení. 

1. Visual Studio se otevře okno prohlížeče. Na řádku nabídek **by se** měly zobrazit **stránky Domů** a Ochrana osobních údajů.

1. Na **řádku nabídek** zvolte Ochrana osobních údajů.

   Stránka **Ochrana** osobních údajů v prohlížeči vykreslí text nastavený v souboru *Privacy.cshtml.*

   ![Zobrazení textu na stránce Ochrana osobních údajů](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Vraťte se Visual Studio a stisknutím **kláves Shift+F5** zastavte režim ladění. Tím se také zavře projekt v okně prohlížeče.

1. V Visual Studio otevřete soubor **Privacy.cshtml pro** úpravy. Potom odstraňte  slova Tato stránka slouží k podrobnostem o zásadách ochrany osobních údajů vašeho webu a na jeho místě přidejte slova This _page is under construction as @ViewData ["TimeStamp"]_.

    ![Změna textu v souboru Privacy.cshtml](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. Teď pojďme provést změnu kódu. Zvolte **Privacy.cshtml.cs.** Pak pomocí následujícího `using` zástupce vyčistěte direktivy v horní části souboru:

   Zvolte některý z direktiv se zašedlou šedou výsečí a žárovka Rychlé akce se zobrazí přímo pod výsečí `using` nebo na levém okraji. [](../../ide/quick-actions.md) Zvolte žárovku a pak najeďte myší na **Odebrat nepotřebné funkce using.**

   ![Odebrání nepotřebných použití v souboru Privacy.cshtml.cs](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   Teď zvolte **Náhled změn a** podívejte se, co se změní.

   ![Náhled změn](media/vs-2019/csharp-aspnet-preview-changes.png)

   Zvolte **Použít**. Visual Studio odstraní nepotřebné `using` direktivy ze souboru .

1. Dále v `OnGet()` metodě změňte text na následující kód:

     ```csharp
     public void OnGet()
     {
        string dateTime = DateTime.Now.ToShortDateString();
        ViewData["TimeStamp"] = dateTime;
     }
    ```

1. Všimněte si, že v části DateTime se zobrazují **dva podtržení vlnovkou.** Podtržení vlnovkou se zobrazí, protože tento typ není v oboru.

   ![Chyby označené podtržením vlnovkou v metodě OnGet](media/vs-2019/csharp-aspnet-add-new-onget-method.png)

    Otevřete panel **Seznam chyb,** na který se zobrazí stejné chyby. (Pokud se tento panel  nástrojů Seznam chyb, zvolte **Zobrazení.**  >  **Seznam chyb** horním řádku nabídek.)

   ![Seznam chyb v Visual Studio](media/vs-2019/csharp-aspnet-error-list.png)

1. Pojďme to napravit. V editoru kódu umístěte kurzor na řádek, který obsahuje chybu, a pak na levém okraji zvolte žárovku Rychlé akce. Potom v rozevírací nabídce zvolte using **System;** (Systém). Tím přidáte tuto direktivu na začátek souboru a vyřešíte chyby.

   ![Přidání direktivy using System;](media/vs-2019/csharp-aspnet-add-usings.png)

1. Stisknutím **klávesy F5** otevřete projekt ve webovém prohlížeči.

1. V horní části webu zvolte Ochrana **osobních údajů a** zobrazte změny.

   ![Podívejte se na aktualizovanou stránku Ochrany osobních údajů, která obsahuje provedené změny.](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. Zavřete webový prohlížeč, stisknutím **klávesy Shift** F5 zastavte režim ladění a pak +  zavřete Visual Studio.
::: moniker-end

## <a name="quick-answers-faq"></a>Rychlé odpovědi – nejčastější dotazy

Tady je stručný přehled nejčastějších dotazů, ve které najdete některé klíčové koncepty.

### <a name="what-is-c"></a>Co je jazyk C#?

[C#](https://docs.microsoft.com/dotnet/csharp/tour-of-csharp/) je typově bezpečný a objektově orientovaný programovací jazyk, který je navržený tak, aby byl robustní a snadno se učí.

### <a name="what-is-aspnet-core"></a>Co je ASP.NET Core?

ASP.NET Core je open source a více platforem pro vytváření aplikací připojených k internetu, jako jsou webové aplikace a služby. ASP.NET Core můžete spouštět na .NET Core nebo na .NET Framework. Můžete vyvíjet a spouštět aplikace ASP.NET Core pro více platforem ve Windows, Macu a Linuxu. ASP.NET Core je open source na [GitHubu.](https://github.com/aspnet/home)

### <a name="what-is-visual-studio"></a>Co je Visual Studio?

Visual Studio je integrovaná sada nástrojů pro produktivitu vývojářů. Představte si ho jako program, který můžete použít k vytváření programů a aplikací.

## <a name="next-steps"></a>Další kroky

Blahopřejeme k dokončení tohoto kurzu! Doufáme, že jste se trochu dozvěděli o C#, ASP.NET Core a integrovaném vývojovém Visual Studio. Další informace o vytvoření webové aplikace nebo webu pomocí jazyka C# a ASP.NET najdete v následujících kurzech:

> [!div class="nextstepaction"]
> [Vytvoření webové Razor Pages pomocí ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)

## <a name="see-also"></a>Viz také

[Publikování webové aplikace do Azure App Service pomocí Visual Studio](../../deployment/quickstart-deploy-to-azure.md)
