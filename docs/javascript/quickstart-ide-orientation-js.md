---
title: První seznámení s integrovaným vývojovým prostředím sady Visual Studio
description: Seznamte se s integrovaným vývojovým prostředím (IDE) sady Visual Studio, včetně oken, nabídek a dalších funkcí uživatelského rozhraní, které se běžně používají.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/05/2019
ms.topic: quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f80dd85e1cc8f93784ed938ef1788730b3c926e8
ms.sourcegitcommit: a7944c325bedd8efbb244452741864089a02f5db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2020
ms.locfileid: "91947814"
---
# <a name="first-look-at-the-visual-studio-ide"></a>První seznámení s integrovaným vývojovým prostředím sady Visual Studio

V tomto 5-10 minutách Úvod do integrovaného vývojového prostředí (IDE) sady Visual Studio se podíváme na některé z oken, nabídek a dalších funkcí uživatelského rozhraní.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a> Úvodní okno

První věc, kterou se zobrazí po spuštění sady Visual Studio, je okno Start. Okno Start je navrženo tak, aby vám pomohla rychleji "získat kód". Obsahuje možnosti, jak zavřít nebo rezervovat kód, otevřít existující projekt nebo řešení, vytvořit nový projekt nebo jednoduše otevřít složku, která obsahuje nějaké soubory kódu.

[![Okno Start v aplikaci Visual Studio 2019](media/vs-2019/start-window.png)](media/vs-2019/start-window.png)

Pokud používáte Visual Studio poprvé, váš seznam posledních projektů bude prázdný.

Pokud pracujete s kódy základů kódu, které nejsou založené na MSBuild, použijete možnost **otevřít místní složku** pro otevření kódu v aplikaci Visual Studio. Další informace naleznete v tématu [vývoj kódu v aplikaci Visual Studio bez projektů nebo řešení](develop-javascript-code-without-solutions-projects.md). V opačném případě můžete vytvořit nový projekt nebo naklonovat projekt ze zdrojového poskytovatele, jako je GitHub nebo Azure DevOps.

Možnost **pokračovat bez kódu** jednoduše otevře vývojové prostředí sady Visual Studio bez jakéhokoli konkrétního projektu nebo načteného kódu. Tuto možnost můžete zvolit, chcete-li připojit relaci [Live Share](/visualstudio/liveshare/) nebo připojit k procesu pro ladění. Můžete také stisknutím klávesy **ESC** zavřít okno Start a otevřít integrované vývojové prostředí (IDE).

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Úvodní stránka

První věc, kterou se zobrazí po spuštění sady Visual Studio, je největší pravděpodobně **úvodní stránkou**. **Úvodní stránka** je navržena jako "centrum", která vám pomůžou najít příkazy a soubory projektu, které potřebujete rychleji. V části **Poslední** se zobrazují projekty a složky, které jste nedávno pracovali. V části **Nový projekt**můžete kliknout na odkaz pro otevření dialogového okna **Nový projekt** nebo v části **otevřít**můžete otevřít existující projekt kódu nebo složku. Napravo je informační kanál nejnovějších příspěvků pro vývojáře.

![Úvodní stránka v aplikaci Visual Studio](media/start-page.png)

Pokud zavřete **úvodní stránku** a chcete ji znovu zobrazit, můžete ji znovu otevřít z nabídky **soubor** .

![Nabídka soubor v aplikaci Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Abychom mohli pokračovat v prozkoumávání funkcí sady Visual Studio, vytvoříme nový projekt.

::: moniker range=">=vs-2019"

1. V okně Start vyberte možnost **vytvořit nový projekt**a potom do vyhledávacího pole zadejte **JavaScript** , aby se vyfiltroval seznam typů projektů, které v názvu nebo typu jazyka obsahují text "JavaScript".

   Visual Studio poskytuje různé druhy šablon projektů, které vám pomohou rychle začít kódovat. (Případně, pokud jste vývojář TypeScript, můžete vytvořit projekt v tomto jazyce. Uživatelské rozhraní, které budeme hledat, je podobné jako u všech programovacích jazyků.)

   ![Hledat v šablonách projektů v okně Start sady Visual Studio](media/vs-2019/create-new-project.png)

1. Vyberte prázdnou šablonu projektu **Node.js webové aplikace** a klikněte na **Další**.

1. V dialogovém okně **Konfigurovat nový projekt** , které se zobrazí, přijměte výchozí název projektu a klikněte na **vytvořit**.

::: moniker-end

::: moniker range="vs-2017"

1. Na **úvodní stránce**zadejte do pole Hledat v části **Nový projekt**text v **jazyce JavaScript** , aby se seznam typů projektů vyfiltroval na ty, které v názvu nebo typu jazyka obsahují text "JavaScript".

   ![Hledat v šablonách projektů na úvodní stránce Visual studia](media/start-page-search-templates.png)

   Visual Studio poskytuje různé druhy šablon projektů, které vám pomohou rychle začít kódovat. Vyberte prázdnou šablonu projektu **Node.js webové aplikace** . (Případně, pokud jste vývojář TypeScript, můžete vytvořit projekt v tomto jazyce. Uživatelské rozhraní, které budeme hledat, je podobné jako u všech programovacích jazyků.)

1. V dialogovém okně **Nový projekt** , které se zobrazí, přijměte výchozí název projektu a klikněte na **tlačítko OK**.
::: moniker-end

   Projekt je vytvořen a v okně **editoru** se otevře soubor s názvem *server.js* . **Editor** zobrazuje obsah souborů a je tam, kde provedete většinu práce s kódováním v aplikaci Visual Studio.

   ![Editor v aplikaci Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Průzkumník řešení

**Průzkumník řešení**, který je obvykle na pravé straně aplikace Visual Studio, zobrazuje grafické znázornění hierarchie souborů a složek ve složce projektu, řešení nebo kódu. Můžete procházet hierarchii a přejít k souboru v **Průzkumník řešení**.

![Průzkumník řešení v aplikaci Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Nabídky

Panel nabídek podél horního okraje příkazů skupiny sady Visual Studio do kategorií. Například nabídka **projekt** obsahuje příkazy týkající se projektu, ve kterém pracujete. V nabídce **nástroje** můžete přizpůsobit, jak se aplikace Visual Studio chová, výběrem **možností**nebo přidáním funkcí do instalace výběrem možnosti **získat nástroje a funkce**.

![Panel nabídek v aplikaci Visual Studio](media/quickstart-IDE-menu-bar.png)

Pojďme otevřít okno **Seznam chyb** tím, že kliknete na nabídku **zobrazení** a pak **Seznam chyb**.

## <a name="error-list"></a>Seznam chyb

**Seznam chyb** zobrazí chyby, varování a zprávy týkající se aktuálního stavu kódu. Pokud jsou v souboru nějaké chyby (například chybějící složená závorka nebo středník) nebo kdekoli v projektu, jsou zde uvedeny.

![Seznam chyb v aplikaci Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Výstup – okno

V okně **výstup** se zobrazí výstupní zprávy ze sestavení projektu a ze svého poskytovatele správy zdrojů.

Pojďme sestavit projekt, aby se zobrazil výstup sestavení. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**. Okno **výstup** automaticky získá fokus a zobrazí zprávu o úspěšném sestavení.

![Okno výstup v aplikaci Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Vyhledávací pole

Vyhledávací pole představuje rychlý a snadný způsob, jak v aplikaci Visual Studio dělat poměrně mnoho všeho. Můžete zadat nějaký text týkající se toho, co chcete udělat, a zobrazí se seznam možností, které se týkají tohoto textu. Představte si například, že chcete zvýšit úroveň podrobností výstupu sestavení a zobrazit další podrobnosti o tom, co právě sestavuje. Můžete to udělat takto:

1. Do vyhledávacího pole zadejte **Podrobnosti** . V zobrazených výsledcích vyberte **projekty a řešení – > sestavovat a spouštět** v kategorii **Možnosti** .

   ![Vyhledávací pole v aplikaci Visual Studio](media/quickstart-IDE-quick-launch.png)

   Dialogové okno **Možnosti** se otevře na stránce možnosti **sestavení a spuštění** .

1. V části **Podrobnosti výstupu sestavení projektu nástroje MSBuild**zvolte možnost **normální**a pak klikněte na tlačítko **OK**.

1. Sestavte projekt znovu tak, že kliknete pravým tlačítkem na projekt **NodejsWebApp1** v **Průzkumník řešení** a z kontextové nabídky zvolíte **znovu sestavit** .

   Tentokrát okno **výstup** zobrazuje podrobné protokolování z procesu sestavení, včetně toho, které soubory byly zkopírovány tam, kde.

   ![Podrobný výstup sestavení v aplikaci Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Nabídka Odeslat názor

Pokud máte v aplikaci Visual Studio nějaké problémy, nebo pokud máte návrhy na to, jak produkt vylepšit, můžete použít nabídku **Odeslat názor** v horní části okna sady Visual Studio.

![Nabídka Odeslat názor v aplikaci Visual Studio](../ide/media/quickstart-ide-send-feedback.png)

## <a name="next-steps"></a>Další kroky

Prohlédli jsme si jenom několik funkcí sady Visual Studio, abyste se seznámili s uživatelským rozhraním. Další zkoumání:

> [!div class="nextstepaction"]
> [Další informace o editoru kódu](write-and-edit-code.md)

> [!div class="nextstepaction"]
> [Další informace o projektech a řešeních](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Viz také

- [Přehled integrovaného vývojového prostředí (IDE) sady Visual Studio](../get-started/visual-studio-ide.md)
- [Další funkce sady Visual Studio 2017](../ide/advanced-feature-overview.md)
- [Změna barev motivu a písma](../ide/quickstart-personalize-the-ide.md)
