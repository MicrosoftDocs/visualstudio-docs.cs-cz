---
title: Blend pro prohlídku funkce visual studia
titleSuffix: ''
ms.date: 07/31/2019
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2b9f38d83befcf49ecd3de8da3a2cd26ff3ab46
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301669"
---
# <a name="blend-for-visual-studio-overview"></a>Přehled prolnutí pro Visual Studio

Blend pro Visual Studio vám pomůže navrhnout Windows a webové aplikace založené na XAML. Poskytuje stejné základní prostředí návrhu XAML jako Visual Studio a přidává vizuální návrháře pro pokročilé úkoly, jako jsou animace a chování. Porovnání mezi blenda Visual Studio, najdete [v tématu Návrh XAML v sadě Visual Studio a Blend pro Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md).

Blend pro Visual Studio je součástí sady Visual Studio. Chcete-li nainstalovat blend, v **Instalační službě sady Visual Studio** zvolte vývoj univerzální **platformy Windows** nebo **úlohu vývoje plochy .NET.** Obě tyto úlohy zahrnují komponentu Blend for Visual Studio.

![Součásti pracovního vytížení UPW](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Součásti úloh y pro vývoj stolních počítačů .NET](media/installer-dotnet-desktop.png)

Pokud s blendem pro Visual Studio tečte, věnujte chvíli tomu, abyste se seznámili s jedinečnými funkcemi pracovního prostoru. Toto téma vás zavede na rychlou prohlídku.

## <a name="tools-panel"></a>Panel Nástroje

Panel **nástrojů** v sadě pro Visual Studio můžete použít k vytváření a úpravám objektů v aplikaci. **Panel nástrojů** se zobrazí na levé straně návrháře XAML, když máte otevřený soubor *XAML.*

Objekty vytvoříte výběrem nástroje a kreslením na kreslicí prkno myší.

![Panel nástrojů v prolnutí pro Visual Studio](media/blend-tools-panel.png)

> [!TIP]
> Některé nástroje v panelu **nástrojů** mají například varianty, například místo obdélníku můžete zvolit elipsu nebo čáru. Chcete-li získat přístup k těmto variantám, klepněte na nástroj pravým tlačítkem nebo klepněte a podržte ho.
>
> ![Variace nástrojů tvarů v prolnutí pro Visual Studio](media/blend-rectangle-tool-variations.png)

### <a name="selection-tools"></a>Nástroje pro výběr

Vyberte objekty a cesty. Nástrojem **pro přímý výběr** vyberte vnořené objekty a segmenty cesty.

### <a name="view-tools"></a>Zobrazit nástroje

Upravte zobrazení kreslicí plochy, například pro posouvání a zvětšování.

### <a name="brush-tools"></a>Nástroje pro štětec

Pracujte s vizuálními atributy objektu, jako je transformace stopy nebo aplikování přechodu.

### <a name="object-tools"></a>Nástroje pro objekty

Nakreslete nejběžnější objekty na kreslicí stěně, jako jsou cesty, tvary, panely rozvržení, text a ovládací prvky.

### <a name="asset-tools"></a>Nástroje pro podklady

Přístup k oknu Datové zdroje a zobrazte naposledy použitý datový zdroj z knihovny.

## <a name="assets-window"></a>Okno Datový majetek

Okno **Prostředky** obsahuje všechny dostupné ovládací prvky a je podobné **panelu nástrojů** v sadě Visual Studio. Kromě ovládacích prvků najdete v okně **Datové zdroje** vše, co můžete přidat do kreslicí plochy, včetně stylů, médií, chování a efektů. Chcete-li otevřít okno **Datové zdroje,** zvolte **Zobrazit** > **datové zdroje** nebo stiskněte **ctrl**+**alt**+**x**.

![Okno Datové zdroje v prolnutí pro Visual Studio](media/blend-assets-window.png)

- Zadáním textu do pole **Hledat datové zdroje** můžete filtrovat seznam datových zdrojů.
- Přepínejte mezi režimem mřížky a zobrazením zobrazení datového zdroje v režimu seznamu pomocí tlačítek vpravo nahoře.

## <a name="objects-and-timeline-window"></a>Okno Objekty a časová osa

Toto okno slouží k uspořádání objektů na kreslicí desce a v případě, že je chcete animovat. Chcete-li otevřít okno **Objekty a Časová osa,** zvolte **Zobrazit** > **obrys dokumentu**. Kromě funkcí poskytovaných v [okně Osnova dokumentu](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window) v sadě Visual Studio má okno Objekty a časová osa v prolnutí pro Visual Studio oblast kompozice časové osy vpravo. Při vytváření a úpravách animací použijte časovou osu.

![Okno Objekt a časová osa v režimu animace](media/storyboard-timeline.png)

Použití tlačítek souvisejících se scénářem ![Tlačítka scénáře v prolnutí pro Visual Studio](media/storyboard-buttons.png) chcete-li vytvořit, odstranit, zavřít nebo vybrat scénář. Pomocí oblasti kompozice časové osy vpravo zobrazte časovou osu a přesuňte klíčové snímky.

Najeďte nad každé tlačítko v okně, abyste se dozvěděli další informace o dostupných funkcích.

## <a name="see-also"></a>Viz také

- [Animace objektů](../xaml-tools/animate-objects-in-xaml-designer.md)
- [Kreslení tvarů a cest](../xaml-tools/draw-shapes-and-paths.md)
- [Návrh XAML v sadě Visual Studio a Blend pro Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md)
