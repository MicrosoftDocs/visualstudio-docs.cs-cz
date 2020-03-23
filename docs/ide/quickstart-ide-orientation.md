---
title: Prohlídka ide sady Visual Studio
titleSuffix: ''
ms.date: 02/21/2019
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 490d3edddd35ad5d72733824e3af41888839e946
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75596967"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Úvodní příručka: První pohled na ide sady Visual Studio

V tomto 5-10 minut úvod do integrovaného vývojového prostředí Visual Studio (IDE), budeme mít prohlídku některých oken, nabídek a dalších funkcí ui.

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Úvodní stránka

První věc, kterou uvidíte po otevření sady Visual Studio, je s největší pravděpodobností **úvodní stránka**. **Úvodní stránka** je navržena jako "rozbočovač", který vám pomůže rychleji najít příkazy a soubory projektu, které potřebujete. V části **Poslední** se zobrazují projekty a složky, na kterých jste v poslední době pracovali. V části **Nový projekt**můžete klepnutím na odkaz vyvolat dialogové okno **Nový projekt** nebo v části **Otevřít**můžete otevřít existující projekt kódu nebo složku. Na pravé straně je krmivo z nejnovějších developer novinky.

![Úvodní stránka v Sadě Visual Studio](media/start-page.png)

Pokud úvodní **stránku** zavřete a chcete ji znovu zobrazit, můžete ji znovu otevřít z nabídky **Soubor.**

![Nabídka Soubor v sadě Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a> Úvodní okno

První věc, kterou uvidíte po otevření sady Visual Studio je počáteční okno. Počáteční okno je navrženo tak, aby vám pomohlo rychleji se dostat ke kódu. Má možnosti klonovat nebo rezervovat kód, otevřít existující projekt nebo řešení, vytvořit nový projekt nebo jednoduše otevřít složku, která obsahuje některé soubory kódu.

[![Počáteční okno v Visual Studiu 2019](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Pokud používáte visual studio poprvé, bude seznam posledních projektů prázdný.

Pokud pracujete s kódovými základnami nezaloženými na MSBuild, použijete možnost **Otevřít místní složku** k otevření kódu v sadě Visual Studio. Další informace naleznete [v tématu Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](develop-code-in-visual-studio-without-projects-or-solutions.md). V opačném případě můžete vytvořit nový projekt nebo klonovat projekt od zdrojového zprostředkovatele, jako je GitHub nebo Azure DevOps.

Možnost **Pokračovat bez kódu** jednoduše otevře vývojové prostředí sady Visual Studio bez načtení konkrétního projektu nebo kódu. Tuto možnost můžete zvolit, chcete-li se připojit k relaci [živého sdílení](/visualstudio/liveshare/) nebo připojit k procesu ladění. Můžete také stisknutím **klávesy Esc** zavřít počáteční okno a otevřít ide.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Chcete-li pokračovat ve zkoumání funkcí sady Visual Studio, vytvořte nový projekt.

::: moniker range="vs-2017"

1. Na **úvodní stránce**do vyhledávacího pole v části **Nový projekt**zadejte do **konzoly,** chcete-li filtrovat seznam typů projektů na ty, které obsahují "konzolu" v jejich názvu.

   ![Hledání šablon projektů na úvodní stránce sady Visual Studio](media/start-page-search-templates.png)

   Visual Studio poskytuje různé druhy šablon projektů, které vám pomohou začít rychle kódovat. Zvolte šablonu projektu konzoly C# **Console (.NET Core).** (Případně pokud jste Visual Basic, C++, Javascript nebo jiný vývojář jazyka, neváhejte vytvořit projekt v jednom z těchto jazyků. UI budeme při pohledu na je podobný pro všechny programovací jazyky.)

1. V zobrazeném dialogovém okně **Nový projekt** přijměte výchozí název projektu a zvolte **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. V počátečním okně zvolte **Vytvořit nový projekt**.

   Otevře se dialogové okno s **nápisem Vytvořit nový projekt**. Zde můžete prohledávat, filtrovat a vybírat šablonu projektu. Zobrazuje také seznam naposledy použitých šablon projektů.

1. Do vyhledávacího pole v horní části zadejte **konzolu,** chcete-li filtrovat seznam typů projektů na ty, které obsahují "konzolu" v jejich názvu. Výsledky hledání dále upřesněte výběrem **jazyka C#** (nebo jiného jazyka podle vašeho výběru) z výběru **jazyka.**

   ![Dialogové okno Nový projekt v Sadě Visual Studio 2019](media/vs-2019/create-a-new-project.png)

1. Pokud jste jako jazyk vybrali c#, visual basic nebo f#, vyberte šablonu **Console App (.NET Core)** a pak zvolte **Další**. (Pokud jste vybrali jiný jazyk, stačí vybrat libovolnou šablonu. UI budeme při pohledu na je podobný pro všechny programovací jazyky.)

1. Na stránce **Konfigurovat nový projekt** přijměte výchozí název a umístění projektu a pak zvolte **Vytvořit**.

::: moniker-end

   Projekt je vytvořen a v okně **Editor** se otevře soubor s názvem *Program.cs.* **Editor** zobrazuje obsah souborů a je místo, kde budete dělat většinu své práce kódování v sadě Visual Studio.

   ![Editor v sadě Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Průzkumník řešení

**Průzkumník řešení**, který je obvykle na pravé straně sady Visual Studio, zobrazuje grafické znázornění hierarchie souborů a složek ve složce projektu, řešení nebo kódu. Hierarchii můžete procházet a přejít k souboru v **Průzkumníku řešení**.

![Průzkumník řešení v sadě Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Nabídky

Řádek nabídek v horní části Visual Studio seskupí příkazy do kategorií. Nabídka **Projekt** například obsahuje příkazy související s projektem, ve kterém pracujete. V nabídce **Nástroje** můžete přizpůsobit způsob, jakým se visual studio chová, výběrem **možnosti nebo**přidáním funkcí do instalace výběrem **možnosti Získat nástroje a funkce**.

::: moniker range="vs-2017"

![Panel nabídek v sadě Visual Studio 2017](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Panel nabídek v Sadě Visual Studio 2019](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Seznam chyb

Otevřete okno **Seznam chyb** výběrem nabídky **Zobrazení** a potom v **seznamu chyb**.

**Seznam chyb** zobrazuje chyby, upozornění a zprávy týkající se aktuálního stavu kódu. Pokud se v souboru nebo kdekoli v projektu nacházejí chyby (například chybějící závorka nebo středník), jsou zde uvedeny.

![Seznam chyb v sadě Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Okno Výstup

Okno **Výstup** zobrazuje výstupní zprávy z vytváření projektu a od poskytovatele správy zdrojového kódu.

Pojďme sestavit projekt vidět některé výstup sestavení. V nabídce **Sestavení** zvolte **Build Solution**. **Okno Výstup** automaticky získá fokus a zobrazí zprávu úspěšnésestavení.

![Okno výstupu v sadě Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Vyhledávací pole

Vyhledávací pole je rychlý a snadný způsob, jak přejít na téměř cokoli v sadě Visual Studio. Můžete zadat text související s tím, co chcete udělat, a zobrazí se seznam možností, které se týkají textu. Představte si například, že chcete zvýšit podrobnost výstupu sestavení, abyste zobrazili další podrobnosti o tom, co přesně sestavení dělá. Zde je návod, jak byste to mohli udělat:

::: moniker range="vs-2017"

1. Vyhledejte vyhledávací pole **snadného spuštění** v pravém horním části ide. (Případně k němu přistupujete stisknutím **klávesy Ctrl**+**Q.)**

2. Do vyhledávacího pole zadejte **podrobnost.** Ze zobrazených výsledků zvolte **Projekty a řešení --> Sestavení a spuštění** v kategorii **Možnosti.**

   ![Vyhledávací pole Rychlé spuštění ve Visual Studiu 2017](media/quickstart-IDE-quick-launch.png)

   Otevře se dialogové okno **Možnosti** na stránce Možnosti **sestavení a spuštění.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Stisknutím **klávesy Ctrl**+**Q** aktivujte vyhledávací pole v horní části ide.

2. Do vyhledávacího pole zadejte **podrobnost.** Ze zobrazených výsledků zvolte **Změnit podrobnost i nicotnosti msbuildu**.

   ![Vyhledávací pole ve Visual Studiu 2019](media/vs-2019/quick-launch-verbosity.png)

   Otevře se dialogové okno **Možnosti** na stránce Možnosti **sestavení a spuštění.**

::: moniker-end

3. V části **MSBuild projektu vytvořit podrobnost výstupu**zvolte **Normální**a klepněte na tlačítko **OK**.

4. Sestavte projekt znovu kliknutím pravým tlačítkem myši na projekt **ConsoleApp1** v **Průzkumníku řešení** a výběrem **příkazu Znovu sestavit** z kontextové nabídky.

   Tentokrát **output** okno zobrazuje podrobnější protokolování z procesu sestavení, včetně souborů, které byly zkopírovány kde.

   ![Podrobný výstup sestavení v sadě Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Nabídka Odeslat zpětnou vazbu

Pokud při používání sady Visual Studio narazíte na nějaké problémy nebo pokud máte návrhy, jak vylepšit produkt, můžete použít nabídku **Odeslat zpětnou vazbu** v horní části okna sady Visual Studio.

::: moniker range="vs-2017"

![Nabídka Odeslat zpětnou vazbu v Sadě Visual Studio 2017](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Nabídka Odeslat zpětnou vazbu v Sadě Visual Studio 2019](media/vs-2019/send-feedback-menu.png)

::: moniker-end

## <a name="next-steps"></a>Další kroky

Podívali jsme se na několik funkcí sady Visual Studio seznámit se s uživatelským rozhraním. Další zkoumání:

> [!div class="nextstepaction"]
> [Další informace o editoru kódu](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Další informace o projektech a řešeních](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Viz také

- [Přehled ide sady Visual Studio](../get-started/visual-studio-ide.md)
- [Další funkce sady Visual Studio](../ide/advanced-feature-overview.md)
- [Změna motivu a barev písma](../ide/quickstart-personalize-the-ide.md)
