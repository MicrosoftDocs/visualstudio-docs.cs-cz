---
description: PerfView je nástroj, který vytváří soubory ETL (protokol trasování událostí) založené na trasování událostí pro Windows), které může být užitečné při řešení problémů s některými druhy problémů se sadou Visual Studio.
title: Shromažďování trasovacích protokolů ETL pomocí nástroje PerfView
ms.date: 09/27/2019
ms.topic: how-to
helpviewer_keywords:
- perfview
- ETL Trace
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 81cf6469a14fb3559d37056ba5193d9018ccc1c8
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221064"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Shromažďování trasovacích protokolů ETL pomocí nástroje PerfView

PerfView je nástroj, který vytváří soubory ETL (protokol trasování událostí) založené na [trasování událostí pro Windows](/windows/desktop/ETW/event-tracing-portal) , které může být užitečné při řešení potíží s některými druhy problémů se sadou Visual Studio. Při nahlášení problému občas může produktový tým požádat o spuštění PerfView ke shromažďování dalších informací.

## <a name="install-perfview"></a>Nainstalovat PerfView

Stáhněte si PerfView z [GitHubu](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md).

## <a name="run-perfview"></a>Spustit PerfView

1. V Průzkumníku Windows klikněte pravým tlačítkem na **PerfView.exe** a jako správce vyberte **Spustit jako správce** .
1. V nabídce shromáždit klikněte na možnost **shromáždit** .
1. Podívejte se na **zip**, **Merge** a **ThreadTime**.
1. Zvyšte **kruhové MB** na 1000.
1. Změna **aktuálního adresáře** pro uložení trasování ETL do zadané složky a datového souboru, pokud se chystáte shromažďovat více než jednou.
1. Chcete-li spustit zaznamenávání dat, klikněte na tlačítko **Spustit shromažďování** .
1. Chcete-li zastavit zaznamenávání dat, klikněte na tlačítko **Zastavit shromažďování** . Soubor PrefView.etl.zip bude uložen v zadaném adresáři.

PerfView může ukládat pouze nejnovější data, která se vejdou do vyrovnávací paměti. Proto se pokuste zastavit shromažďování co nejdříve po zahájení zablokování nebo zpomalení sady Visual Studio. Neshromažďovat po dobu delší než 30 sekund, než se narazí na problém.

Další informace najdete v tématu [kurz PerfView na channel9](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).
