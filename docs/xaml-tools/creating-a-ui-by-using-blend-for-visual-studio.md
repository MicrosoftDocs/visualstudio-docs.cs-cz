---
title: Blend pro Visual Studio prohlídka funkcí
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593006"
---
# <a name="blend-for-visual-studio-overview"></a>Přehled Blend pro Visual Studio

Blend for Visual Studio vám pomůže návrhu na základě XAML Windows a webových aplikací. Nabízí stejné základní XAML návrhové prostředí jako sady Visual Studio a přidá vizuální návrhářské nástroje pro pokročilé úlohy, jako je například animace a chování. Porovnání mezi Blendem a sadou Visual Studio najdete v tématu [návrh XAML v sadě Visual Studio a nástroje Blend for Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md).

Blend for Visual Studio je součástí sady Visual Studio. Instalace v programu Blend, **instalační program sady Visual Studio** zvolit buď **vývoj pro univerzální platformu Windows** nebo **vývoj desktopových aplikací .NET** pracovního vytížení. Obě tyto úlohy zahrnují Blend pro komponentu sady Visual Studio.

![Součásti UPW pracovního vytížení](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Součásti úlohy vývoj desktopových aplikací .NET](media/installer-dotnet-desktop.png)

Pokud začínáte blendu pro Visual Studio, věnujte chvíli seznámení s jedinečné funkce pracovního prostoru. Toto téma přejdete na stručný přehled.

## <a name="tools-panel"></a>Panel Nástroje

Můžete použít **nástroje** panelu v Blendu pro Visual Studio k vytvoření a úprava objektů ve vaší aplikaci. Panel **nástroje** se zobrazí na levé straně návrháře XAML, když máte soubor *. XAML* otevřený.

Vytvoření objektů výběrem nástroj a vykreslení na návrhovou plochu pomocí myši.

![Panel nástrojů v Blend pro Visual Studio](media/blend-tools-panel.png)

> [!TIP]
> Některé nástroje na panelu **nástroje** mají variace, například místo obdélníku, můžete zvolit elipsu nebo čáru. Chcete-li získat přístup k těmto variantám, klikněte na něj pravým tlačítkem nebo klikněte a podržte ho.
>
> ![Variace nástroj Obrazec v Blend pro Visual Studio](media/blend-rectangle-tool-variations.png)

### <a name="selection-tools"></a>Nástroje pro výběr

Vyberte možnost objekty a cesty. Použití **přímý výběr** nástroj pro výběr vnořené objekty a segmenty cesty.

### <a name="view-tools"></a>Zobrazení nástroje

Upravte zobrazení návrhové plochy, například pro posouvání a zvětšování.

### <a name="brush-tools"></a>Štětec

Pracujte s vizuálními atributy objektu, jako je například transformace štětce nebo použití přechodu.

### <a name="object-tools"></a>Objekt nástroje

Nakreslete nejběžnější objekty na návrhové ploše, například cesty, tvary, panely rozložení, text a ovládací prvky.

### <a name="asset-tools"></a>Nástroje pro prostředek

Přejděte do okna assets (prostředky) a zobrazte naposledy použitý prostředek z knihovny.

## <a name="assets-window"></a>Okno prostředků

Okno **assets (prostředky** ) obsahuje všechny dostupné ovládací prvky a je podobné jako **Sada nástrojů v sadě** Visual Studio. Kromě ovládacích prvků najdete vše, co můžete přidat na návrhovou plochu v okně **assety** , včetně stylů, médií, chování a efektů. Chcete-li otevřít okno **assety** , zvolte možnost **Zobrazit** > **assets Window** nebo stiskněte klávesu **CTRL**+**ALT**+**X**.

![Okno prostředků v Blend pro Visual Studio](media/blend-assets-window.png)

- Zadáním textu do pole **Hledat prostředky** můžete filtrovat seznam assetů.
- Přepínání mezi zobrazením mřížky a režimu seznamu v zobrazení assetů pomocí tlačítek v pravém horním rohu.

## <a name="objects-and-timeline-window"></a>Objekty a časová osa okno

Toto okno slouží k uspořádání objektů na návrhové ploše a v případě, že je chcete animovat. Chcete-li otevřít okno **objekty a časová osa** , vyberte možnost **Zobrazit** > **Osnova dokumentu**. Kromě funkcí, které jsou k dispozici v [okně Osnova dokumentu](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window) v aplikaci Visual Studio, má okno Objekty a časová osa v Blend pro Visual Studio oblast kompozice časové osy na pravé straně. Použijte časovou osu při vytváření a úpravách animací.

![Okno objekt a časová osa v režimu animace](media/storyboard-timeline.png)

Použití tlačítek souvisejících se scénářem ![Tlačítka scénáře v Blend pro Visual Studio](media/storyboard-buttons.png) k vytvoření, odstranění, zavření nebo výběru scénáře. Pomocí oblasti kompozice časové osy napravo můžete zobrazit časovou osu a přesunout klíčové snímky.

Pokud se chcete dozvědět víc o dostupných funkcích, najeďte myší na jednotlivá tlačítka v okně.

## <a name="see-also"></a>Viz také:

- [Animace objektů](../xaml-tools/animate-objects-in-xaml-designer.md)
- [Kreslení tvarů a cest](../xaml-tools/draw-shapes-and-paths.md)
- [Návrh XAML v sadě Visual Studio a Blend pro Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md)
