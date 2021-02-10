---
title: 'Rychlý Start: prohlídka integrovaného vývojového prostředí (IDE) sady Visual Studio'
description: Přečtěte si o některých oknech, nabídkách a dalších funkcích uživatelského rozhraní integrovaného vývojového prostředí (IDE) sady Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/21/2019
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e0199319bc0c647f42e87d4003dd2fabe4544a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945497"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Rychlý Start: první pohled na integrované vývojové prostředí (IDE) sady Visual Studio

V tomto 5-10 minutách Úvod do integrovaného vývojového prostředí (IDE) sady Visual Studio se podíváme na některé z oken, nabídek a dalších funkcí uživatelského rozhraní.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Úvodní stránka

První věc, kterou uvidíte po otevření sady Visual Studio, je největší pravděpodobně **úvodní stránkou**. **Úvodní stránka** je navržena jako "centrum", která vám pomůžou najít příkazy a soubory projektu, které potřebujete rychleji. V části **Poslední** se zobrazují projekty a složky, které jste nedávno pracovali. V části **Nový projekt** můžete kliknout na odkaz pro otevření dialogového okna **Nový projekt** nebo v části **otevřít** můžete otevřít existující projekt kódu nebo složku. Napravo je informační kanál nejnovějších příspěvků pro vývojáře.

![Úvodní stránka v aplikaci Visual Studio](media/start-page.png)

Pokud zavřete **úvodní stránku** a chcete ji znovu zobrazit, můžete ji znovu otevřít z nabídky **soubor** .

![Nabídka soubor v aplikaci Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a> Úvodní okno

První věc, kterou uvidíte po otevření sady Visual Studio, je okno Start. Okno Start je navrženo tak, aby vám pomohla rychleji "získat kód". Obsahuje možnosti klonování nebo rezervace kódu, otevření existujícího projektu nebo řešení, vytvoření nového projektu nebo snadné otevření složky, která obsahuje některé soubory kódu.

[![Okno Start v aplikaci Visual Studio 2019](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Pokud používáte Visual Studio poprvé, váš seznam posledních projektů bude prázdný.

Pokud pracujete s kódy základů kódu, které nejsou založené na MSBuild, použijete možnost **otevřít místní složku** pro otevření kódu v aplikaci Visual Studio. Další informace naleznete v tématu [vývoj kódu v aplikaci Visual Studio bez projektů nebo řešení](develop-code-in-visual-studio-without-projects-or-solutions.md). V opačném případě můžete vytvořit nový projekt nebo naklonovat projekt ze zdrojového poskytovatele, jako je GitHub nebo Azure DevOps.

Možnost **pokračovat bez kódu** jednoduše otevře vývojové prostředí sady Visual Studio bez jakéhokoli konkrétního projektu nebo načteného kódu. Tuto možnost můžete zvolit, chcete-li připojit relaci [Live Share](/visualstudio/liveshare/) nebo připojit k procesu pro ladění. Můžete také stisknutím klávesy **ESC** zavřít okno Start a otevřít integrované vývojové prostředí (IDE).

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Abychom mohli pokračovat v prozkoumávání funkcí sady Visual Studio, vytvoříme nový projekt.

::: moniker range="vs-2017"

1. Na **úvodní stránce** zadejte do pole Hledat v části **Nový projekt** možnost **Konzola** , aby se seznam typů projektů vyfiltroval na ty, které v názvu obsahují "Console".

   ![Hledat v šablonách projektů na úvodní stránce Visual studia](media/start-page-search-templates.png)

   Visual Studio poskytuje různé druhy šablon projektů, které vám pomohou rychle začít kódovat. Vyberte šablonu projektu **aplikace konzoly C# (.NET Core)** . (Případně, pokud jste Visual Basic, C++, JavaScript nebo jiný vývojář jazyka, nebojte se vytvořit projekt v jednom z těchto jazyků. Uživatelské rozhraní, které budeme hledat, je podobné jako u všech programovacích jazyků.)

1. V dialogovém okně **Nový projekt** , které se zobrazí, přijměte výchozí název projektu a klikněte na **tlačítko OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   Otevře se dialogové okno s informacemi **o vytvoření nového projektu**. Tady můžete vyhledat, filtrovat a vybrat šablonu projektu. Zobrazuje také seznam naposledy použitých šablon projektu.

1. Do pole Hledat v horní části zadejte text **Konzola** , chcete-li filtrovat seznam typů projektu na ty, které v názvu obsahují "Console". Další upřesnění výsledků hledání výběrem **C#** (nebo jiného jazyka podle vašeho výběru) ve výběru **jazyka** .

   ![Dialogové okno Nový projekt v aplikaci Visual Studio 2019](media/vs-2019/create-a-new-project.png)

1. Pokud jste jako jazyk vybrali C#, Visual Basic nebo F #, vyberte šablonu **Konzolová aplikace (.NET Core)** a pak zvolte **Další**. (Pokud jste vybrali jiný jazyk, stačí vybrat šablonu. Uživatelské rozhraní, které budeme hledat, je podobné jako u všech programovacích jazyků.)

1. Na stránce **Konfigurovat nový projekt** přijměte výchozí název projektu a umístění a pak zvolte **vytvořit**.

::: moniker-end

   Projekt je vytvořen a v okně **editoru** se otevře soubor s názvem *program.cs* . **Editor** zobrazuje obsah souborů a je tam, kde provedete většinu práce s kódováním v aplikaci Visual Studio.

   ![Editor v aplikaci Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Průzkumník řešení

**Průzkumník řešení**, který je obvykle na pravé straně aplikace Visual Studio, zobrazuje grafické znázornění hierarchie souborů a složek ve složce projektu, řešení nebo kódu. Můžete procházet hierarchii a přejít k souboru v **Průzkumník řešení**.

![Průzkumník řešení v aplikaci Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Nabídky

Panel nabídek podél horního okraje příkazů skupiny sady Visual Studio do kategorií. Například nabídka **projekt** obsahuje příkazy týkající se projektu, ve kterém pracujete. V nabídce **nástroje** můžete přizpůsobit, jak se aplikace Visual Studio chová, výběrem **možností** nebo přidáním funkcí do instalace výběrem možnosti **získat nástroje a funkce**.

::: moniker range="vs-2017"

![Řádek nabídek v aplikaci Visual Studio 2017](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Řádek nabídek v aplikaci Visual Studio 2019](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Seznam chyb

Otevřete okno **Seznam chyb** výběrem nabídky **zobrazit** a pak **Seznam chyb**.

**Seznam chyb** zobrazí chyby, varování a zprávy týkající se aktuálního stavu kódu. Pokud jsou v souboru nějaké chyby (například chybějící složená závorka nebo středník) nebo kdekoli v projektu, jsou zde uvedeny.

![Seznam chyb v aplikaci Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Výstup – okno

V okně **výstup** se zobrazí výstupní zprávy ze sestavení projektu a ze svého poskytovatele správy zdrojů.

Pojďme sestavit projekt, aby se zobrazil výstup sestavení. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**. Okno **výstup** automaticky získá fokus a zobrazí zprávu o úspěšném sestavení.

![Okno výstup v aplikaci Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Vyhledávací pole

Vyhledávací pole představuje rychlý a snadný způsob, jak v aplikaci Visual Studio přejít na hodně mnohem cokoli. Můžete zadat nějaký text týkající se toho, co chcete udělat, a zobrazí se seznam možností, které se týkají tohoto textu. Představte si například, že chcete zvýšit úroveň podrobností výstupu sestavení a zobrazit další podrobnosti o tom, co právě sestavuje. Můžete to udělat takto:

::: moniker range="vs-2017"

1. V pravém horním rohu integrovaného vývojového prostředí (IDE) Najděte vyhledávací pole **Snadné spuštění** . (Případně stiskněte klávesu **CTRL** + **Dotaz** pro přístup k němu.)

2. Do vyhledávacího pole zadejte **Podrobnosti** . V zobrazených výsledcích vyberte **projekty a řešení – > sestavovat a spouštět** v kategorii **Možnosti** .

   ![Rychlé spuštění vyhledávacího pole v aplikaci Visual Studio 2017](media/quickstart-IDE-quick-launch.png)

   Dialogové okno **Možnosti** se otevře na stránce možnosti **sestavení a spuštění** .

::: moniker-end

::: moniker range=">=vs-2019"

1. Stisknutím klávesy **CTRL** + **Q** aktivujte vyhledávací pole v horní části integrovaného vývojového prostředí (IDE).

2. Do vyhledávacího pole zadejte **Podrobnosti** . V zobrazených výsledcích vyberte možnost **změnit podrobnosti MSBuild**.

   ![Vyhledávací pole v aplikaci Visual Studio 2019](media/vs-2019/quick-launch-verbosity.png)

   Dialogové okno **Možnosti** se otevře na stránce možnosti **sestavení a spuštění** .

::: moniker-end

3. V části **Podrobnosti výstupu sestavení projektu nástroje MSBuild** zvolte možnost **normální** a pak klikněte na tlačítko **OK**.

4. Sestavte projekt znovu tak, že kliknete pravým tlačítkem na projekt **ConsoleApp1** v **Průzkumník řešení** a z kontextové nabídky zvolíte **znovu sestavit** .

   Tentokrát okno **výstup** zobrazuje podrobné protokolování z procesu sestavení, včetně toho, které soubory byly zkopírovány tam, kde.

   ![Podrobný výstup sestavení v aplikaci Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Nabídka Odeslat názor

Pokud máte v aplikaci Visual Studio nějaké problémy, nebo pokud máte návrhy na to, jak produkt vylepšit, můžete použít nabídku **Odeslat názor** v horní části okna sady Visual Studio.

::: moniker range="vs-2017"

![Nabídka Odeslat názor v aplikaci Visual Studio 2017](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Nabídka Odeslat názor v aplikaci Visual Studio 2019](media/vs-2019/send-feedback-menu.png)

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
