---
title: Filtr zobrazení sestavy výkonu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9a5642a8e153a4dfc7705d91d933397b6f8acb37
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778451"
---
# <a name="performance-report-view-filter"></a>Filtr zobrazení sestav výkonu
Okno **Filtr zobrazení sestavy profileru** se nachází v horní části okna Sestava **výkonu.** Pokud ji nevidíte, klepněte na tlačítko **Zobrazit filtr.**

 Každou klauzuli filtru můžete upravit a upřesnit tak výsledky. Následující sloupce jsou k dispozici v nástroji pro tvorbu filtrů.

|Položka filtru|Popis|
|-----------------|-----------------|
|Nebo|Zvolte **A** pokud tato klauzule a další klauzule musí být pravdivé, aby odpovídaly výsledku. Zvolte **Nebo** pokud tato klauzule nebo další klauzule může být true tak, aby odpovídala výsledku.|
|Pole|Vyberte pole, které chcete použít v klauzuli filtru, ze seznamu datových polí, která jsou k dispozici v aktuálním souboru sestavy.|
|Operátor|Zvolte operátor, který určuje požadovaný vztah mezi polem a hodnotou.<br /><br /> = Rovná se<br /><br /> <>  není rovnoprávně<br /><br /> < méně než<br /><br /> > větší než<br /><br /> <= menší nebo rovno<br /><br /> >= větší nebo rovno|
|Hodnota|Vyberte nebo zadejte hodnotu, kterou chcete vyhledat. V některých polích jsou uvedeny dostupné hodnoty pro pole.|

 Můžete přidat klauzule filtru, dokud nebudete mít pocit, že filtr vám poskytne nejlepší výsledky. Kliknutím na **Spustit filtr** aplikujte filtr na datový soubor.

 V zobrazení sestavy **Značky** můžete vygenerovat klauzule filtru, které omezí data v zobrazení sestavy na data shromážděná mezi dvěma značkami. Vyberte značky, které chcete začínat a končit data sestavy, pak klepněte pravým tlačítkem myši a vyberte **buď Přidat filtr na značky** nebo Přidat filtr na **časová razítka**. Oba filtry omezují data v aktuálním datovém souboru na stejné rozpětí; **Přidat filtr na značky** lze použít na jiné soubory VSP.

 Chcete-li filtr uložit, klepněte na panelu nástrojů **Zprávy o výkonu** na **položku Exportovat filtr** a zadejte umístění a název souboru . *vspf.* Chcete-li načíst dříve uložený filtr, klepněte na **tlačítko Importovat filtr** a vyhledejte uložený soubor filtru. Soubory filtrů lze také použít k filtrování datových souborů v počítačích, ve kterých jsou nainstalovány samostatné nástroje pro profilování. Další informace naleznete [v tématu VSPerfReport](../profiling/vsperfreport.md).

## <a name="see-also"></a>Viz také
- [Analýza dat nástrojů pro měření výkonu](../profiling/analyzing-performance-tools-data.md)
- [VSPerfReport](../profiling/vsperfreport.md)
