---
title: Shromažďování trasovacích protokolů ETL pomocí nástroje PerfView
ms.date: 09/27/2019
ms.topic: conceptual
helpviewer_keywords:
- perfview
- ETL Trace
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 24d72e9630506ecc3d25fcc75e51eeb84f619e53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77271163"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Shromažďování trasovacích protokolů ETL pomocí nástroje PerfView

PerfView je nástroj, který vytváří ETL (protokol trasování událostí) soubory založené na [trasování událostí pro Windows,](/windows/desktop/ETW/event-tracing-portal) které mohou být užitečné při řešení některých druhů problémů s Visual Studio. V některých případě, když nahlásíte problém, produktový tým vás může požádat o spuštění perfview shromažďovat další informace.

## <a name="install-perfview"></a>Instalace perfview

Stáhnout PerfView z [GitHubu](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md).

## <a name="run-perfview"></a>Spustit perfview

1. Klikněte pravým tlačítkem myši na **perfView.exe** v Průzkumníkovi Windows a zvolte **Spustit jako správce** jako správce
1. V nabídce Shromáždit zvolte **Sbírat**
1. Zaškrtněte **políčko** **Zip**, Merge a **ThreadTime**.
1. Zvyšte **kruhový MB** na 1000.
1. Změna **aktuálního směrového adresáře** pro uložení trasování ETL do zadané složky a datového souboru, pokud budete shromažďovat více než jednou.
1. Chcete-li začít zaznamenávat data, zvolte tlačítko **Spustit shromažďování.**
1. Chcete-li zastavit nahrávání dat, zvolte tlačítko **Zastavit sběr.** Soubor PrefView.etl.zip bude uložen v zadaném adresáři.

PerfView můžete uložit pouze nejnovější data, která se vejde do jeho vyrovnávací paměti. Proto zkuste zastavit kolekci co nejdříve po Visual Studio začne zmrazit nebo zpomalit. Nesbírejte déle než 30 sekund po zasažení problému.

Další informace naleznete [v tématu PerfView Tutorial on Channel9](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).
