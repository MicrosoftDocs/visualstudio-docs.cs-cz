---
title: Prohlížeč událostí | Microsoft Docs
ms.date: 4/30/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, Events Viewer
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 0be00f2333a2e732d9ba4472004c383b132c0bf2
ms.sourcegitcommit: 14637be49401f56341c93043eab560a4ff6b57f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075062"
---
# <a name="events-viewer"></a>Prohlížeč událostí

Prohlížeč obecných událostí zobrazuje aktivitu aplikace pomocí seznamu událostí, jako je zatížení modulu, spuštění vlákna a konfigurace systému. Toto zobrazení vám pomůže lépe diagnostikovat, jak vaše aplikace funguje v profileru sady Visual Studio.

## <a name="setup"></a>Nastavení

1. Kliknutím na **ALT + F2** otevřete Profiler výkonu v aplikaci Visual Studio.

1. Zaškrtněte políčko **Prohlížeč událostí** .

   ![Zaškrtnuté políčko Prohlížeč událostí](../profiling/media/eventsviewerselected.png "Zaškrtnuté políčko Prohlížeč událostí")

1. Kliknutím na tlačítko **Spustit** nástroj spustíte.

1. Po spuštění nástroje si Projděte scénář pro profilaci ve vaší aplikaci. Pak vyberte **Zastavit shromažďování** nebo zavřít aplikaci, aby se zobrazila vaše data.

   ![Okno, v němž je zastaveno shromažďování](../profiling/media/stopcollectioneventsviewer.png "Okno, v němž je zastaveno shromažďování")

Další informace o tom, jak nástroj zvýšit efektivitu, najdete v tématu [optimalizace nastavení profilace](../profiling/optimize-profiler-settings.md).

## <a name="understand-your-data"></a>Pochopení vašich dat

![Trasování prohlížeče událostí](../profiling/media/eventviewertrace.png "Trasování prohlížeče událostí")

|Název sloupce|Popis|
|----------|---------------------|
|Název zprostředkovatele|Zdroj události|
|Název události|Událost zadaná poskytovatelem|
|Text|Popisy zprostředkovatele, názvu události a ID události|
|Časové razítko (MS)|Čas, kdy došlo k události|
|Identifikátor GUID zprostředkovatele|ID zprostředkovatele událostí|
|ID události|ID události|
|ID procesu|Proces, ze kterého došlo k události (Pokud je známý)|
|Název procesu|Název procesu, pokud je aktivně spuštěn|
|ID vlákna|ID vlákna, ze kterého došlo k události (Pokud je známá)|

Pokud ve výchozím nastavení chybí libovolný sloupec, klikněte pravým tlačítkem na jedno z existujících záhlaví sloupců a vyberte sloupec, který chcete přidat.

![Přidání sloupců do prohlížeče událostí](../profiling/media/eventvieweraddcolumns.png "Přidání sloupců do prohlížeče událostí")

Po výběru události se zobrazí okno **Další vlastnosti** . **Společné vlastnosti** zobrazují seznam vlastností, které se zobrazí pro libovolnou událost. **Vlastnosti datové části** zobrazují vlastnosti specifické pro událost. U některých událostí můžete také zobrazit **zásobníky**.

![Prohlížeč událostí zobrazující zásobníky](../profiling/media/eventviewerstacks.png "Prohlížeč událostí zobrazující zásobníky")

## <a name="organize-your-data"></a>Uspořádání dat

Všechny sloupce s výjimkou **textového** sloupce jsou seřaditelné.

![Trasování prohlížeče událostí](../profiling/media/eventviewertrace.png "Trasování prohlížeče událostí")

V prohlížeči událostí se zobrazí až 20 000 událostí v daném okamžiku. Pokud se chcete zaměřit na události, které vás zajímají, můžete filtrovat zobrazení událostí tak, že vyberete filtr událostí. Můžete také zjistit, jaké procento celkového počtu událostí u každého poskytovatele proběhlo. Když najedete myší na jeden filtr událostí, zobrazí se popisek s popisem:

- Název události
- Poskytovatel
- Identifikátor GUID
- Procento z celkového počtu událostí
- Počet událostí

![Filtr událostí prohlížeče událostí](../profiling/media/eventviewereventfilter.png "Filtr událostí prohlížeče událostí")

Filtr poskytovatele zobrazuje procento celkového počtu událostí, ke kterým došlo u každého poskytovatele. Najeďte myší na jednoho poskytovatele, aby se zobrazil podobný popis s názvem poskytovatele, procentem celkového počtu událostí a počtem událostí.

![Filtr poskytovatele prohlížeče událostí](../profiling/media/eventviewerproviderfilter.png "Filtr poskytovatele prohlížeče událostí")
