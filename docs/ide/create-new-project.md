---
title: Vytvoření nového projektu
description: Naučte se, jak vytvořit nový projekt v aplikaci Visual Studio.
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
ms.openlocfilehash: 97d585f8c484f1ef8b4cbd0514585d6f328af67c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956877"
---
# <a name="create-a-new-project-in-visual-studio"></a>Vytvoření nového projektu v aplikaci Visual Studio

V tomto článku vám ukážeme, jak rychle vytvořit nový projekt v aplikaci Visual Studio.

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Otevření dialogového okna Nový projekt

Existuje několik způsobů, jak vytvořit nový projekt v aplikaci Visual Studio 2017. Na úvodní stránce můžete zadat název šablony projektu v poli **Hledat šablony projektů** nebo kliknutím na odkaz **vytvořit nový projekt** otevřít dialogové okno **Nový projekt** . Kromě na úvodní stránce můžete také vybrat **soubor**  >  **Nový**  >  **projekt** na panelu nabídek nebo kliknout na tlačítko **Nový projekt** na panelu nástrojů.

![Snímek obrazovky s panelem nabídek v aplikaci Visual Studio se souborem > nové možnosti projektu > vybrány.](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Vybrat typ šablony

V dialogovém okně **Nový projekt** se zobrazí dostupné šablony projektu v seznamu v kategorii **šablony** . Šablony jsou uspořádány podle programovacího jazyka a typu projektu, jako je například Visual C#, JavaScript a Azure Data Lake.

![Snímek obrazovky dialogového okna Nový projekt, ve kterém se zobrazuje seznam nainstalovaných šablon.](./media/vside-newproject-templates-list.png)

> [!NOTE]
> Seznam dostupných jazyků a šablon projektů, které se zobrazí, závisí na verzi sady Visual Studio, kterou používáte, a na nainstalovaných úlohách. Další informace o tom, jak nainstalovat další úlohy, najdete v tématu [Změna sady Visual Studio přidáním nebo odebráním úloh a součástí](../install/modify-visual-studio.md).

Zobrazte seznam šablon pro programovací jazyk, který chcete použít, kliknutím na trojúhelník vedle názvu jazyka a následným výběrem kategorie projektu (například Windows Desktop).

Následující obrázek ukazuje šablony projektu dostupné pro projekty Visual C# .NET Core:

![Snímek obrazovky dialogového okna Nový projekt se seznamem šablon projektů, ze kterých můžete vybírat.](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Konfigurace projektu

Do pole **název** zadejte název nového projektu. Projekt můžete uložit ve výchozím umístění v počítači nebo kliknutím na tlačítko **Procházet** vyhledat jiné umístění. Můžete také vybrat název řešení nebo přidat nový projekt do úložiště Git (výběrem možnosti **Přidat do správy zdrojového kódu**).

Kliknutím na tlačítko **OK** vytvořte řešení a projekt.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Otevřete stránku vytvořit nový projekt.

Existuje několik způsobů, jak vytvořit nový projekt v aplikaci Visual Studio 2019. Při prvním spuštění sady Visual Studio se zobrazí okno Start a odtud můžete vybrat možnost **vytvořit nový projekt**.

:::image type="content" source="media/vs-2019/start-window-create-new-project.png" alt-text="Snímek obrazovky dialogového okna vytvořit nový projekt z okna Start v aplikaci Visual Studio 2019":::

Pokud je vývojové prostředí sady Visual Studio již otevřeno, můžete vytvořit nový projekt výběrem možnosti **soubor**  >  **Nový**  >  **projekt** na panelu nabídek. Můžete také kliknout na tlačítko **Nový projekt** na panelu nástrojů nebo stisknout klávesy **CTRL** + **SHIFT** + **N**.

:::image type="content" source="media/vs-2019/new-project-button.png" alt-text="Snímek obrazovky s tlačítkem nový projekt v aplikaci Visual Studio 2019":::

## <a name="select-a-template-type"></a>Vybrat typ šablony

Na stránce **vytvořit nový projekt** se zobrazí seznam naposledy vybraných šablon na levé straně. Šablony jsou seřazené podle *posledního použití*.

Pokud nevyberete z naposledy použitých šablon, můžete filtrovat všechny dostupné šablony projektu podle **jazyka** (například C# nebo C++), **platformy** (například Windows nebo Azure), a **typu projektu** (například Desktop nebo Web). Můžete také zadat hledaný text do vyhledávacího pole, chcete-li dále filtrovat šablony, například **ASP.NET**.

:::image type="content" source="media/vs-2019/create-new-project-filters.png" alt-text="Snímek obrazovky s filtry šablon projektů v aplikaci Visual Studio 2019.":::

Značky, které se zobrazí pod každou šablonou, odpovídají třem filtrům rozevíracích seznamů (jazyk, platforma a typ projektu).

> [!TIP]
> Pokud nevidíte šablonu, kterou hledáte, možná nemáte k dispozici úlohu pro Visual Studio. Pokud chcete nainstalovat další úlohy, třeba vývoj pro **vývoj pro Azure** nebo **vývoj mobilních aplikací pomocí .NET**, klikněte na odkaz **instalovat další nástroje a funkce** a otevřete instalační program pro Visual Studio. Odtud vyberte úlohy, které chcete nainstalovat, a pak vyberte **Upravit**. Pak budou k dispozici další šablony projektů, ze kterých si můžete vybrat.
>
> :::image type="content" source="media/vs-2019/install-more-tools-features.png" alt-text="Snímek obrazovky s odkazem pro instalaci dalších nástrojů a funkcí v aplikaci Visual Studio 2019.":::

Vyberte šablonu a pak klikněte na **Další**.

## <a name="configure-your-project"></a>Konfigurace projektu

Stránka **Konfigurovat nový projekt** obsahuje možnosti pro pojmenování projektu (a řešení), výběr umístění na disku a výběr verze architektury (Pokud je k dispozici pro šablonu, kterou jste zvolili).

:::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Snímek stránky konfigurace nového projektu v aplikaci Visual Studio 2019":::

> [!NOTE]
> Pokud vytvoříte nový projekt, když již máte projekt nebo řešení otevřené v aplikaci Visual Studio, je k dispozici další možnost konfigurace. Můžete zvolit vytvoření nového řešení nebo přidat nový projekt do již otevřeného řešení.
>
> :::image type="content" source="media/vs-2019/configure-new-project-solution.png" alt-text="Snímek obrazovky s dialogovým oknem vytvořit nové řešení nebo přidat do řešení v aplikaci Visual Studio 2019":::

Kliknutím na **vytvořit** vytvořte nový projekt.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Přidání dalších projektů do řešení

Pokud chcete přidat další projekt do řešení, klikněte pravým tlačítkem myši na uzel řešení v **Průzkumník řešení** a pak vyberte **Přidat**  >  **Nový projekt**.

> [!TIP]
> Příklad projektu a řešení vytvořeného od začátku, dokončení s podrobnými pokyny a ukázkový kód naleznete v tématu [Úvod do projektů a řešení](../get-started/tutorial-projects-solutions.md).

## <a name="see-also"></a>Viz také

- [Seznámení s projekty a řešení](../get-started/tutorial-projects-solutions.md)
- [Práce s řešeními a projekty](creating-solutions-and-projects.md)
- [Správa vlastností projektu a řešení](managing-project-and-solution-properties.md)
- [Vytváření projektů (Visual Studio pro Mac)](/visualstudio/mac/create-new-projects)