---
title: Prohlídka integrovaného vývojového prostředí sady Visual Studio
titleSuffix: ''
ms.date: 02/21/2019
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 490d3edddd35ad5d72733824e3af41888839e946
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596967"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Rychlý start: Nejdřív se podívejte na integrovaném vývojovém prostředí sady Visual Studio

V tomto úvodu 5 až 10 minut do integrovaného vývojového prostředí (IDE) sady Visual Studio provedeme si některé z okna, nabídek a další funkce uživatelského rozhraní.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránku a nainstalovat zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) stránku a nainstalovat zdarma.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Domovská stránka

První věc, kterou uvidíte po otevření sady Visual Studio, je největší pravděpodobně **úvodní stránkou**. **Úvodní stránka** slouží jako "centra", které vám pomohou najít příkazy a potřebujete rychlejší soubory projektu. **Poslední** části zobrazí projekty a složky, které jste nedávno pracovali. V části **nový projekt**, můžete kliknout na odkaz zobrazíte **nový projekt** dialogové okno, nebo v části **otevřete**, můžete otevřít existující projekt kódu nebo složky. Na pravé straně je informační kanál nejnovější Novinky pro vývojáře.

![Úvodní stránka v sadě Visual Studio](media/start-page.png)

Pokud zavřete **úvodní stránka** a chcete ho znovu zobrazit, můžete znovu otevřít z **souboru** nabídky.

![Nabídka soubor v sadě Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Počáteční okno

První věc, kterou uvidíte po otevření sady Visual Studio, je okno Start. Okno Start je navrženo tak, aby vám pomohla rychleji "získat kód". Obsahuje možnosti klonování nebo rezervace kódu, otevření existujícího projektu nebo řešení, vytvoření nového projektu nebo snadné otevření složky, která obsahuje některé soubory kódu.

[![okno Start v aplikaci Visual Studio 2019](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Pokud používáte Visual Studio poprvé, váš seznam posledních projektů bude prázdný.

Pokud pracujete s kódy základů kódu, které nejsou založené na MSBuild, použijete možnost **otevřít místní složku** pro otevření kódu v aplikaci Visual Studio. Další informace najdete v tématu [vývoj kódu v sadě Visual Studio bez projektů nebo řešení](develop-code-in-visual-studio-without-projects-or-solutions.md). V opačném případě můžete vytvořit nový projekt nebo naklonovat projekt ze zdrojového poskytovatele, jako je GitHub nebo Azure DevOps.

Možnost **pokračovat bez kódu** jednoduše otevře vývojové prostředí sady Visual Studio bez jakéhokoli konkrétního projektu nebo načteného kódu. Tuto možnost můžete zvolit, chcete-li připojit relaci [Live Share](/visualstudio/liveshare/) nebo připojit k procesu pro ladění. Můžete také stisknutím klávesy **ESC** zavřít okno Start a otevřít integrované vývojové prostředí (IDE).

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Pokračujte ve zkoumání funkcí sady Visual Studio, vytvoříme nový projekt.

::: moniker range="vs-2017"

1. Na **úvodní stránka**, do vyhledávacího pole v rámci **nový projekt**, zadejte v **konzoly** pro filtrování seznamu typů projektů na ty, které obsahují "console" v názvu.

   ![Hledat v šablonách projektů na úvodní stránce Visual Studio](media/start-page-search-templates.png)

   Visual Studio poskytuje různé druhy šablony projektů, které vám pomůžou začít pracovat rychle kódování. C# Vyberte šablonu projektu **aplikace konzoly (.NET Core)** . (Případně pokud jste v jazyce Visual Basic, C++, Javascript nebo jiné jazyk pro vývojáře, můžete vytvořit projekt v jednom z těchto jazyků. Uživatelské rozhraní, které jsme vám pomyslného je podobné pro všechny programovací jazyky.)

1. V **nový projekt** dialogové okno, které se zobrazí, přijměte výchozí název projektu a zvolte možnost **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   Otevře se dialogové okno s informacemi **o vytvoření nového projektu**. Tady můžete vyhledat, filtrovat a vybrat šablonu projektu. Zobrazuje také seznam naposledy použitých šablon projektu.

1. Do pole Hledat v horní části zadejte text **Konzola** , chcete-li filtrovat seznam typů projektu na ty, které v názvu obsahují "Console". Další upřesnění výsledků hledání výběrem **C#** (nebo jiného jazyka podle vašeho výběru) z výběru **jazyka** .

   ![Dialogové okno Nový projekt v aplikaci Visual Studio 2019](media/vs-2019/create-a-new-project.png)

1. Pokud jste vybrali C#, Visual Basic nebo F# jako svůj jazyk, vyberte šablonu **Konzolová aplikace (.NET Core)** a pak klikněte na tlačítko **Další**. (Pokud jste vybrali jiný jazyk, stačí vybrat šablonu. Uživatelské rozhraní, které jsme vám pomyslného je podobné pro všechny programovací jazyky.)

1. Na stránce **Konfigurovat nový projekt** přijměte výchozí název projektu a umístění a pak zvolte **vytvořit**.

::: moniker-end

   Vytvoření projektu a soubor s názvem *Program.cs* se otevře v **Editor** okna. **Editor** zobrazuje obsah souborů a je tam, kde provedete většinu práce s kódováním v aplikaci Visual Studio.

   ![Editor v sadě Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Průzkumník řešení

**Průzkumník řešení**, což je obvykle na pravé straně sady Visual Studio, se dozvíte, grafické reprezentace hierarchie souborů a složek ve vašem projektu, řešení nebo složky s kódem. Můžete procházet hierarchii a přejděte k souboru v **Průzkumníka řešení**.

![Průzkumník řešení v sadě Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Nabídky

Příkazy nabídek v horní části Visual Studio seskupí do kategorií. Například **projektu** nabídka obsahuje příkazy související s projektem, ve které pracujete. Na **nástroje** nabídky, si můžete přizpůsobit chování sady Visual Studio tak, že vyberete **možnosti**, nebo přidání funkcí k instalaci tak, že vyberete **stažení nástrojů a funkcí**.

::: moniker range="vs-2017"

![Řádek nabídek v aplikaci Visual Studio 2017](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Řádek nabídek v aplikaci Visual Studio 2019](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Seznam chyb

Otevřete okno **Seznam chyb** výběrem nabídky **zobrazit** a pak **Seznam chyb**.

**Seznam chyb** se dozvíte, chyby, varování a zprávy týkající se aktuální stav vašeho kódu. Pokud nejsou žádné chyby (například chybějící závorka nebo středník) v souboru nebo kdekoli ve vašem projektu, jsou zde uvedeny.

![Seznam chyb v sadě Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Výstup – okno

**Výstup** okno zobrazuje výstup zprávy z sestavení vašeho projektu a váš poskytovatel správy zdrojových kódů.

Vytvořme projektu zobrazíte některé výstup sestavení. Z **sestavení** nabídce zvolte **sestavit řešení**. **Výstup** okno automaticky získá fokus a zobrazí zprávy úspěšné sestavení.

![Okno výstup v sadě Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Vyhledávací pole

Vyhledávací pole představuje rychlý a snadný způsob, jak v aplikaci Visual Studio přejít na hodně mnohem cokoli. Můžete zadat nějaký text související s co chcete udělat, a ho budete zobrazit seznam možností, které se vztahují na text. Představte si například, že chcete zvýšit úroveň podrobností výstupu sestavení zobrazíte další podrobnosti o tom, co přesně sestavení dělá. Zde je, jak vám může provést:

::: moniker range="vs-2017"

1. V pravém horním rohu integrovaného vývojového prostředí (IDE) Najděte vyhledávací pole **Snadné spuštění** . (Případně stiskněte klávesu **Ctrl**+**Q** pro přístup k ní.)

2. Do vyhledávacího pole zadejte **Podrobnosti** . V zobrazené výsledky, zvolte **projekty a řešení--> sestavení a spuštění** pod **možnosti** kategorie.

   ![Rychlé spuštění vyhledávacího pole v aplikaci Visual Studio 2017](media/quickstart-IDE-quick-launch.png)

   **Možnosti** dialogové okno s **sestavíte a spustíte** stránka možností.

::: moniker-end

::: moniker range=">=vs-2019"

1. Stisknutím **kombinace kláves Ctrl**+**Q** aktivujete vyhledávací pole v horní části rozhraní IDE.

2. Do vyhledávacího pole zadejte **Podrobnosti** . V zobrazených výsledcích vyberte možnost **změnit podrobnosti MSBuild**.

   ![Vyhledávací pole v aplikaci Visual Studio 2019](media/vs-2019/quick-launch-verbosity.png)

   **Možnosti** dialogové okno s **sestavíte a spustíte** stránka možností.

::: moniker-end

3. V části **podrobnosti výstupu sestavení projektu nástroje MSBuild**, zvolte **normální**a potom klikněte na tlačítko **OK**.

4. Znovu sestavte projekt kliknutím pravým tlačítkem na **ConsoleApp1** projekt **Průzkumníka řešení** a zvolíte **znovu sestavit** v místní nabídce.

   Tentokrát **výstup** okně se zobrazí podrobnější protokolování z procesu sestavení, včetně souborů, které byly zkopírovány where.

   ![Výstup podrobné sestavení v sadě Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Odeslat zpětnou vazbu nabídky

Pokud máte v aplikaci Visual Studio nějaké problémy, nebo pokud máte návrhy na to, jak produkt vylepšit, můžete použít nabídku **Odeslat názor** v horní části okna sady Visual Studio.

::: moniker range="vs-2017"

![Nabídka Odeslat názor v aplikaci Visual Studio 2017](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Nabídka Odeslat názor v aplikaci Visual Studio 2019](media/vs-2019/send-feedback-menu.png)

::: moniker-end

## <a name="next-steps"></a>Další kroky

Jsme se zabývali jenom některé funkce sady Visual Studio k seznámit s uživatelským rozhraním. Chcete-li podrobněji:

> [!div class="nextstepaction"]
> [Další informace o editoru kódu](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Seznamte se s projekty a řešení](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Viz také:

- [Přehled prostředí IDE sady Visual Studio](../get-started/visual-studio-ide.md)
- [Další funkce sady Visual Studio](../ide/advanced-feature-overview.md)
- [Změna barvy motivu a písma](../ide/quickstart-personalize-the-ide.md)
