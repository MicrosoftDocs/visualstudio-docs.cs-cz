---
title: 'Kurz: Začínáme s C# a ASP.NET Core'
titleSuffix: ''
description: Přečtěte si, jak vytvořit webovou aplikaci ASP.NET Core ve Visual Studiu s C#, krok za krokem.
ms.custom: seodec18, get-started
ms.date: 05/29/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: ef41e28d994f27f66f616623d1b2c9798b65ede4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580059"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Kurz: Začínáme s C# a ASP.NET Core v sadě Visual Studio

V tomto kurzu pro vývoj jazyka C# s ASP.NET Core pomocí Sady Visual Studio vytvoříte c# ASP.NET základní webové aplikace, provést změny v něm, prozkoumat některé funkce ide a pak spustit aplikaci.

## <a name="before-you-begin"></a>Než začnete

### <a name="install-visual-studio"></a>Instalace sady Visual Studio

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

### <a name="update-visual-studio"></a>Aktualizace sady Visual Studio

Pokud jste už nainstalovali Visual Studio, ujistěte se, že používáte nejnovější verzi. Další informace o aktualizaci instalace naleznete na [stránce Aktualizace sady Visual Studio na nejnovější](../../install/update-visual-studio.md) verzi.

### <a name="choose-your-theme-optional"></a>Vyberte si motiv (volitelné)

Tento výukový program obsahuje snímky obrazovky, které používají tmavý motiv. Pokud nepoužíváte tmavý motiv, ale chcete, podívejte se na [stránku Přizpůsobit ide a editor u visual ateliéru,](../../ide/quickstart-personalize-the-ide.md) kde se dozvíte, jak na to.

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt ASP.NET Core. Typ projektu je dodáván se všemi soubory šablon, které budete potřebovat pro plně funkční webové stránky, ještě předtím, než jste něco přidali!

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

3. V dialogovém okně **Nový projekt** v levém podokně rozbalte **položku Visual C#**, rozbalte **položku Web**a pak zvolte **.NET Core**. V prostředním podokně zvolte **ASP.NET Základní webová aplikace**. Poté pojmenujte soubor *MyCoreApp* a zvolte **OK**.

   ![ASP.NET šablona projektu Základní webová aplikace v dialogovém okně Nový projekt v ide sady Visual Studio](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>Přidání pracovního vytížení (volitelné)

Pokud nevidíte šablonu projektu **ASP.NET základní webové aplikace,** můžete ji získat přidáním **ASP.NET a zatížení vývoje webu.** Toto zatížení můžete přidat jedním ze dvou následujících způsobů, v závislosti na tom, které aktualizace Visual Studia 2017 jsou nainstalovány v počítači.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Možnost 1: Použití dialogového okna Nový projekt

1. V levém podokně dialogového okna Nový **projekt** vyberte odkaz Otevřít instalační program **sady Visual Studio.** (V závislosti na nastavení zobrazení může být nutné jej zobrazit posunutím.)

   ![V dialogovém okně Nový projekt vyberte odkaz Otevřít instalační program sady Visual Studio.](../media/open-visual-studio-installer-mycoreapp.png)

1. Spustí se instalační program pro Visual Studio. Zvolte **ASP.NET a zatížení vývoje webu** a pak zvolte **Změnit**.

   ![Úloha vývoje napříč platformami .NET Core v instalačním programu sady Visual Studio](../media/tutorial-aspnet-workload.png)

   (Možná budete muset zavřít Visual Studio před pokračováním v instalaci nové úlohy.)

#### <a name="option-2-use-the-tools-menu-bar"></a>Možnost 2: Použití panelu nabídek Nástroje

1. Zrušit z dialogového okna **Nový projekt** Potom z horního řádku nabídek zvolte **Nástroje** > **získat nástroje a funkce**.

1. Spustí se instalační program pro Visual Studio. Zvolte **ASP.NET a zatížení vývoje webu** a pak zvolte **Změnit**.

   (Možná budete muset zavřít Visual Studio před pokračováním v instalaci nové úlohy.)

### <a name="add-a-project-template"></a>Přidání šablony projektu

1. V dialogovém okně **Nová ASP.NET základní webová aplikace** zvolte šablonu projektu webové **aplikace.**

1. Ověřte, zda se v horní rozevírací nabídce zobrazí **ASP.NET Jádra 2.1.** Potom zvolte **OK**.

   ![Dialogové okno Nová ASP.NET základní webová aplikace](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Pokud nevidíte **ASP.NET Jádrem 2.1** v horní rozevírací nabídce, ujistěte se, že používáte nejnovější verzi sady Visual Studio. Další informace o aktualizaci instalace naleznete na [stránce Aktualizace sady Visual Studio na nejnovější](../../install/update-visual-studio.md) verzi.

::: moniker-end

::: moniker range="vs-2019"

1. V počátečním okně zvolte **Vytvořit nový projekt**.

   ![Zobrazit okno Vytvořit nový projekt](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **Vytvořit nový projekt** zadejte nebo zadejte *ASP.NET* do vyhledávacího pole. Dále zvolte **C#** ze seznamu jazyk a pak zvolte **Windows** ze seznamu platformy.

   Po použití filtrů jazyka a platformy zvolte **šablonu ASP.NET Základní webová aplikace** a pak zvolte **Další**.

   ![Zvolte šablonu Jazyka C# pro základní ASP.NET webovou aplikaci](./media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > Pokud šablonu ASP.NET **základní webové aplikace** nevidíte, můžete ji nainstalovat z okna **Vytvořit nový projekt.** Ve zprávě **Install more tools and features** **Nenajít to, co hledáte?**
   >
   > ![Odkaz "Nainstalovat další nástroje a funkce" ze zprávy "Nenajít to, co hledáte" v okně "Vytvořit nový projekt"](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Potom v Instalační službě sady Visual Studio zvolte **úlohu ASP.NET a vývoj webových** aplikací.
   >
   > ![Úloha vývoje napříč platformami .NET Core v instalačním programu sady Visual Studio](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Poté zvolte tlačítko **Změnit** v Instalační službě sady Visual Studio. Pokud se zobrazí výzva k uložení práce, uděláte to. Dále zvolte **Pokračovat** k instalaci úlohy. Potom se vraťte ke kroku 2 v tomto postupu "[Vytvořit projekt](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *MyCoreApp* do pole **Název projektu.** Potom zvolte **Vytvořit**.

   ![v okně Konfigurace nového projektu pojmenujte projekt MyCoreApp](./media/vs-2019/csharp-name-your-aspnet-mycoreapp-project.png)

1. V okně **Vytvořit novou ASP.NET základní webové aplikace** ověřte, zda se v horní rozevírací nabídce zobrazí ASP.NET **jádra 3.0.** Potom zvolte **Webovou aplikaci**, která obsahuje příklady Razor Pages. Dále zvolte **Vytvořit**.

   ![Okno Vytvořit novou ASP.NET základní webovou aplikaci](./media/vs-2019/csharp-create-aspnet-razor-pages-app.png)

   Visual Studio otevře nový projekt.

::: moniker-end

### <a name="about-your-solution"></a>O vašem řešení

Toto řešení se řídí návrhovým vzorem **Razor Page.** Je to jiné než [model-View-Controller (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x) návrhový vzor v tom, že je zjednodušený zahrnout model a kód řadiče v rámci Razor Page sám.

::: moniker range="vs-2017"
## <a name="tour-your-solution"></a>Prohlídka vašeho řešení

 1. Šablona projektu vytvoří řešení s jedním ASP.NET základní projekt, který se nazývá _MyCoreApp_. Chcete-li zobrazit její obsah, zvolte kartu **Průzkumník řešení.**

    ![ASP.NET Průzkumník řešení v sadě Visual Studio pro Razor Pages řešení s názvem MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Rozbalte složku **Stránky** a potom *rozbalte položku About.cshtml*.

     ![Soubor About.cshtml v Průzkumníku řešení v sadě Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Zobrazení souboru **About.cshtml** v editoru kódu.

     ![Zobrazení souboru About.cshtml v editoru kódu sady Visual Studio](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. Zvolte **soubor About.cshtml.cs.**

     ![Výběr souboru About.cshtml.cs v editoru kódu sady Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Zobrazení **souboru About.cshtml.cs** v editoru kódu.

     ![Zobrazení souboru About.cshtml v editoru kódu sady Visual Studio](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Projekt obsahuje složku **wwwroot,** která je kořenem vašeho webu. Rozbalte složku a zobrazte její obsah.

     ![Složka wwwroot v Průzkumníkovi řešení v sadě Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Statický obsah&mdash;webu, jako jsou css, obrázky&mdash;a knihovny JavaScriptu, můžete umístit přímo do cest, kam je chcete mít.

 1. Projekt také obsahuje konfigurační soubory, které spravují webovou aplikaci za běhu. Výchozí [konfigurace](/aspnet/core/fundamentals/configuration) aplikace je uložena v *souboru appsettings.json*. Tato nastavení však můžete přepsat pomocí *nastavení aplikace. Development.json*. Chcete-li zobrazit nastavení aplikace, rozbalte soubor **appsettings.json.** ** Soubor Development.json.**

     ![Konfigurační soubory v Průzkumníku řešení v sadě Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Spuštění, ladění a provádění změn

1. Zvolte tlačítko **IIS Express** v ide k sestavení a spuštění aplikace v režimu ladění. (Případně stiskněte **klávesu F5**nebo zvolte **Ladění** > **ladění startování** z panelu nabídek.)

     ![Výběr tlačítka IIS Express v sadě Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Pokud se zobrazí chybová zpráva **Nelze se připojit k webovému serveru IIS Express**, zavřete Visual Studio a otevřete ji pomocí **možnosti Spustit jako správce** z nabídky pravým tlačítkem myši nebo místní nabídky. Potom spusťte aplikaci znovu.
     >
     > Může se také zobrazí zpráva s dotazem, zda chcete přijmout certifikát Služby IIS SSL Express. Chcete-li kód zobrazit ve webovém prohlížeči, zvolte **Ano**a pak zvolte **Ano,** pokud se zobrazí upozornění na následné zabezpečení.

1. Visual Studio spustí okno prohlížeče. Na **panelu**nabídek by se pak měly zobrazit stránky Domů , **Informace**a **Kontakt.** (Pokud tak nechcete, zvolte položku nabídky hamburger, abyste je zobrazili.)

    ![Vyberte položku nabídky Hamburger z panelu nabídek ve webové aplikaci.](media/csharp-aspnet-razor-browser-page.png)

1. Z řádku nabídek zvolte **O.**

   ![V řádku nabídek okna prohlížeče pro vaši aplikaci vyberte Možnost O aplikaci.](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Stránka **Informace** v prohlížeči mimo jiné vykreslí text nastavený v souboru *About.cshtml.*

   ![Zobrazení textu na stránce Informace](media/csharp-aspnet-razor-browser-page-about.png)

1. Vraťte se do sady Visual Studio a stisknutím **shift+F5** ukončit režim ladění. Tím se také zavře projekt v okně prohlížeče.

1. V sadě Visual Studio zvolte **About.cshtml**. Potom odstraňte slovo _další_ a na jeho místě přidejte soubor slov _a adresář_.

    ![Změna textu v souboru About.cshtml](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. Zvolte **About.cshtml.cs**. Potom vyčistěte `using` direktivy v horní části souboru pomocí následující zástupce:

   Vyberte si některou `using` ze šedě zobrazených směrnic a žárovka [Rychlé akce](../../ide/quick-actions.md) se zobrazí těsně pod stříškou nebo na levém okraji. Zvolte žárovku a pak zvolte **Odstranit nepotřebné způsoby použití**.

   ![Odebrání nepotřebných použití v souboru About.cshtml.cs](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Visual Studio odstraní `using` zbytečné direktivy ze souboru.

1. Dále v `OnGet()` metodě změňte tělo na následující kód:

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
         Message = String.Format("Your directory is {0}.", directory);
     }
    ```

1. Všimněte si, že dvě podtržení vlnovkou se zobrazí v části **Prostředí** a **řetězec**. Podtržení vlnovkou se zobrazí, protože tyto typy nejsou v oboru.

   ![Chyby označené podtržením vlnovkou v metodě OnGet](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Otevřete panel nástrojů **Seznam chyb,** abyste viděli stejné chyby, které jsou zde uvedeny. (Pokud panel nástrojů **Seznam chyb** nevidíte, zvolte **Zobrazit** > **seznam chyb** z horního řádku nabídek.)

   ![Seznam chyb v sadě Visual Studio](media/csharp-aspnet-razor-error-list.png)

1. Napravíme to. V editoru kódu umístěte kurzor na oba řádky, které obsahují chybu, a pak zvolte žárovku Rychlé akce v levém okraji. Potom z rozevírací nabídky zvolte **použít systém;** chcete-li přidat tuto direktivu do horní části souboru a vyřešit chyby.

   ![Přidat direktivu "using System;"](media/csharp-aspnet-razor-add-usings.png)

1. Stisknutím **klávesy Ctrl**+**S** uložte změny a stisknutím **klávesy F5** otevřete projekt ve webovém prohlížeči.

1. V horní části webu zvolte **O** zobrazení změn.

   ![Zobrazení aktualizované stránky Informace obsahující provedené změny](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Zavřete webový prohlížeč, stisknutím **shift**+**F5** ukončit režim ladění a zavřete Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="tour-your-solution"></a>Prohlídka vašeho řešení

 1. Šablona projektu vytvoří řešení s jedním ASP.NET základní projekt, který se nazývá _MyCoreApp_. Chcete-li zobrazit její obsah, zvolte kartu **Průzkumník řešení.**

    ![ASP.NET Průzkumník řešení v sadě Visual Studio pro Razor Pages řešení s názvem MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Rozbalte složku **Stránky.**

     ![Složka Stránky v Průzkumníku řešení](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Zobrazení souboru **Index.cshtml** v editoru kódu.

     ![Zobrazení souboru Index.cshtml v editoru kódu sady Visual Studio](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. Každý soubor .cshtml má přidružený soubor kódu. Chcete-li otevřít soubor kódu v editoru, rozbalte uzel **Index.cshtml** v Průzkumníku řešení a zvolte **soubor Index.cshtml.cs.**

     ![Výběr souboru Index.cshtml.cs v editoru kódu sady Visual Studio](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. Zobrazení **souboru Index.cshtml.cs** v editoru kódu.

     ![Zobrazení souboru About.cshtml v editoru kódu sady Visual Studio](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Projekt obsahuje složku **wwwroot,** která je kořenem vašeho webu. Rozbalte složku a zobrazte její obsah.

     ![Složka wwwroot v Průzkumníkovi řešení v sadě Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Statický obsah&mdash;webu, jako jsou css, obrázky&mdash;a knihovny JavaScriptu, můžete umístit přímo do cest, kam je chcete mít.

 1. Projekt také obsahuje konfigurační soubory, které spravují webovou aplikaci za běhu. Výchozí [konfigurace](/aspnet/core/fundamentals/configuration) aplikace je uložena v *souboru appsettings.json*. Tato nastavení však můžete přepsat pomocí *nastavení aplikace. Development.json*. Chcete-li zobrazit nastavení aplikace, rozbalte soubor **appsettings.json.** ** Soubor Development.json.**

     ![Konfigurační soubory v Průzkumníku řešení v sadě Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Spuštění, ladění a provádění změn

1. Zvolte tlačítko **IIS Express** v ide k sestavení a spuštění aplikace v režimu ladění. (Případně stiskněte **klávesu F5**nebo zvolte **Ladění** > **ladění startování** z panelu nabídek.)

     ![Výběr tlačítka IIS Express v sadě Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Pokud se zobrazí chybová zpráva **Nelze se připojit k webovému serveru IIS Express**, zavřete Visual Studio a otevřete ji pomocí **možnosti Spustit jako správce** z nabídky pravým tlačítkem myši nebo místní nabídky. Potom spusťte aplikaci znovu.
     >
     > Může se také zobrazí zpráva s dotazem, zda chcete přijmout certifikát Služby IIS SSL Express. Chcete-li kód zobrazit ve webovém prohlížeči, zvolte **Ano**a pak zvolte **Ano,** pokud se zobrazí upozornění na následné zabezpečení.

1. Visual Studio spustí okno prohlížeče. Na panelu nabídek by se pak měly zobrazit stránky **Domů**a **Ochrana osobních údajů.**

1. Z řádku nabídek zvolte **Soukromí.**

   Stránka **Ochrana osobních údajů** v prohlížeči vykreslí text nastavený v souboru *Privacy.cshtml.*

   ![Zobrazení textu na stránce Ochrana osobních údajů](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Vraťte se do sady Visual Studio a stisknutím **shift+F5** ukončit režim ladění. Tím se také zavře projekt v okně prohlížeče.

1. V sadě Visual Studio otevřete **adresu Privacy.cshtml** pro úpravy. Poté odstraňte slova _Pomocí této stránky můžete podrobně popsat zásady ochrany osobních údajů vašeho webu_ a na jeho místě přidejte slova Tato stránka je ve _výstavbě od @ViewData["TimeStamp"]_.

    ![Změna textu v souboru Privacy.cshtml](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. Teď uděláme změnu kódu. Zvolte **Privacy.cshtml.cs**. Potom vyčistěte `using` direktivy v horní části souboru pomocí následující zástupce:

   Vyberte si některou `using` ze šedě zobrazených směrnic a žárovka [Rychlé akce](../../ide/quick-actions.md) se zobrazí těsně pod stříškou nebo na levém okraji. Zvolte žárovku a pak najeďte na **Odebrat zbytečné používání**.

   ![Odebrání nepotřebných použití v souboru Privacy.cshtml.cs](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   Teď zvolte **Náhled změn,** aby se zjistilo, co se změní.

   ![Náhled změn](media/vs-2019/csharp-aspnet-preview-changes.png)

   Zvolte **Použít**. Visual Studio odstraní `using` zbytečné direktivy ze souboru.

1. Dále v `OnGet()` metodě změňte tělo na následující kód:

     ```csharp
     public void OnGet()
     {
        string dateTime = DateTime.Now.ToShortDateString();
        ViewData["TimeStamp"] = dateTime;
     }
    ```

1. Všimněte si, že dvě podtržení vlnovkou se zobrazí v části **DateTime**. Podtržení vlnovkou se zobrazí, protože tyto typy nejsou v oboru.

   ![Chyby označené podtržením vlnovkou v metodě OnGet](media/vs-2019/csharp-aspnet-add-new-onget-method.png)

    Otevřete panel nástrojů **Seznam chyb,** abyste viděli stejné chyby, které jsou zde uvedeny. (Pokud panel nástrojů **Seznam chyb** nevidíte, zvolte **Zobrazit** > **seznam chyb** z horního řádku nabídek.)

   ![Seznam chyb v sadě Visual Studio](media/vs-2019/csharp-aspnet-error-list.png)

1. Napravíme to. V editoru kódu umístěte kurzor na oba řádky, které obsahují chybu, a pak zvolte žárovku Rychlé akce v levém okraji. Potom z rozevírací nabídky zvolte **použít systém;** chcete-li přidat tuto direktivu do horní části souboru a vyřešit chyby.

   ![Přidat direktivu "using System;"](media/vs-2019/csharp-aspnet-add-usings.png)

1. Stisknutím **klávesy F5** otevřete projekt ve webovém prohlížeči.

1. V horní části webu zvolte **Soukromí,** chcete-li zobrazit změny.

   ![Zobrazení aktualizované stránky ochrany osobních údajů, která obsahuje provedené změny](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. Zavřete webový prohlížeč, stisknutím **shift**+**F5** ukončit režim ladění a zavřete Visual Studio.
::: moniker-end

## <a name="quick-answers-faq"></a>Nejčastější dotazy týkající se rychlých odpovědí

Zde je rychlý FAQ upozornit na některé klíčové pojmy.

### <a name="what-is-c"></a>Co je C#?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) je typově bezpečný a objektově orientovaný programovací jazyk, který je navržen tak, aby byl robustní a snadno se učí.

### <a name="what-is-aspnet-core"></a>Co je ASP.NET Core?

ASP.NET Core je open-source a multiplatformní rámec pro vytváření aplikací připojených k internetu, jako jsou webové aplikace a služby. ASP.NET Základní aplikace lze spustit na rozhraní .NET Core nebo .NET Framework. Aplikace ASP.NET Core můžete vyvíjet a spouštět na příčce na Windows, Macu a Linuxu. ASP.NET Core je open source na [GitHubu](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>Co je Visual Studio?

Visual Studio je integrovaná vývojová sada nástrojů pro zvýšení produktivity pro vývojáře. Přemýšlejte o tom jako o programu, který můžete použít k vytváření programů a aplikací.

## <a name="next-steps"></a>Další kroky

Gratulujeme k dokončení tohoto výukového programu! Doufáme, že jste se dozvěděli něco o C#, ASP.NET Core a IDE sady Visual Studio. Další informace o vytváření webové aplikace nebo webu pomocí c# a ASP.NET, pokračujte v následujících kurzech:

> [!div class="nextstepaction"]
> [Vytvořte webovou aplikaci Razor Pages s ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)

## <a name="see-also"></a>Viz také

[Publikování webové aplikace do služby Azure App Service pomocí Visual Studia](../../deployment/quickstart-deploy-to-azure.md)
