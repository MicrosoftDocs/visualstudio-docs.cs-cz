---
title: Blend pro Visual Studio prohlídka funkcí
titleSuffix: ''
ms.date: 07/31/2019
ms.topic: overview
f1_keywords:
- Blend.Start.Dev12
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8348ba38849b76a745a56f941850d6b61a8f433f
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332088"
---
# <a name="blend-for-visual-studio-overview"></a>Přehled Blend pro Visual Studio

Blend pro Visual Studio vám pomůže navrhovat okna a webové aplikace založené na jazyce XAML. Poskytuje stejné základní prostředí pro návrh XAML jako Visual Studio a přidává vizuální návrháře pro pokročilé úlohy, jako jsou například animace a chování. Porovnání mezi Blendem a sady Visual Studio naleznete v tématu [design XAML v aplikaci Visual Studio a Blend pro Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md).

Blend pro Visual Studio je součástí sady Visual Studio. Chcete-li nainstalovat Blend, v **instalační program pro Visual Studio** vyberte buď úlohu **vývoj Univerzální platforma Windows** nebo vývoj **desktopových aplikací .NET** . Obě tyto úlohy zahrnují komponentu Blend pro Visual Studio.

![Komponenty úlohy UWP](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Součásti úlohy vývoj desktopových aplikací .NET](media/installer-dotnet-desktop.png)

Pokud s Blend pro Visual Studio začínáte, měli byste se seznámit s jedinečnými funkcemi pracovního prostoru. Toto téma vás provede rychlou prohlídku.

## <a name="tools-panel"></a>Panel Nástroje

Pomocí panelu **nástroje** v Blend pro Visual Studio můžete vytvářet a upravovat objekty v aplikaci. Panel **nástroje** se zobrazí na levé straně návrháře XAML, když máte soubor *. XAML* otevřený.

Objekty vytvoříte tak, že vyberete nástroj a nakreslíte na návrhovou plochu pomocí myši.

![Panel nástrojů v Blend pro Visual Studio](media/blend-tools-panel.png)

> [!TIP]
> Některé nástroje na panelu **nástroje** mají variace, například místo obdélníku, můžete zvolit elipsu nebo čáru. Chcete-li získat přístup k těmto variantám, klikněte na něj pravým tlačítkem nebo klikněte a podržte ho.
>
> ![Variace nástroj Obrazec v Blend pro Visual Studio](media/blend-rectangle-tool-variations.png)

### <a name="selection-tools"></a>Nástroje pro výběr

Vyberte možnost objekty a cesty. Pomocí nástroje **přímý výběr** vyberte vnořené objekty a segmenty cest.

### <a name="view-tools"></a>Zobrazit nástroje

Upravte zobrazení návrhové plochy, například pro posouvání a zvětšování.

### <a name="brush-tools"></a>Nástroje štětce

Pracujte s vizuálními atributy objektu, jako je například transformace štětce nebo použití přechodu.

### <a name="object-tools"></a>Nástroje objektů

Nakreslete nejběžnější objekty na návrhové ploše, například cesty, tvary, panely rozložení, text a ovládací prvky.

### <a name="asset-tools"></a>Nástroje assetu

Přejděte do okna assets (prostředky) a zobrazte naposledy použitý prostředek z knihovny.

## <a name="assets-window"></a>Okno prostředků

Okno **assets (prostředky** ) obsahuje všechny dostupné ovládací prvky a je podobné jako **Sada nástrojů v sadě** Visual Studio. Kromě ovládacích prvků najdete vše, co můžete přidat na návrhovou plochu v okně **assety** , včetně stylů, médií, chování a efektů. Chcete-li otevřít okno **assety** , zvolte možnost **Zobrazit**  >  **okno assety** nebo stiskněte klávesovou **zkratku CTRL** + **+** + **X**.

![Okno prostředků v Blend pro Visual Studio](media/blend-assets-window.png)

- Zadáním textu do pole **Hledat prostředky** můžete filtrovat seznam assetů.
- Přepínání mezi zobrazením mřížky a režimu seznamu v zobrazení assetů pomocí tlačítek v pravém horním rohu.

## <a name="objects-and-timeline-window"></a>Objekty a časová osa okno

Toto okno slouží k uspořádání objektů na návrhové ploše a v případě, že je chcete animovat. Chcete-li otevřít okno **objekty a časová osa** , vyberte možnost **Zobrazit**  >  **osnovu dokumentu**. Kromě funkcí, které jsou k dispozici v [okně Osnova dokumentu](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window) v aplikaci Visual Studio, má okno Objekty a časová osa v Blend pro Visual Studio oblast kompozice časové osy na pravé straně. Použijte časovou osu při vytváření a úpravách animací.

![Okno objekt a časová osa v režimu animace](media/storyboard-timeline.png)

Použití tlačítek souvisejících se scénářem ![Tlačítka scénáře v Blend pro Visual Studio](media/storyboard-buttons.png) k vytvoření, odstranění, zavření nebo výběru scénáře. Pomocí oblasti kompozice časové osy napravo můžete zobrazit časovou osu a přesunout klíčové snímky.

Pokud se chcete dozvědět víc o dostupných funkcích, najeďte myší na jednotlivá tlačítka v okně.

## <a name="see-also"></a>Viz také

- [Animace objektů](../xaml-tools/animate-objects-in-xaml-designer.md)
- [Kreslení tvarů a cest](../xaml-tools/draw-shapes-and-paths.md)
- [Návrh XAML v sadě Visual Studio a Blend pro Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md)
