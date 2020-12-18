---
title: Vytvoření nového projektu
description: Naučte se, jak vytvořit nový projekt v aplikaci Visual Studio.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 12/17/2020
ms.topic: how-to
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd8b6cb4819ae13b526eb5106bc7de3919d1a74f
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/18/2020
ms.locfileid: "97683979"
---
# <a name="create-a-new-project-in-visual-studio"></a>Vytvoření nového projektu v aplikaci Visual Studio

V tomto článku vám ukážeme, jak rychle vytvořit nový projekt v aplikaci Visual Studio.

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Otevření dialogového okna Nový projekt

Existuje několik způsobů, jak vytvořit nový projekt v aplikaci Visual Studio 2017. Na úvodní stránce můžete zadat název šablony projektu v poli **Hledat šablony projektů** nebo kliknutím na odkaz **vytvořit nový projekt** otevřít dialogové okno **Nový projekt** . Kromě na úvodní stránce můžete také vybrat **soubor**  >  **Nový**  >  **projekt** na panelu nabídek nebo kliknout na tlačítko **Nový projekt** na panelu nástrojů.

![Úvodní stránka a soubor > nový > projekt](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Vybrat typ šablony

V dialogovém okně **Nový projekt** se zobrazí dostupné šablony projektu v seznamu v kategorii **šablony** . Šablony jsou uspořádány podle programovacího jazyka a typu projektu, jako je například Visual C#, JavaScript a Azure Data Lake.

![Dialogové okno Nový projekt](./media/vside-newproject-templates-list.png)

> [!NOTE]
> Seznam dostupných jazyků a šablon projektů, které se zobrazí, závisí na verzi sady Visual Studio, kterou používáte, a na nainstalovaných úlohách. Další informace o tom, jak nainstalovat další úlohy, najdete v tématu [Změna sady Visual Studio přidáním nebo odebráním úloh a součástí](../install/modify-visual-studio.md).

Zobrazte seznam šablon pro programovací jazyk, který chcete použít, kliknutím na trojúhelník vedle názvu jazyka a následným výběrem kategorie projektu (například Windows Desktop).

Následující obrázek ukazuje šablony projektu dostupné pro projekty Visual C# .NET Core:

![Šablony projektů](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Konfigurace projektu

Do pole **název** zadejte název nového projektu. Projekt můžete uložit ve výchozím umístění v počítači nebo kliknutím na tlačítko **Procházet** vyhledat jiné umístění. Můžete také vybrat název řešení nebo přidat nový projekt do úložiště Git (výběrem možnosti **Přidat do správy zdrojového kódu**).

Kliknutím na tlačítko **OK** vytvořte řešení a projekt.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Otevřete stránku vytvořit nový projekt.

Existuje několik způsobů, jak vytvořit nový projekt v aplikaci Visual Studio 2019. Při prvním spuštění sady Visual Studio se zobrazí okno Start a odtud můžete vybrat možnost **vytvořit nový projekt**.

![Vytvoření nového projektu z okna Start v aplikaci Visual Studio 2019](media/vs-2019/start-window-create-new-project.png)

Pokud je vývojové prostředí sady Visual Studio již otevřeno, můžete vytvořit nový projekt výběrem možnosti **soubor** > **Nový** > **projekt** na panelu nabídek nebo kliknutím na tlačítko **Nový projekt** na panelu nástrojů.

![Tlačítko Nový projekt v aplikaci Visual Studio 2019](media/vs-2019/new-project-button.png)

## <a name="select-a-template-type"></a>Vybrat typ šablony

Na stránce **vytvořit nový projekt** se zobrazí seznam naposledy vybraných šablon na levé straně. Šablony jsou seřazené podle *posledního použití*.

Pokud nevyberete z naposledy použitých šablon, můžete filtrovat všechny dostupné šablony projektu podle **jazyka** (například C# nebo C++), **platformy** (například Windows nebo Azure), a **typu projektu** (například Desktop nebo Web). Můžete také zadat hledaný text do vyhledávacího pole, chcete-li dále filtrovat šablony, například **ASP.NET**.

![Filtry šablony projektu v aplikaci Visual Studio 2019](media/vs-2019/create-new-project-filters.png)

Značky, které se zobrazí pod každou šablonou, odpovídají třem filtrům rozevíracích seznamů (jazyk, platforma a typ projektu).

> [!TIP]
> Pokud nevidíte šablonu, kterou hledáte, možná nemáte k dispozici úlohu pro Visual Studio. Pokud chcete nainstalovat další úlohy, třeba vývoj pro **vývoj pro Azure** nebo **vývoj mobilních aplikací pomocí .NET**, klikněte na odkaz **instalovat další nástroje a funkce** a otevřete instalační program pro Visual Studio. Odtud vyberte úlohy, které chcete nainstalovat, a pak vyberte **Upravit**. Pak budou k dispozici další šablony projektů, ze kterých si můžete vybrat.
>
> ![Instalace dalších nástrojů a odkazů na funkce v aplikaci Visual Studio 2019](media/vs-2019/install-more-tools-features.png)

Vyberte šablonu a pak klikněte na **Další**.

## <a name="configure-your-project"></a>Konfigurace projektu

Stránka **Konfigurovat nový projekt** obsahuje možnosti pro pojmenování projektu (a řešení), výběr umístění na disku a výběr verze architektury (Pokud je k dispozici pro šablonu, kterou jste zvolili).

![Konfigurace nové stránky projektu v aplikaci Visual Studio 2019](media/vs-2019/configure-new-project.png)

> [!NOTE]
> Pokud vytvoříte nový projekt, když již máte projekt nebo řešení otevřené v aplikaci Visual Studio, je k dispozici další možnost konfigurace. Můžete zvolit vytvoření nového řešení nebo přidat nový projekt do již otevřeného řešení.
>
> ![Vytvořit nové řešení nebo přidat k existujícímu řešení v aplikaci Visual Studio 2019](media/vs-2019/configure-new-project-solution.png)

Kliknutím na **vytvořit** vytvořte nový projekt.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Přidání dalších projektů do řešení

Chcete-li do řešení přidat další projekt, klikněte pravým tlačítkem myši na uzel řešení v **Průzkumník řešení** a vyberte možnost **Přidat**  >  **Nový projekt**.

> [!TIP]
> Příklad projektu a řešení vytvořeného od začátku, dokončení s podrobnými pokyny a ukázkový kód naleznete v tématu [Úvod do projektů a řešení](../get-started/tutorial-projects-solutions.md).

## <a name="see-also"></a>Viz také

- [Práce s řešeními a projekty](creating-solutions-and-projects.md)
