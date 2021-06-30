---
title: Další informace o Průzkumník řešení nástroje
description: Zjistěte, jak můžete pomocí Průzkumník řešení nástrojů v Visual Studio vytvořit a & spravovat soubory, projekty a řešení.
ms.date: 06/29/2021
ms.topic: conceptual
helpviewer_keywords:
- solution explorer [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8360f553dc913164d302ef03a0a32626f83a51c2
ms.sourcegitcommit: 7393a37ce77c5b80312ce787baa060c91d41d959
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2021
ms.locfileid: "113114782"
---
# <a name="how-to-use-solution-explorer"></a>Jak používat Průzkumník řešení

Okno nástroje Průzkumník řešení můžete použít k vytvoření a & řešení a projektů a k zobrazení & s vaším kódem. V tomto článku podrobně popisujeme možnosti uživatelského rozhraní, které vám s tím pomůžou.

> [!NOTE]
> Toto téma se týká pouze Visual Studio ve Windows.

## <a name="solution-explorer-tool-window"></a>Průzkumník řešení nástroje

Začneme tím, že se podíváme na okno nástroje Průzkumník řešení v integrovaném vývojovém Visual Studio [(IDE)](../get-started/visual-studio-ide.md)jazyka Visual Studio otevřeném řešení konzoly jazyka C#, které má dva projekty.

[![V Průzkumník řešení se zobrazí okno Visual Studio.](media/solution-explorer-tool-window.png)](media/solution-explorer-tool-window.png#lightbox)

Okno nástroje obsahuje následující prvky uživatelského rozhraní (uživatelské rozhraní):

- **Řádek nabídek**, kde můžete řídit, jak se budou soubory zobrazovat
- **Panel hledání**, kde můžete hledat konkrétní soubory a typy souborů
- **Hlavní okno**, kde můžete zobrazit a spravovat soubory, projekty a & řešení
- **Uzel řešení**, kde můžete spravovat řešení
- **Uzel projektu**, kde můžete spravovat své projekty
- **Uzel Závislosti,** kde můžete spravovat řešení a & projektu.
- **Uzel programu**, kde můžete zobrazit, upravit a spravovat program nebo aplikaci (aplikaci)
- **[Karta změn Gitu,](../version-control/git-with-visual-studio.md?view=vs-2019&preserve-view=true#git-changes-window)** kde můžete pomocí Gitu & GitHubu v rámci Visual Studio spolupracovat na projektech s týmem

> [!TIP]
> Pokud okno nástroje Průzkumník řešení nevidíte, můžete ho otevřít z řádku nabídek Visual Studio pomocí zobrazení Průzkumník řešení nebo stisknutím  >   **kláves Ctrl** + **Alt** + **L**.

## <a name="solution-explorer-menu-bar"></a>Průzkumník řešení řádku nabídek

Pokračujte tím, že se blíže podíváme na Průzkumník řešení řádku nabídek.

[Panel Průzkumník řešení v nabídce Visual Studio.](media/solution-explorer-menu-bar.png)

Řádek nabídek obsahuje následující prvky uživatelského rozhraní zleva doprava:

- **Tlačítko** Zpět pro přepínání mezi výsledky hledání
- **Tlačítko Forward** (Přeposlání) pro přepínání mezi výsledky hledání
- **Tlačítko** Domů, které se vrátí do výchozího zobrazení
- **Přepnutí** tlačítka pro přepínání mezi řešeními a dostupnými zobrazeními
- **Tlačítko Filtru čekajících** změn & rozevírací nabídku pro zobrazení otevřených souborů nebo souborů s čekajícími změnami
- **Tlačítko Synchronizovat s aktivním** dokumentem pro vyhledání souboru v editoru kódu
- **Tlačítko** Aktualizovat, které se zobrazí pouze při výběru závislosti, jako je například funkce nebo balíček
- **Sbalení** tlačítka All (Sbalit vše) pro sbalení zobrazení souboru v hlavním okně
- **Tlačítko Zobrazit všechny** soubory pro zobrazení všech souborů, včetně [uvolněných projektů](filtered-solutions.md#toggle-unloaded-project-visibility)
- **Tlačítko** Vlastnosti pro zobrazení a změnu nastavení konkrétních souborů a komponent
- **Tlačítko Náhled vybraných** položek pro zobrazení vybraného souboru nebo komponenty v editoru kódu

### <a name="solution-explorer-right-click-context-menu"></a>Průzkumník řešení místní nabídku po kliknutí pravým tlačítkem myši

V Průzkumník řešení existuje několik vlastností souboru, se kterými můžete pracovat pomocí místní nabídky po kliknutí pravým tlačítkem myši. Další informace o možnostech místní nabídky po kliknutí pravým tlačítkem najdete na stránce Správa [vlastností](managing-project-and-solution-properties.md) projektu a řešení.

## <a name="see-also"></a>Viz také

- [Co jsou řešení a projekty v Visual Studio?](solutions-and-projects-in-visual-studio.md)
- [Přizpůsobení rozložení oken v Visual Studio](customizing-window-layouts-in-visual-studio.md)
