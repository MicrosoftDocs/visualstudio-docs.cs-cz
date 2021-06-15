---
title: Vytvoření nového projektu
description: Zjistěte, jak vytvořit nový projekt v Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/23/2020
ms.topic: how-to
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05cfb7cf053a3275b49b76b46bec8054fb105078
ms.sourcegitcommit: 529e1716924c3e1ac8a750550b996ad3c79f353b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/14/2021
ms.locfileid: "112066953"
---
# <a name="create-a-new-project-in-visual-studio"></a>Vytvoření nového projektu v Visual Studio

V tomto článku vám ukážeme, jak rychle vytvořit nový projekt v Visual Studio ze šablony.

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Otevření dialogového okna Nový projekt

Existuje několik způsobů, jak vytvořit nový projekt v Visual Studio 2017. Na stránce Start můžete zadat název šablony projektu  do pole Hledat šablony  projektů nebo výběrem odkazu Vytvořit nový projekt otevřít dialogové **okno** Nový projekt. Kromě úvodní stránky můžete také na řádku nabídek vybrat File New Project (Soubor nového projektu) nebo kliknout na tlačítko  >    >   **New Project** (Nový projekt) na panelu nástrojů.

![Snímek obrazovky s panelem nabídek Visual Studio s vybranými možnostmi > Nový > projekt](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Výběr typu šablony

V dialogovém **okně Nový** projekt se dostupné šablony projektů zobrazí v seznamu v **kategorii Šablony.** Šablony jsou uspořádané podle programovacího jazyka a typu projektu, jako jsou Visual C#, JavaScript a Azure Data Lake.

![Snímek obrazovky s dialogem Nový projekt se seznamem nainstalovaných šablon](./media/vside-newproject-templates-list.png)

> [!NOTE]
> Seznam dostupných jazyků a šablon projektů, který se zobrazí, závisí na verzi Visual Studio které používáte, a nainstalovaných úlohách. Další informace o instalaci dalších úloh najdete v tématu Úprava Visual Studio přidáním nebo [odebráním úloh](../install/modify-visual-studio.md)a komponent.

Kliknutím na trojúhelník vedle názvu jazyka a zvolením kategorie projektu (například Plocha Windows) zobrazte seznam šablon pro programovací jazyk, který chcete použít.

Následující obrázek ukazuje šablony projektů dostupné pro projekty Visual C# .NET Core:

![Snímek obrazovky s dialogem Nový projekt se seznamem šablon projektů, ze které si můžete vybrat](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Konfigurace projektu

Do pole Název zadejte název nového **projektu.** Projekt můžete uložit do výchozího umístění v počítači nebo můžete kliknout na **tlačítko Procházet** a najít jiné umístění. Můžete také vybrat název řešení nebo přidat nový projekt do úložiště Git (výběrem možnosti Přidat do **správy zdrojového kódu).**

Kliknutím **na OK** vytvořte řešení a projekt.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Otevření stránky Vytvořit nový projekt

Existuje několik způsobů, jak vytvořit nový projekt v Visual Studio 2019. Při prvním otevření Visual Studio se zobrazí úvodní okno a odtud můžete vybrat **Vytvořit nový projekt**.

:::image type="content" source="media/vs-2019/start-window-create-new-project.png" alt-text="Snímek obrazovky s dialogem Vytvořit nový projekt z úvodního okna v Visual Studio 2019":::

Pokud je Visual Studio prostředí otevřené, můžete vytvořit nový projekt tak, že na řádku nabídek zvolíte File   >  **New**  >  **Project (Soubor** nový projekt). Můžete také kliknout na **tlačítko Nový projekt** na panelu nástrojů nebo stisknout **Ctrl** + **Shift** + **N**.

:::image type="content" source="media/vs-2019/new-project-button.png" alt-text="Snímek obrazovky s tlačítkem Nový projekt Visual Studio 2019":::

## <a name="select-a-template-type"></a>Výběr typu šablony

Na **stránce Vytvořit nový projekt** se vlevo zobrazí seznam naposledy vybraných šablon. Šablony jsou seřazené podle naposledy *použitých šablon*.

Pokud nevybýádáte z naposledy použitých šablon, můžete filtrovat všechny dostupné šablony projektů podle jazyka **(například** C# nebo C++), **platformy** (například Windows nebo Azure) a typu projektu **(například** Desktop nebo Web). Můžete také zadat hledaný text do vyhledávacího pole a dále filtrovat šablony, například **asp.net**.

:::image type="content" source="media/vs-2019/create-new-project-filters.png" alt-text="Snímek obrazovky s filtry šablony projektu Visual Studio 2019":::

Značky, které se zobrazují pod jednotlivými šablonami, odpovídají třem filtrům rozevíracího seznamu (Jazyk, Platforma a Typ projektu).

> [!TIP]
> Pokud šablonu, kterou hledáte, nevidíte, možná vám chybí úloha pro Visual Studio. Pokud chcete nainstalovat další úlohy, například **Vývoj pro Azure** nebo Vývoj pro mobilní zařízení pomocí **.NET,** kliknutím na odkaz Nainstalovat **další** nástroje a funkce otevřete Instalační program pro Visual Studio. Tady vyberte úlohy, které chcete nainstalovat, a pak vyberte **Upravit.** Potom budou k dispozici další šablony projektů, ze které si můžete vybrat.
>
> :::image type="content" source="media/vs-2019/install-more-tools-features.png" alt-text="Snímek obrazovky s odkazem Nainstalovat další nástroje a funkce v Visual Studio 2019":::

Vyberte šablonu a potom klikněte na **Další.**

## <a name="configure-your-project"></a>Konfigurace projektu

Stránka **Configure your new project** (Konfigurace nového projektu) obsahuje možnosti pro název projektu (a řešení), výběr umístění disku a výběr verze architektury (pokud je k dispozici pro šablonu, kterou jste zvolili).

:::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Snímek obrazovky se stránkou Konfigurovat nový projekt v Visual Studio 2019":::

> [!NOTE]
> Pokud vytvoříte nový projekt, pokud už máte projekt nebo řešení otevřené v Visual Studio, je k dispozici další možnost konfigurace. Můžete se rozhodnout vytvořit nové řešení nebo přidat nový projekt do řešení, které je už otevřené.
>
> :::image type="content" source="media/vs-2019/configure-new-project-solution.png" alt-text="Snímek obrazovky s dialogem Vytvořit nové řešení nebo Přidat do řešení v Visual Studio 2019":::

Kliknutím **na** Vytvořit vytvořte nový projekt.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Přidání dalších projektů do řešení

Pokud chcete do řešení přidat další projekt, klikněte pravým  tlačítkem na uzel řešení v Průzkumník řešení pak vyberte **Přidat**  >  **nový projekt**.

> [!TIP]
> Příklad projektu a řešení vytvořeného od začátku s podrobnými pokyny a ukázkovým kódem najdete v tématu Úvod do projektů a [řešení.](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Viz také

- [Úvod do projektů a řešení](../get-started/tutorial-projects-solutions.md)
- [Práce s řešeními a projekty](creating-solutions-and-projects.md)
- [Správa vlastností projektu a řešení](managing-project-and-solution-properties.md)
- [Vytváření projektů (Visual Studio pro Mac)](/visualstudio/mac/create-new-projects)
