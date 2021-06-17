---
title: 'Rychlý start: Prohlídka integrovaného vývojového Visual Studio (IDE)'
description: Přečtěte si o některých oknech, nabídkách a dalších funkcích uživatelského rozhraní integrovaného vývojového Visual Studio (IDE).
ms.custom: acquisition
titleSuffix: ''
ms.date: 03/02/2021
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f10c3fcca5d87f8371d1373314406cf4aa47ec3
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113231"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Rychlý start: První pohled na integrované Visual Studio ide

V tomto 5 až 10minutových úvodu do integrovaného vývojového prostředí (IDE) Visual Studio si prohlédněte některá okna, nabídky a další funkce uživatelského rozhraní.

::: moniker range="vs-2017"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Úvodní stránka

První věc, kterou uvidíte po otevření Visual Studio je pravděpodobně **úvodní stránka**. Úvodní **stránka je** navržená jako "centrum", které vám pomůže rychleji najít příkazy a soubory projektu, které potřebujete. V **části Poslední** se zobrazují projekty a složky, na které jste nedávno pracovali. V **části Nový** projekt můžete kliknutím na  odkaz zobrazit dialogové okno Nový projekt nebo v části Otevřít otevřít existující projekt nebo složku kódu. Napravo je informační kanál nejnovějších zpráv pro vývojáře.

![Úvodní stránka v Visual Studio](media/start-page.png)

Pokud úvodní stránku **zavřete** a chcete ji znovu zobrazit, můžete ji znovu otevřít v **nabídce** Soubor.

![Nabídka Soubor v Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a> Úvodní okno

První věc, kterou uvidíte po otevření Visual Studio, je úvodní okno. Úvodní okno je navržené tak, aby vám pomohlo rychleji se dostat ke kódu. Nabízí možnosti klonování nebo rezervujení kódu, otevření existujícího projektu nebo řešení, vytvoření nového projektu nebo jednoduše otevření složky, která obsahuje nějaké soubory kódu.

[![Úvodní okno v Visual Studio 2019](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Pokud tento seznam používáte poprvé, Visual Studio seznam posledních projektů prázdný.

Pokud pracujete se bázemi kódu, které nejsou založené na MSBuildu, použijete možnost Otevřít místní složku **k** otevření kódu v Visual Studio. Další informace najdete v tématu [Vývoj kódu v Visual Studio bez projektů nebo řešení.](develop-code-in-visual-studio-without-projects-or-solutions.md) Jinak můžete vytvořit nový projekt nebo naklonovat projekt ze zdrojového poskytovatele, jako je GitHub nebo Azure DevOps.

Možnost **Pokračovat bez kódu** jednoduše otevře Visual Studio prostředí bez načtení konkrétního projektu nebo kódu. Tuto možnost můžete zvolit pro připojení Live Share [nebo](/visualstudio/liveshare/) připojení k procesu pro účely ladění. Stisknutím klávesy **Esc můžete také** zavřít úvodní okno a otevřít integrované vývojové prostředí (IDE).

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Pokud chcete Visual Studio funkcích, pojďme vytvořit nový projekt.

::: moniker range="vs-2017"

1. Na úvodní **stránce zadejte** do vyhledávacího pole  v části Nový projekt v konzole příkaz , který vyfiltruje seznam typů projektů podle těch, které v názvu obsahují "console".

   ![Hledání šablon projektů na Visual Studio stránce](media/start-page-search-templates.png)

   Visual Studio nabízí různé druhy šablon projektů, které vám pomůžou rychle začít kódovat. Zvolte šablonu projektu Konzolová aplikace v jazyce C# **(.NET Core).** (Případně pokud jste vývojář jazyka Visual Basic, C++, Javascript nebo jiný jazyk, můžete vytvořit projekt v jednom z těchto jazyků. Uživatelské rozhraní, na které se podíváme, je podobné pro všechny programovací jazyky.)

1. V dialogovém **okně Nový** projekt, které se zobrazí, přijměte výchozí název projektu a zvolte **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. V úvodním okně zvolte **Vytvořit nový projekt.**

    :::image type="content" source="../get-started/media/vs-2019/start-window-create-new-project.png" alt-text="Snímek obrazovky s oknem Vytvořit nový projekt v Visual Studio 2019":::

   Otevře **se okno Vytvořit nový** projekt s několika šablonami *projektů.* Šablona obsahuje základní soubory a nastavení vyžadované pro daný typ projektu.

   Tady můžete vyhledat, filtrovat a vybrat šablonu projektu. Zobrazuje také seznam naposledy použitých šablon projektů.

1. Do vyhledávacího pole v horní části zadejte **konzolu** a vyfiltrujte seznam typů projektů podle těch, které v názvu obsahují "console". Výsledky hledání můžete dále upřesnit výběrem jazyka **C#** (nebo jiného jazyka podle vašeho výběru) **z** rozevíracího seznamu Všechny jazyky.

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="Snímek obrazovky okna Vytvořit nový projekt v Visual Studio 2019, kde vyberete požadovanou šablonu":::

1. Pokud jste jako jazyk vybrali C#, Visual Basic, nebo F#, vyberte šablonu **Konzolová** aplikace a pak zvolte **Další.** (Pokud jste vybrali jiný jazyk, stačí vybrat libovolnou šablonu. Uživatelské rozhraní, na které se podíváme, je podobné pro všechny programovací jazyky.)

1. V okně **Configure your new project** (Konfigurace nového projektu) přijměte výchozí název a umístění projektu a pak zvolte Next **(Další).**

    :::image type="content" source="media/vs-2019/configure-new-project-console.png" alt-text="Snímek obrazovky s oknem Konfigurovat nový projekt v Visual Studio 2019, kde zadáte název projektu":::

1. V okně Další **informace** ověřte, že se v rozevírací  nabídce Cílová rozhraní zobrazuje **.NET Core 3.1,** a pak klikněte na **Vytvořit.**

    :::image type="content" source="../get-started/media/vs-2019/create-project-additional-info.png" alt-text="Snímek obrazovky s oknem Další informace v Visual Studio 2019, kde vyberete požadovanou verzi rozhraní .NET Core Framework":::

::: moniker-end

   Projekt se vytvoří a v okně Editoru  se otevře soubor s názvem *Program.cs.* Editor **zobrazuje** obsah souborů a v tomto místě budete většinu práce s kódováním dělat v Visual Studio.

   ![Editor v Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Průzkumník řešení

**Průzkumník řešení**, která je obvykle na pravé straně Visual Studio, ukazuje grafické znázornění hierarchie souborů a složek ve složce projektu, řešení nebo kódu. Můžete procházet hierarchii a přejít k souboru v **Průzkumník řešení**.

![Průzkumník řešení v Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Nabídky

Řádek nabídek v horní části Visual Studio seskupuje příkazy do kategorií. Například nabídka Projekt **obsahuje** příkazy související s projektem, ve které pracujete. V nabídce **Nástroje** můžete přizpůsobit chování Visual Studio výběrem možnosti Možnosti nebo přidáním funkcí do instalace výběrem možnosti Získat nástroje a **funkce.**

::: moniker range="vs-2017"

![Řádek nabídek v Visual Studio 2017](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Řádek nabídek v Visual Studio 2019](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Seznam chyb

Otevřete okno **Seznam chyb** výběrem nabídky **Zobrazení** a potom **klikněte na Seznam chyb**.

V **Seznam chyb** se zobrazí chyby, upozornění a zprávy týkající se aktuálního stavu kódu. Pokud v souboru nebo kdekoli ve vašem projektu dojde k chybám (například chybějící složená závorka nebo středník), budou uvedené tady.

![Seznam chyb v Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Výstup – okno

V **okně** Výstup se zobrazí výstupní zprávy z sestavení projektu a z poskytovatele správy zdrojového kódu.

Pojďme projekt sestavit a podívat se na výstup sestavení. V **nabídce Sestavení** zvolte Sestavit **řešení.** Okno **Výstup** automaticky získá fokus a zobrazí zprávu o úspěšném sestavení.

![Okno Výstup v Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Vyhledávací pole

Vyhledávací pole je rychlý a snadný způsob, jak přejít na všechno v Visual Studio. Můžete zadat nějaký text související s tím, co chcete udělat, a zobrazí se seznam možností, které se textu týkají. Představte si například, že chcete zvýšit úroveň podrobností výstupu buildu, abyste si prohlédněte další podrobnosti o tom, co přesně sestavení dělá. Můžete to udělat takhle:

::: moniker range="vs-2017"

1. Vyhledejte **Snadné spuštění** v pravém horním rohu integrovaného vývojového prostředí (IDE). (Případně stiskněte **Ctrl.** + **Q** pro přístup k ní.)

2. Do vyhledávacího pole zadejte **verbosity.** Ze zobrazených výsledků zvolte Projekty a **řešení --> Sestavení** a spuštění v **kategorii** Možnosti.

   ![Vyhledávací pole pro snadné spuštění ve Visual Studio 2017](media/quickstart-IDE-quick-launch.png)

   Otevře **se** dialogové okno Možnosti na **stránce Možnosti** sestavení a spuštění.

::: moniker-end

::: moniker range=">=vs-2019"

1. Stisknutím **kláves Ctrl** + **Q** aktivujte vyhledávací pole v horní části integrovaného vývojového prostředí (IDE).

2. Do vyhledávacího pole zadejte **verbosity.** Ze zobrazených výsledků zvolte **Změnit podrobnost nástroje MSBuild.**

   ![Vyhledávací pole v Visual Studio 2019](media/vs-2019/quick-launch-verbosity.png)

   Otevře **se** dialogové okno Možnosti na **stránce Možnosti** sestavení a spuštění.

::: moniker-end

3. V **části Podrobnost výstupu sestavení projektu MSBuild** zvolte **Normální** a pak klikněte na **OK.**

4. Znovu sestavte projekt tak, že kliknete pravým tlačítkem na  projekt **ConsoleApp1** **v Průzkumník řešení** a v místní nabídce zvolíte Znovu sestavit.

   Tentokrát se **v okně Výstup** zobrazí podrobnější protokolování z procesu sestavení, včetně souborů, kam byly zkopírovány.

   ![Podrobný výstup sestavení v Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Nabídka Odeslat názor

Pokud při používání služby Visual Studio narazíte na nějaké problémy nebo pokud máte návrhy, jak  produkt vylepšit, můžete použít nabídku Odeslat názor v horní části okna Visual Studio.

::: moniker range="vs-2017"

![Nabídka Odeslat názor v Visual Studio 2017](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Nabídka Odeslat názor v Visual Studio 2019](media/vs-2019/send-feedback-menu.png)

::: moniker-end

## <a name="next-steps"></a>Další kroky

Prohlédli jsme si jenom několik funkcí sady Visual Studio, abyste se seznámili s uživatelským rozhraním. Další zkoumání:

> [!div class="nextstepaction"]
> [Další informace o editoru kódu](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Další informace o projektech a řešeních](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Viz také

- [Přehled integrovaného vývojového prostředí (IDE) sady Visual Studio](../get-started/visual-studio-ide.md)
- [Další funkce sady Visual Studio](../ide/advanced-feature-overview.md)
- [Změna barev motivu a písma](../ide/quickstart-personalize-the-ide.md)
