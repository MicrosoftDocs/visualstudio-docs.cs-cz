---
title: Vytvoření nového projektu
ms.date: 03/19/2019
ms.topic: conceptual
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77a6a33a1dde4d779a56c9ee559ecfd3b20dfbfb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585467"
---
# <a name="create-a-new-project-in-visual-studio"></a>Vytvoření nového projektu v sadě Visual Studio

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Otevření dialogového okna Nový projekt

Existuje několik způsobů, jak vytvořit nový projekt v sadě Visual Studio 2017. Na úvodní stránce můžete zadat název šablony projektu do pole **Hledat šablony projektu** nebo zvolte odkaz Vytvořit nový **projekt** a otevřete dialogové okno **Nový projekt.** Kromě úvodní stránky můžete také na řádku nabídek zvolit **možnost Soubor** > **nového** > **projektu** nebo klepnout na tlačítko Nový **projekt** na panelu nástrojů.

![Úvodní stránka a projekt Nový > souboru > a soubor](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Výběr typu šablony

V dialogovém okně **Nový projekt** se dostupné šablony projektů zobrazí v seznamu v kategorii **Šablony.** Šablony jsou uspořádány podle programovacího jazyka a typu projektu, jako je Visual C#, JavaScript a Azure Data Lake.

![Dialogové okno Nový projekt](./media/vside-newproject-templates-list.png)

> [!NOTE]
> Seznam dostupných jazyků a šablon projektů, které se zobrazí, závisí na verzi sady Visual Studio, kterou používáte, a na nainstalovaných úlohách. Informace o instalaci dalších úloh najdete v [tématu Úprava sady Visual Studio přidáním nebo odebráním úloh a součástí](../install/modify-visual-studio.md).

Kliknutím na trojúhelník vedle názvu jazyka a výběrem kategorie projektu (například Plochy systému Windows) zobrazíte seznam šablon programovacího jazyka, který chcete použít.

Následující obrázek znázorňuje šablony projektu, které jsou k dispozici pro projekty Visual C# .NET Core:

![Šablony projektů](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Konfigurace projektu

Do pole **Název** zadejte název nového projektu. Projekt můžete uložit do výchozího umístění v počítači nebo klepnutím na tlačítko **Procházet** vyhledejte jiné umístění. Můžete také zvolit název řešení nebo přidat nový projekt do úložiště Git (výběrem **možnosti Přidat do správy zdrojového kódu).**

Chcete-li vytvořit řešení a projekt, klepněte na tlačítko **OK.**

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Otevření stránky Vytvořit nový projekt

Existuje několik způsobů, jak vytvořit nový projekt v sadě Visual Studio 2019. Při prvním otevření sady Visual Studio se zobrazí počáteční okno a odtud můžete zvolit **Vytvořit nový projekt**.

![Vytvoření nového projektu ze startovního okna ve VS 2019](media/vs-2019/start-window-create-new-project.png)

Pokud je vývojové prostředí sady Visual Studio již otevřené, můžete vytvořit nový projekt tak, že na panelu nabídek zvolíte Nový **New** > **projekt** **souboru** > nebo kliknete na tlačítko **Nový projekt** na panelu nástrojů.

![Tlačítko Nový projekt v Sadě Visual Studio 2019](media/vs-2019/new-project-button.png)

## <a name="select-a-template-type"></a>Výběr typu šablony

Na stránce **Vytvořit nový projekt** se vlevo zobrazí seznam naposledy vybraných šablon. Šablony jsou seřazeny podle *naposledy použitých šablon*.

Pokud nevybíráte z naposledy použitých šablon, můžete filtrovat všechny dostupné šablony projektů podle **jazyka** (například C# nebo C++), **platformy** (například Windows nebo Azure) a **typu projektu** (například Desktop nebo Web). Můžete také zadat hledaný text do vyhledávacího pole a dále filtrovat šablony, například **asp.net**.

![Filtry šablon projektu ve Visual Studiu 2019](media/vs-2019/create-new-project-filters.png)

Značky, které se zobrazují pod každou šablonou, odpovídají třem rozbalovacím filtrům (jazyk, platforma a typ projektu).

> [!TIP]
> Pokud nevidíte šablonu, kterou hledáte, může chybět zatížení pro Visual Studio. Chcete-li nainstalovat další úlohy, například **Vývoj Azure** nebo **Vývoj mobilních zařízení pomocí rozhraní .NET**, klikněte na odkaz **Instalovat další nástroje a funkce** a otevřete Instalační službu Sady Visual Studio. Odtud vyberte úlohy, které chcete nainstalovat, a pak zvolte **Změnit**. Poté budou k dispozici další šablony projektu, ze kterých si můžete vybrat.
>
> ![Instalace odkazu na další nástroje a funkce ve VS 2019](media/vs-2019/install-more-tools-features.png)

Vyberte šablonu a klepněte na tlačítko **Další**.

## <a name="configure-your-project"></a>Konfigurace projektu

Stránka **Konfigurovat nový projekt** obsahuje možnosti, jak pojmenovat projekt (a řešení), zvolit umístění disku a vybrat verzi rozhraní Framework (pokud je to relevantní pro vybranou šablonu).

![Konfigurace nové stránky projektu ve VS 2019](media/vs-2019/configure-new-project.png)

> [!NOTE]
> Pokud vytvoříte nový projekt, když již máte projekt nebo řešení otevřené v sadě Visual Studio, je k dispozici další možnost konfigurace. Můžete vytvořit nové řešení nebo přidat nový projekt do řešení, které je již otevřené.
>
> ![Vytvoření nového řešení nebo přidání do stávajícího řešení ve VS 2019](media/vs-2019/configure-new-project-solution.png)

Chcete-li vytvořit nový projekt, klepněte na **tlačítko Vytvořit.**

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Přidání dalších projektů do řešení

Pokud chcete do řešení přidat další projekt, klikněte pravým tlačítkem myši na uzel řešení v **Průzkumníku řešení** a zvolte **Přidat** > **nový projekt**.

## <a name="see-also"></a>Viz také

- [Vytváření řešení a projektů](creating-solutions-and-projects.md)
