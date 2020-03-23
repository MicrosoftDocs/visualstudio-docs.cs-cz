---
title: Zvýšení výkonu, pokud je Visual Studio pomalé
titleSuffix: ''
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 6495e8506e12c0c5e5f878a23c609fe53a401bde
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596993"
---
# <a name="optimize-visual-studio-performance"></a>Optimalizace výkonu sady Visual Studio

Tento článek obsahuje některé návrhy vyzkoušet, pokud zjistíte, že Visual Studio běží pomalu. Můžete se také podívat na [tipy a triky pro výkon sady Visual Studio,](../ide/visual-studio-performance-tips-and-tricks.md) kde najdete další návrhy, jak zlepšit výkon.

## <a name="upgrade-visual-studio"></a>Upgrade Visual Studio

Pokud aktuálně používáte Visual Studio 2015, stáhněte si [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) nebo [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) zdarma a podívejte se na jeho vylepšený výkon. Řešení načítají dvakrát až třikrát rychleji než v sadě Visual Studio 2015, s vylepšením výkonu i v jiných oblastech. Visual Studio 2017 a Visual Studio 2019 jsou kompatibilní vedle sebe s Visual Studio 2015, takže tím, že to vyzkoušíte, nic neztratíte.

::: moniker range="vs-2017"

Pokud už používáte Visual Studio 2017, ujistěte se, že používáte verzi 15.6 nebo novější. Data ukazují, že řešení načítají až dvakrát nebo třikrát rychleji ve verzi 15.6. Stáhněte si ji [zde](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download).

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Rozšíření a okna nástrojů

Je možné, že máte nainstalovaná rozšíření, která zpomalují visual studio. Nápovědu ke správě rozšíření ke zlepšení výkonu najdete v [tématu Změna nastavení rozšíření za účelem zvýšení výkonu](../ide/optimize-visual-studio-startup-time.md#extensions).

Podobně můžete mít okna nástrojů, které zpomalují Visual Studio dolů. Nápovědu ke správě oken nástrojů naleznete v [tématu Změna nastavení okna nástroje za účelem zvýšení výkonu](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Hardware

Pokud uvažujete o upgradu hardwaru, má jednotka SSD větší vliv na výkon než další paměť RAM nebo rychlejší procesor.

Pokud přidáte SSD, pro optimální výkon nainstalujte systém Windows na tuto jednotku na rozdíl od pevného disku (HDD). Umístění jednotky řešení sady Visual Studio nezdá nezáleží tolik.

Navíc nespouštějte řešení z jednotky USB. Zkopírujte jej na pevný disk nebo SSD.

## <a name="help-us-improve"></a>Pomozte nám zlepšit

Vaše zpětná vazba nám pomáhá zlepšovat. Pomocí funkce **Nahlásit problém** můžete "zaznamenat" trasování a odeslat nám ji. Vyberte ikonu zpětné vazby vedle **položky Rychlé spuštění**nebo vyberte **možnost Odeslat** > **zpětnou vazbu** > **Nahlásit problém** z řádku nabídek. Další informace naleznete v [tématu Jak nahlásit problém s visual studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Viz také

- [Tipy a triky pro výkon](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog visual studia – rychlejší načítání řešení pomocí Visual Studia 2017 verze 15.6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
