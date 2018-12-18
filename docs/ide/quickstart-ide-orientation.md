---
title: Prohlídka integrovaného vývojového prostředí sady Visual Studio
titleSuffix: ''
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7864a85e676e76dda593580d58036c4429fa43c7
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159565"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Rychlý start: První pohled na integrovaném vývojovém prostředí sady Visual Studio

V tomto úvodu 5 až 10 minut do integrovaného vývojového prostředí (IDE) sady Visual Studio provedeme si některé z okna, nabídek a další funkce uživatelského rozhraní.

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stránku a nainstalovat zdarma.

## <a name="start-page"></a>Úvodní stránka

První věc, kterou se zobrazí po spuštění sady Visual Studio je s největší pravděpodobností **úvodní stránka**. **Úvodní stránka** slouží jako "centra", které vám pomohou najít příkazy a potřebujete rychlejší soubory projektu. **Poslední** části zobrazí projekty a složky, které jste nedávno pracovali. V části **nový projekt**, můžete kliknout na odkaz zobrazíte **nový projekt** dialogové okno, nebo v části **otevřete**, můžete otevřít existující projekt kódu nebo složky. Na pravé straně je informační kanál nejnovější Novinky pro vývojáře.

![Úvodní stránka v sadě Visual Studio](media/start-page.png)

Pokud zavřete **úvodní stránka** a chcete ho znovu zobrazit, můžete znovu otevřít z **souboru** nabídky.

![Nabídka soubor v sadě Visual Studio](media/quickstart-IDE-file-menu-large.png)

## <a name="create-a-project"></a>Vytvoření projektu

Pokračujte ve zkoumání funkcí sady Visual Studio, vytvoříme nový projekt.

1. Na **úvodní stránka**, do vyhledávacího pole v rámci **nový projekt**, zadejte v **konzoly** pro filtrování seznamu typů projektů na ty, které obsahují "console" v názvu.

   ![Hledat v šablonách projektů na úvodní stránce Visual Studio](media/start-page-search-templates.png)

   Visual Studio poskytuje různé druhy šablony projektů, které vám pomůžou začít pracovat rychle kódování. Zvolte možnost jazyka C# **Konzolová aplikace (.NET Framework)** šablony projektu. (Případně pokud jste v jazyce Visual Basic, C++, Javascript nebo jiné jazyk pro vývojáře, můžete vytvořit projekt v jednom z těchto jazyků. Uživatelské rozhraní, které jsme vám pomyslného je podobné pro všechny programovací jazyky.)

1. V **nový projekt** dialogové okno, které se zobrazí, přijměte výchozí název projektu a zvolte možnost **OK**.

   Vytvoření projektu a soubor s názvem *Program.cs* se otevře v **Editor** okna. **Editor** zobrazuje obsah souborů a je, ve kterém budete provádět většinu práce psaní kódu v sadě Visual Studio.

   ![Editor v sadě Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Průzkumník řešení

**Průzkumník řešení**, což je obvykle na pravé straně sady Visual Studio, se dozvíte, grafické reprezentace hierarchie souborů a složek ve vašem projektu, řešení nebo složky s kódem. Můžete procházet hierarchii a přejděte k souboru v **Průzkumníka řešení**.

![Průzkumník řešení v sadě Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Nabídky

Příkazy nabídek v horní části Visual Studio seskupí do kategorií. Například **projektu** nabídka obsahuje příkazy související s projektem, ve které pracujete. Na **nástroje** nabídky, si můžete přizpůsobit chování sady Visual Studio tak, že vyberete **možnosti**, nebo přidání funkcí k instalaci tak, že vyberete **stažení nástrojů a funkcí**.

![Panel nabídek v sadě Visual Studio](media/quickstart-IDE-menu-bar.png)

Otevřete **seznam chyb** okno výběrem **zobrazení** nabídky a potom **seznam chyb**.

## <a name="error-list"></a>Seznam chyb

**Seznam chyb** se dozvíte, chyby, varování a zprávy týkající se aktuální stav vašeho kódu. Pokud nejsou žádné chyby (například chybějící závorka nebo středník) v souboru nebo kdekoli ve vašem projektu, jsou zde uvedeny.

![Seznam chyb v sadě Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Výstup – okno

**Výstup** okno zobrazuje výstup zprávy z sestavení vašeho projektu a váš poskytovatel správy zdrojových kódů.

Vytvořme projektu zobrazíte některé výstup sestavení. Z **sestavení** nabídce zvolte **sestavit řešení**. **Výstup** okno automaticky získá fokus a zobrazí zprávy úspěšné sestavení.

![Okno výstup v sadě Visual Studio](media/build-output-minimal.png)

## <a name="quick-launch"></a>Snadné spuštění

**Snadné spuštění** pole je rychlý a snadný způsob, jak to je mnohem nic v sadě Visual Studio. Můžete zadat nějaký text související s co chcete udělat, a ho budete zobrazit seznam možností, které se vztahují na text. Představte si například, že chcete zvýšit úroveň podrobností výstupu sestavení zobrazíte další podrobnosti o tom, co přesně sestavení dělá. Zde je, jak vám může provést:

1. Typ **podrobností** do **Snadné spuštění** pole. V zobrazené výsledky, zvolte **projekty a řešení--> sestavení a spuštění** pod **možnosti** kategorie.

   ![Snadné spuštění pole v sadě Visual Studio](media/quickstart-IDE-quick-launch.png)

   **Možnosti** dialogové okno s **sestavíte a spustíte** stránka možností.

1. V části **podrobnosti výstupu sestavení projektu nástroje MSBuild**, zvolte **normální**a potom klikněte na tlačítko **OK**.

1. Znovu sestavte projekt kliknutím pravým tlačítkem na **ConsoleApp1** projekt **Průzkumníka řešení** a zvolíte **znovu sestavit** v místní nabídce.

   Tentokrát **výstup** okně se zobrazí podrobnější protokolování z procesu sestavení, včetně souborů, které byly zkopírovány where.

   ![Výstup podrobné sestavení v sadě Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Odeslat zpětnou vazbu nabídky

By se vyskytnou potíže při použití sady Visual Studio, nebo pokud máte návrhy na vylepšení produktu, můžete použít **odeslat zpětnou vazbu** nabídce v horní části okna nástroje Visual Studio vedle **rychlé Spuštění** pole.

![Odeslat nabídku názoru v sadě Visual Studio](media/quickstart-IDE-send-feedback.png)

## <a name="next-steps"></a>Další kroky

Jsme se zabývali jenom některé funkce sady Visual Studio k seznámit s uživatelským rozhraním. Chcete-li podrobněji:

> [!div class="nextstepaction"]
> [Další informace o editoru kódu](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Seznamte se s projekty a řešení](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Viz také:

- [Přehled prostředí IDE sady Visual Studio](../get-started/visual-studio-ide.md)
- [Další funkce sady Visual Studio 2017](../ide/advanced-feature-overview.md)
- [Změna barvy motivu a písma](../ide/quickstart-personalize-the-ide.md)
