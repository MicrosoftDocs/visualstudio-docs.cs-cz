---
title: Zvýšit výkon, pokud je Visual Studio pomalé
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596993"
---
# <a name="optimize-visual-studio-performance"></a>Optimalizace výkonu sady Visual Studio

Tento článek poskytuje některé návrhy, které můžete vyzkoušet, pokud zjistíte, že je aplikace Visual Studio spuštěná pomalu. Další informace o tom, jak zvýšit výkon, si můžete prohlédnout v tématu [tipy a tipy k výkonu sady Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md) .

## <a name="upgrade-visual-studio"></a>Upgrade sady Visual Studio

Pokud aktuálně používáte Visual Studio 2015, Stáhněte si [Visual studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) nebo [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) , abyste se mohli podívat na jeho Vylepšený výkon. Řešení se načítají dvakrát a třikrát rychleji než v aplikaci Visual Studio 2015 a vylepšení výkonu v jiných oblastech. Visual Studio 2017 a Visual Studio 2019 jsou souběžně kompatibilní se sadou Visual Studio 2015, takže nepřijdete o cokoli.

::: moniker range="vs-2017"

Pokud již používáte Visual Studio 2017, ujistěte se, že používáte verzi 15,6 nebo novější. Data ukazují, že řešení ve verzi 15,6 se rychleji načítají do dvou nebo třikrát. Stáhněte si ho [sem](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download).

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Okna rozšíření a nástrojů

Je možné, že máte nainstalovaná rozšíření, která zpomalují Visual Studio. Nápovědu ke správě rozšíření pro zlepšení výkonu najdete v tématu [Změna nastavení rozšíření za účelem zvýšení výkonu](../ide/optimize-visual-studio-startup-time.md#extensions).

Podobně můžete mít okna nástrojů, která zpomalují Visual Studio. Nápovědu ke správě oken nástrojů najdete v tématu [Změna nastavení okna nástrojů pro zlepšení výkonu](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Hardware

Pokud uvažujete o upgradu hardwaru, má jednotka SSD (Solid State Drive) více vliv na výkon než další paměť RAM nebo rychlejší procesor.

Pokud přidáte jednotku SSD, pro optimální výkon nainstalujte systém Windows na tuto jednotku na rozdíl od jednotky pevného disku (HDD). Místo na disku vašich řešení pro Visual Studio nezáleží na velikosti.

Kromě toho nespouštějte řešení z jednotky USB. Zkopírujte ho na pevný disk nebo SSD.

## <a name="help-us-improve"></a>Pomáhat nám zlepšovat

Vaše názory nám pomáhají zlepšit. Pomocí funkce **nahlásit problém** můžete zaznamenat trasování a odeslat ho do nás. Vyberte ikonu zpětné vazby vedle **Rychlé spuštění**nebo vyberte **help**  >  **poslat zpětnou vazbu**  >  **ohlásit problém** z řádku nabídek. Další informace najdete v tématu [postup nahlášení problému se sadou Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Viz také

- [Tipy a triky pro výkon](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog sady Visual Studio – nahrávání řešení rychleji pomocí sady Visual Studio 2017 verze 15,6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
