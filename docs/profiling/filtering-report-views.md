---
title: Filtrování zobrazení sestavy | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, configuring
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: acdfe8f96d30ad881d8c9c0f0a9ff48c3353afee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779243"
---
# <a name="filter-report-views"></a>Filtrování zobrazení sestavy
Filtry můžete použít pro profilování datových souborů, abyste omezili data profilování, která jsou zobrazena v zobrazeních sestavy výkonu a exportována do souborů sestav. Můžete omezit sestavu na data mezi hodnotami časového razítka a můžete omezit data na konkrétní procesy a vlákna. Filtry můžete uložit do souboru a importem uloženého filtru vytvořit filtr v jiném souboru dat profilování.

 Sestavu můžete také omezit na časový segment pomocí grafické časové osy v souhrnném zobrazení. Viz [Postup: Filtrování zobrazení sestavy ze souhrnné časové osy](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

 Informace o vyloučení systémového kódu a kódu třetí strany ze sestavy naleznete v tématu [Postup: Filtrování zobrazení sestavy nástrojů profilování k zobrazení pouze kódu](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)

## <a name="procedures"></a>Procedury

#### <a name="to-create-a-profiler-report-filter"></a>Vytvoření filtru sestavy profileru

1. Pokud se okno Filtr zobrazení sestavy výkonu nezobrazí, klepněte na tlačítko **Zobrazit filtr** na panelu nástrojů Zobrazení sestavy výkonu.

     Filtr zobrazení sestavy výkonu je tabulka. Každý řádek tabulky představuje klauzuli filtru. Do filtru můžete přidat libovolný počet klauzulí.

2. Pro každou klauzuli, kterou chcete přidat do filtru, vyberte nebo zadejte hodnoty do následujících polí řádku.

    |Pole|Popis|
    |-----------|-----------------|
    |**Nebo**|Zvolte **A** pokud tato klauzule a další klauzule musí být pravdivé, aby odpovídaly výsledku. Zvolte **Nebo** pokud tato klauzule nebo další klauzule může být true tak, aby odpovídala výsledku.|
    |**Pole**|Vyberte pole sestavy, které chcete použít v klauzuli filtru ze zobrazeného seznamu datových polí.|
    |**Operátor**|Vyberte operátor, který určuje požadovaný vztah v klauzuli mezi polem a hodnotou.<br /><br /> = Rovná se<br /><br /> <>  není rovnoprávně<br /><br /> < méně než<br /><br /> > větší než<br /><br /> <= menší nebo rovno<br /><br /> >= větší nebo rovno|
    |**Hodnotu**|Vyberte nebo zadejte hodnotu, kterou chcete vyhledat. V některých polích jsou uvedeny dostupné hodnoty pro pole.|

#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>Vytvoření filtru sestavy profileru ze zobrazení Sestavy značek

1. Vyberte **značky** ze seznamu **Aktuální zobrazení** na panelu nástrojů Zobrazení sestavy výkonu.

    Zobrazí se sestava Profiler marks.

2. Vyberte ETW nebo vzorkování i to, co chcete použít jako výchozí bod sestavy.

3. Stiskněte a podržte klávesu CTRL a klepněte na událost, kterou chcete použít jako koncový bod sestavy.

4. Klikněte pravým tlačítkem myši a potom klikněte na jednu z následujících možností:

   - **Přidat filtr na značky** vytvoří klauzule filtru, které používají sloupec Označit jako pole filtru.

   - **Přidat filtr na časová razítka** vytvoří klauzule filtru, které používají sloupec Časové razítko v milisekundách jako pole filtru.

     Dvě možnosti filtrují aktuální datový soubor ve stejném počátečním a koncovém bodě. Obě možnosti mohou být lepší, pokud exportujete filtr pro použití v jiných sestavách.

#### <a name="to-load-an-existing-filter-from-a-file"></a>Načtení existujícího filtru ze souboru

1. Na panelu nástrojů Zobrazení sestavy výkonu klepněte na **položku Importovat filtr**.

     Zobrazí se dialogové okno **Načíst filtr.**

2. Zadejte umístění a název souboru filtru (.vspf), který má být načítán.

#### <a name="to-execute-a-filter"></a>Spuštění filtru

- Na panelu nástrojů Zobrazení sestavy výkonu klepněte na **tlačítko Spustit filtr**.

#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>Zastavení filtru, jehož spuštění trvá příliš dlouho

- Na panelu nástrojů Zobrazení sestavy výkonu klepněte na tlačítko **Zastavit filtr**.

#### <a name="to-remove-a-filter-on-a-report-view"></a>Odebrání filtru v zobrazení sestavy

1. Odstraňte řádky klauzulí ve filtru zobrazení sestavy výkonu.

2. Na panelu nástrojů Zobrazení sestavy výkonu klepněte na **tlačítko Spustit filtr**.

#### <a name="to-save-a-filter-to-a-file"></a>Uložení filtru do souboru

1. Na panelu nástrojů Zobrazení sestavy výkonu klepněte na **položku Exportovat filtr**.

     Zobrazí se dialogové okno **Uložit filtr.**

2. Zadejte umístění a název souboru filtru (.vspf), který chcete uložit.

## <a name="see-also"></a>Viz také
- [Přizpůsobení zobrazení sestav nástrojů pro měření výkonu](../profiling/customizing-performance-tools-report-views.md)
