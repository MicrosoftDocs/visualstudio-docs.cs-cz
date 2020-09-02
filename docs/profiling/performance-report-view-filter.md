---
title: Filtr zobrazení sestav výkonu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778451"
---
# <a name="performance-report-view-filter"></a>Filtr zobrazení sestav výkonu
Okno **filtru zobrazení sestav profileru** se nachází v horní části okna **sestavy výkonu** . Pokud ho nevidíte, klikněte na tlačítko **Zobrazit filtr** .

 Pro upřesnění výsledků můžete upravit každou klauzuli filtru. V Tvůrci filtru jsou k dispozici následující sloupce.

|Filtrovat položku|Popis|
|-----------------|-----------------|
|A/nebo|Vyberte **a** Pokud má tato klauzule a další klauzule hodnotu true, aby odpovídaly výsledku. Vyberte **nebo** Pokud má tato klauzule nebo další klauzule hodnotu true, aby odpovídaly výsledku.|
|Pole|Vyberte pole, které chcete použít v klauzuli Filter, ze seznamu datových polí, která jsou k dispozici v aktuálním souboru sestavy.|
|Operátor|Vyberte operátor, který určuje vztah, který chcete mezi polem a hodnotou.<br /><br /> = Equals<br /><br /> <>  se nerovná<br /><br /> < menší než<br /><br /> > větší než<br /><br /> <= menší než nebo rovno<br /><br /> >= větší než nebo rovno|
|Hodnota|Vyberte nebo zadejte hodnotu, která se má hledat. Některá pole uvádějí dostupné hodnoty pro pole.|

 Klauzule filtru můžete přidat, dokud nebudete mít pocit, že vám filtr poskytne nejlepší výsledky. Kliknutím na **Spustit filtr** použijete filtr pro datový soubor.

 Ze zobrazení **značek značky** můžete generovat klauzule filtru k omezení dat v zobrazeních sestavy na data, která jsou shromažďována mezi dvěma značkami. Vyberte značky, které chcete spustit a ukončit data sestavy, potom klikněte pravým tlačítkem myši a vyberte možnost **Přidat filtr do značek** nebo **Přidat filtr na časová razítka**. Oba filtry omezují data v aktuálním datovém souboru do stejného rozsahu. **Přidání filtru do značek** lze použít pro jiné soubory. vsp.

 Filtr uložíte tak, že kliknete na tlačítko **Exportovat filtr** na panelu nástrojů **Sestava výkonu** a pak zadáte umístění a název souboru pro. soubor *vspf* Pokud chcete načíst dříve uložený filtr, klikněte na **importovat filtr** a vyhledejte uložený soubor filtru. Filtrovat soubory lze také použít k filtrování datových souborů v počítačích, ve kterých je nainstalován samostatný Nástroje pro profilaci. Další informace najdete v tématu [VSPerfReport](../profiling/vsperfreport.md).

## <a name="see-also"></a>Viz také
- [Analýza dat nástrojů pro měření výkonu](../profiling/analyzing-performance-tools-data.md)
- [VSPerfReport](../profiling/vsperfreport.md)
