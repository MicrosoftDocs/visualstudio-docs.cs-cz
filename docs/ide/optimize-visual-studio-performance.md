---
title: Zlepšení výkonu při pomalém sady Visual Studio
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596993"
---
# <a name="optimize-visual-studio-performance"></a>Optimalizace výkonu sady Visual Studio

Tento článek obsahuje několik návrhů vyzkoušet, pokud zjistíte, že Visual Studio běží pomalu. Můžete taky využít podívat [a tipy k výkonu sady Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md) další návrhy na vylepšení výkonu.

## <a name="upgrade-visual-studio"></a>Upgrade sady Visual Studio

Pokud aktuálně používáte Visual Studio 2015, Stáhněte si [Visual studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) nebo [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) , abyste se mohli podívat na jeho Vylepšený výkon. Řešení se načítají dvakrát a třikrát rychleji než v aplikaci Visual Studio 2015 a vylepšení výkonu v jiných oblastech. Visual Studio 2017 a Visual Studio 2019 jsou souběžně kompatibilní se sadou Visual Studio 2015, takže nepřijdete o cokoli.

::: moniker range="vs-2017"

Pokud již používáte Visual Studio 2017, ujistěte se, že používáte verzi 15,6 nebo novější. Dat udávají, že řešení se načtení do dvakrát nebo třikrát rychlejší ve verzi 15.6. Stáhněte si ho [tady](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download).

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Rozšíření a okna nástrojů

Můžete mít nainstalovaná rozšíření, které snižují sady Visual Studio. Nápověda pro správu rozšíření kvůli zvýšení výkonu, naleznete v tématu [změnit nastavení rozšíření kvůli zvýšení výkonu](../ide/optimize-visual-studio-startup-time.md#extensions).

Podobně může mít okna nástrojů, které snižují sady Visual Studio. Nápovědu pro správu nástroje windows najdete v tématu [změnit nastavení okna nástroje pro zvýšení výkonu](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Hardware

Pokud uvažujete o hardwaru, jednotky SSD (Solid-State Drive) má další dopad na výkon než další paměť RAM nebo na rychlejší procesor.

Pokud chcete přidat SSD, pro zajištění optimálního výkonu instalaci Windows na této jednotce, na rozdíl od pevných discích (HDD). Umístění disku řešení sady Visual Studio nefunguje co nejvíce záleží.

Kromě toho nespouštějte řešení z USB Flash disk. Zkopírujte ho do pevný disk nebo SSD.

## <a name="help-us-improve"></a>Pomozte nám zlepšovat kvalitu

Vaše zpětná vazba pomůže nám se zdokonalovat. Použití **nahlásit problém** funkci pro trasování "záznam" a odeslat společnosti Microsoft. Vyberte ikonu zpětné vazby vedle **rychlé spuštění**, nebo vyberte **pomáhají** > **odeslat zpětnou vazbu** > **nahlásit problém** z řádku nabídek. Další informace najdete v tématu [postup nahlášení problému se sadou Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Viz také:

- [Tipy ke zvýšení výkonu a triky](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog Visual Studio – zátěžové řešení rychleji s využitím sady Visual Studio 2017 verze 15.6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
