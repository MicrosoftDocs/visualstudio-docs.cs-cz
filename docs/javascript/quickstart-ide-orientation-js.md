---
title: Prohlídka ide sady Visual Studio
titleSuffix: ''
ms.date: 02/05/2019
ms.topic: quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7a05f62685509a69fd5dfe8f758b4e5599b9324
ms.sourcegitcommit: 334024a43477290ecc610e70c80a0f772787a7d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80527937"
---
# <a name="first-look-at-the-visual-studio-ide"></a>První seznámení s integrovaným vývojovým prostředím sady Visual Studio

V tomto 5-10 minut úvod do integrovaného vývojového prostředí Visual Studio (IDE), budeme mít prohlídku některých oken, nabídek a dalších funkcí ui.

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a> Úvodní okno

První věc, kterou uvidíte po spuštění sady Visual Studio, je počáteční okno. Počáteční okno je navrženo tak, aby vám pomohlo rychleji se dostat ke kódu. Má možnosti zavřít nebo rezervovat kód, otevřít existující projekt nebo řešení, vytvořit nový projekt nebo jednoduše otevřít složku, která obsahuje některé soubory kódu.

[![Počáteční okno v Sadě Visual Studio 2019](media/vs-2019/start-window.png)](media/vs-2019/start-window.png)

Pokud používáte visual studio poprvé, bude seznam posledních projektů prázdný.

Pokud pracujete s kódovými základnami nezaloženými na MSBuild, použijete možnost **Otevřít místní složku** k otevření kódu v sadě Visual Studio. Další informace naleznete [v tématu Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](develop-javascript-code-without-solutions-projects.md). V opačném případě můžete vytvořit nový projekt nebo klonovat projekt od zdrojového zprostředkovatele, jako je GitHub nebo Azure DevOps.

Možnost **Pokračovat bez kódu** jednoduše otevře vývojové prostředí sady Visual Studio bez načtení konkrétního projektu nebo kódu. Tuto možnost můžete zvolit, chcete-li se připojit k relaci [živého sdílení](/visualstudio/liveshare/) nebo připojit k procesu ladění. Můžete také stisknutím **klávesy Esc** zavřít počáteční okno a otevřít ide.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Úvodní stránka

První věc, kterou uvidíte po spuštění sady Visual Studio, je s největší pravděpodobností **úvodní stránka**. **Úvodní stránka** je navržena jako "rozbočovač", který vám pomůže rychleji najít příkazy a soubory projektu, které potřebujete. V části **Poslední** se zobrazují projekty a složky, na kterých jste v poslední době pracovali. V části **Nový projekt**můžete klepnutím na odkaz vyvolat dialogové okno **Nový projekt** nebo v části **Otevřít**můžete otevřít existující projekt kódu nebo složku. Na pravé straně je krmivo z nejnovějších developer novinky.

![Úvodní stránka v Sadě Visual Studio](media/start-page.png)

Pokud úvodní **stránku** zavřete a chcete ji znovu zobrazit, můžete ji znovu otevřít z nabídky **Soubor.**

![Nabídka Soubor v sadě Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Chcete-li pokračovat ve zkoumání funkcí sady Visual Studio, vytvořte nový projekt.

::: moniker range=">=vs-2019"

1. V úvodním okně vyberte **Vytvořit nový projekt**a potom ve vyhledávacím poli v **javascriptu** vyfiltrujte seznam typů projektů na ty, které obsahují javascript v jejich názvu nebo typu jazyka.

   Visual Studio poskytuje různé druhy šablon projektů, které vám pomohou začít rychle kódovat. (Případně, pokud jste vývojář typu TypeScript, neváhejte a vytvořte projekt v tomto jazyce. UI budeme při pohledu na je podobný pro všechny programovací jazyky.)

   ![Hledání šablon projektů v počátečním okně sady Visual Studio](media/vs-2019/create-new-project.png)

1. Zvolte šablonu projektu **webové aplikace Blank Node.js** a klepněte na tlačítko **Další**.

1. V zobrazeném **dialogovém okně Konfigurovat nový projekt** přijměte výchozí název projektu a zvolte **Vytvořit**.

::: moniker-end

::: moniker range="vs-2017"

1. Na **úvodní stránce**do vyhledávacího pole v části **Nový projekt**zadejte **javascript,** chcete-li filtrovat seznam typů projektů na ty, které obsahují "javascript" v jejich názvu nebo typu jazyka.

   ![Hledání šablon projektů na úvodní stránce sady Visual Studio](media/start-page-search-templates.png)

   Visual Studio poskytuje různé druhy šablon projektů, které vám pomohou začít rychle kódovat. Zvolte šablonu projektu **webové aplikace Blank Node.js.** (Případně, pokud jste vývojář typu TypeScript, neváhejte a vytvořte projekt v tomto jazyce. UI budeme při pohledu na je podobný pro všechny programovací jazyky.)

1. V zobrazeném dialogovém okně **Nový projekt** přijměte výchozí název projektu a zvolte **OK**.
::: moniker-end

   Projekt je vytvořen a v okně **Editor** se otevře soubor s názvem *server.js.* **Editor** zobrazuje obsah souborů a je místo, kde budete dělat většinu své práce kódování v sadě Visual Studio.

   ![Editor v sadě Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Průzkumník řešení

**Průzkumník řešení**, který je obvykle na pravé straně sady Visual Studio, zobrazuje grafické znázornění hierarchie souborů a složek ve složce projektu, řešení nebo kódu. Hierarchii můžete procházet a přejít k souboru v **Průzkumníku řešení**.

![Průzkumník řešení v sadě Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Nabídky

Řádek nabídek v horní části Visual Studio seskupí příkazy do kategorií. Nabídka **Projekt** například obsahuje příkazy související s projektem, ve kterém pracujete. V nabídce **Nástroje** můžete přizpůsobit způsob, jakým se visual studio chová, výběrem **možnosti nebo**přidáním funkcí do instalace výběrem **možnosti Získat nástroje a funkce**.

![Panel nabídek v sadě Visual Studio](media/quickstart-IDE-menu-bar.png)

Otevřeme okno **Seznam chyb** výběrem nabídky **Zobrazení** a potom v **seznamu chyb**.

## <a name="error-list"></a>Seznam chyb

**Seznam chyb** zobrazuje chyby, upozornění a zprávy týkající se aktuálního stavu kódu. Pokud se v souboru nebo kdekoli v projektu nacházejí chyby (například chybějící závorka nebo středník), jsou zde uvedeny.

![Seznam chyb v sadě Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Výstup – okno

Okno **Výstup** zobrazuje výstupní zprávy z vytváření projektu a od poskytovatele správy zdrojového kódu.

Pojďme sestavit projekt vidět některé výstup sestavení. V nabídce **Sestavení** zvolte **Build Solution**. **Okno Výstup** automaticky získá fokus a zobrazí zprávu úspěšnésestavení.

![Okno výstupu v sadě Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Vyhledávací pole

Vyhledávací pole je rychlý a snadný způsob, jak v sadě Visual Studio provést téměř cokoli. Můžete zadat text související s tím, co chcete udělat, a zobrazí se seznam možností, které se týkají textu. Představte si například, že chcete zvýšit podrobnost výstupu sestavení, abyste zobrazili další podrobnosti o tom, co přesně sestavení dělá. Zde je návod, jak byste to mohli udělat:

1. Do vyhledávacího pole zadejte **podrobnost.** Ze zobrazených výsledků zvolte **Projekty a řešení --> Sestavení a spuštění** v kategorii **Možnosti.**

   ![Vyhledávací pole ve Visual Studiu](media/quickstart-IDE-quick-launch.png)

   Otevře se dialogové okno **Možnosti** na stránce Možnosti **sestavení a spuštění.**

1. V části **MSBuild projektu vytvořit podrobnost výstupu**zvolte **Normální**a klepněte na tlačítko **OK**.

1. Sestavte projekt znovu kliknutím pravým tlačítkem myši na projekt **NodejsWebApp1** v **Průzkumníku řešení** a výběrem **příkazu Znovu sestavit** z kontextové nabídky.

   Tentokrát **output** okno zobrazuje podrobnější protokolování z procesu sestavení, včetně souborů, které byly zkopírovány kde.

   ![Podrobný výstup sestavení v sadě Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Nabídka Odeslat zpětnou vazbu

Pokud při používání sady Visual Studio narazíte na nějaké problémy nebo pokud máte návrhy, jak vylepšit produkt, můžete použít nabídku **Odeslat zpětnou vazbu** v horní části okna sady Visual Studio.

![Nabídka Odeslat zpětnou vazbu v sadě Visual Studio](../ide/media/quickstart-ide-send-feedback.png)

## <a name="next-steps"></a>Další kroky

Podívali jsme se na několik funkcí sady Visual Studio seznámit se s uživatelským rozhraním. Další zkoumání:

> [!div class="nextstepaction"]
> [Další informace o editoru kódu](write-and-edit-code.md)

> [!div class="nextstepaction"]
> [Další informace o projektech a řešeních](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Viz také

- [Přehled ide sady Visual Studio](../get-started/visual-studio-ide.md)
- [Další funkce Visual Studia 2017](../ide/advanced-feature-overview.md)
- [Změna motivu a barev písma](../ide/quickstart-personalize-the-ide.md)
