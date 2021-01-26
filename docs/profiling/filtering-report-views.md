---
title: Filtrování zobrazení sestav | Microsoft Docs
description: V aplikaci Visual Studio použijte filtry na soubory dat profilování, abyste omezili data profilování zobrazená v zobrazeních sestav výkonu a exportovali do souborů sestav.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f6ba3e207b180b26ea4b53765926b16fb2e85d48
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801449"
---
# <a name="filter-report-views"></a>Filtrovat zobrazení sestav
Můžete použít filtry na soubory dat profilování a omezit tak data profilování, která se zobrazují v zobrazeních sestavy výkonu a exportována do souborů sestav. Sestavu můžete omezit na data mezi hodnotami časových razítek a data můžete omezit na konkrétní procesy a vlákna. Filtry můžete uložit do souboru a pak vytvořit filtr v jiném datovém souboru profilování importováním uloženého filtru.

 Sestavu můžete také omezit na časové segmenty pomocí grafické osy v zobrazení souhrnu. Viz [Postupy: filtrování zobrazení sestav na časové ose souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

 Chcete-li vyloučit systémové kódy a kód třetí strany ze sestavy, přečtěte si téma [Postup: filtrování nástroje pro profilaci zobrazení sestav pro zobrazení pouze můj kód](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)

## <a name="procedures"></a>Procedury

#### <a name="to-create-a-profiler-report-filter"></a>Vytvoření filtru sestavy profileru

1. Pokud není zobrazeno okno filtru zobrazení sestavy výkonu, klikněte na tlačítko **Zobrazit filtr** na panelu nástrojů zobrazení sestavy výkonu.

     Filtr zobrazení sestav výkonu je tabulka. Každý řádek tabulky představuje klauzuli filtru. Do filtru můžete přidat tolik klauzulí, kolik chcete.

2. U každé klauzule, kterou chcete přidat do filtru, vyberte nebo zadejte hodnoty v následujících polích řádku.

    |Pole|Popis|
    |-----------|-----------------|
    |**A/nebo**|Vyberte **a** Pokud má tato klauzule a další klauzule hodnotu true, aby odpovídaly výsledku. Vyberte **nebo** Pokud má tato klauzule nebo další klauzule hodnotu true, aby odpovídaly výsledku.|
    |**Pole**|Vyberte pole sestavy, které chcete použít v klauzuli Filter ze zobrazeného seznamu datových polí.|
    |**Operátor**|Vyberte operátor, který určuje vztah, který chcete v klauzuli mezi polem a hodnotou.<br /><br /> = Equals<br /><br /> <>  se nerovná<br /><br /> < menší než<br /><br /> > větší než<br /><br /> <= menší než nebo rovno<br /><br /> >= větší než nebo rovno|
    |**Hodnota**|Vyberte nebo zadejte hodnotu, která se má hledat. Některá pole uvádějí dostupné hodnoty pro pole.|

#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>Vytvoření filtru sestavy profileru ze zobrazení zprávy značky

1. Vyberte možnost **značky** ze seznamu **aktuální zobrazení** na panelu nástrojů zobrazení sestavy výkonu.

    Zobrazí se sestava značky profileru.

2. Vyberte ETW nebo vzorkování, a to i v případě, že chcete použít jako výchozí bod sestavy.

3. Stiskněte a podržte klávesu CTRL a klikněte na událost, kterou chcete použít jako koncový bod sestavy.

4. Klikněte pravým tlačítkem a potom klikněte na jednu z následujících možností:

   - **Přidání filtru při označení** vytvoří klauzule filtru, které používají sloupec označit jako pole filtru.

   - **Přidat filtr na časová razítka** vytvoří klauzule filtru, které jako pole filtru používají časové razítko ve sloupci milisekund.

     Tyto dvě možnosti filtrují aktuální datový soubor na stejném počátečním a koncovém bodu. Je-li filtr exportován pro použití v jiných sestavách, může být tato možnost vhodnější.

#### <a name="to-load-an-existing-filter-from-a-file"></a>Načtení existujícího filtru ze souboru

1. Na panelu nástrojů zobrazení sestavy výkonu klikněte na **importovat filtr**.

     Zobrazí se dialogové okno **načíst filtr** .

2. Zadejte umístění a název souboru filtru (. vspf), který se má načíst.

#### <a name="to-execute-a-filter"></a>Spuštění filtru

- Na panelu nástrojů zobrazení sestavy výkonu klikněte na **Spustit filtr**.

#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>Zastavení filtru, který trvá příliš dlouho, než se spustí

- Na panelu nástrojů zobrazení sestavy výkonu klikněte na **zastavit filtr**.

#### <a name="to-remove-a-filter-on-a-report-view"></a>Odebrání filtru v zobrazení sestavy

1. Odstraňte řádky klauzulí v filtru zobrazení sestav výkonu.

2. Na panelu nástrojů zobrazení sestavy výkonu klikněte na **Spustit filtr**.

#### <a name="to-save-a-filter-to-a-file"></a>Uložení filtru do souboru

1. Na panelu nástrojů zobrazení sestavy výkonu klikněte na **Exportovat filtr**.

     Zobrazí se dialogové okno **Uložit filtr** .

2. Zadejte umístění a název souboru filtru (. vspf), který chcete uložit.

## <a name="see-also"></a>Viz také
- [Přizpůsobení zobrazení sestav nástrojů pro měření výkonu](../profiling/customizing-performance-tools-report-views.md)
