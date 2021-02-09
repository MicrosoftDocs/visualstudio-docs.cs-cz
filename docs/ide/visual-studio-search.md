---
title: Použití vyhledávání sady Visual Studio
description: Naučte se používat Visual Studio Search k hledání nastavení, nabídek a kódu.
ms.date: 10/08/2020
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.QuickLaunch
- IDE navigator
ms.assetid: 3870a8fd-4afa-4f1e-a811-9fdf41a9e82d
monikerRange: vs-2019
author: profexorgeek
ms.author: jusjohns
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 101875b3a600a71c832498d05073187d2cf0b774
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873902"
---
# <a name="use-visual-studio-search"></a>Použití Visual Studio Search

Integrované vývojové prostředí (IDE) sady Visual Studio má mnoho nabídek, možností a funkcí, které mohou být obtížné pamatovat. Vyhledávací funkce sady Visual Studio je jediné vyhledávací pole, které vývojářům pomáhá najít nabídky a možnosti integrovaného vývojového prostředí a současně také vyhledat váš kód. Bez ohledu na to, zda jste novinkou v aplikaci Visual Studio nebo zkušený vývojář, tato funkce nabízí rychlý způsob vyhledávání napříč funkcemi IDE a vaším kódem.

Použijte klávesovou zkratku **CTRL** + **Q** pro přístup k vyhledávacímu poli nebo klikněte na vstupní pole pro vyhledávání v aplikaci Visual Studio, které se ve výchozím nastavení nachází vedle řádku nabídek:

:::image type="content" source="media/visual-studio-search-cropped.png" alt-text="Vyhledávací pole pro Visual Studio" lightbox="media/visual-studio-search.png":::

> [!NOTE]
> Příkaz provedený funkcí Search v aplikaci Visual Studio je `Window.QuickLaunch` a může se zobrazit tato funkce, na kterou se říká rychlé vyhledávání nebo snadné spuštění.

Na rozdíl od jiných vyhledávacích funkcí, jako je například Find in Files nebo Search Průzkumník řešení, hledání ve výsledcích sady Visual Studio zahrnuje funkce IDE, možnosti nabídky, názvy souborů a další. Následující části popisují různé typy výsledků, které hledání v aplikaci Visual Studio může najít.

## <a name="search-menus-options-and-windows"></a>Hledání v nabídkách, možnostech a oknech

K vyhledání nastavení, možností a podobných položek konfigurace můžete použít vyhledávací pole aplikace Visual Studio. Můžete například vyhledat *změnit motiv* a rychle najít a otevřít dialog, který umožňuje změnit barevný motiv sady Visual Studio, jak je znázorněno na následujícím snímku obrazovky:

:::image type="content" source="media/visual-studio-search-options.png" alt-text="Prohledat nastavení a možnosti sady Visual Studio":::

> [!TIP]
> Ve většině případů hledání v aplikaci Visual Studio vám také připomene nabídku, klávesové zkratky a umístění jednotlivých položek ve výsledcích.

Pomocí vyhledávacího pole aplikace Visual Studio můžete najít položky a příkazy nabídky. Pokud například chcete rychle najít a spustit příkaz vyčistit řešení, vyhledejte příkaz *vyčistit Sol* . Výsledky hledání také nabídnou připomenutí, kde najít tento příkaz v nabídkách, jak je znázorněno na následujícím snímku obrazovky:

:::image type="content" source="media/visual-studio-search-menu.png" alt-text="Hledání položek a příkazů nabídky sady Visual Studio":::

Nakonec můžete vyhledat okna nebo panely, které jste pravděpodobně omylem zavřeli. Vyhledejte například *test* a otevřete okno Průzkumník testů:

:::image type="content" source="media/visual-studio-search-window.png" alt-text="Hledání oken a panelů sady Visual Studio":::

## <a name="search-files-and-code"></a>Hledání souborů a kódu

Vyhledávání v aplikaci Visual Studio také hledá položky řešení pro název souboru, kód, metodu a další shody. Na následujícím snímku obrazovky hledání *Markdownu* našel soubor MarkdownMetaExtractor.cs, `MarkdownMetaExtractor` třídu a dvě metody v rámci řešení:

:::image type="content" source="media/visual-studio-search-files.png" alt-text="Hledání souborů pomocí Visual Studio Search":::

Můžete také provést hledání "ve stylu CamelCase případ". V následujícím snímku obrazovky hledání *FSS* našel soubor, třídu a metodu Canner v **jazyce F****starší verze** zařadit **s**:

:::image type="content" source="media/visual-studio-search-camel.png" alt-text="Ve stylu CamelCase Hump Search s využitím Visual studia Search":::

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](reference/visual-studio-commands.md)