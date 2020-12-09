---
title: Karta Obecné, dialogové okno Vlastnosti okna | Microsoft Docs
description: Zobrazte kartu Obecné pro informace o okně, včetně titulku, popisovače, obdélníku, popisovače instance aplikace, popisovače nabídky a uživatelských dat.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 125420655af4fb021e264c3885a739fc90cfff59
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862747"
---
# <a name="general-tab-window-properties-dialog-box"></a>Karta Obecné, dialogové okno vlastnosti okna
Na kartě **Obecné** můžete zobrazit informace o vybraném okně. Chcete-li zobrazit [dialogové okno Vlastnosti okna](../debugger/window-properties-dialog-box.md), přesuňte fokus do okna [zobrazení systému Windows](../debugger/windows-view.md) . Ve stromové struktuře vyberte libovolný uzel okna a pak v nabídce **zobrazení** zvolte možnost **vlastnosti** .

 Na kartě **Obecné** jsou k dispozici následující nastavení:

|Entry|Popis|
|-----------|-----------------|
|**Titulek okna**|Text v záhlaví okna nebo text obsažený v okně, pokud se jedná o ovládací prvek.|
|**Popisovač okna**|Jedinečné ID tohoto okna Znovu se používají čísla popisovačů oken; identifikují okno pouze za dobu života tohoto okna.|
|**Procedura okna**|Virtuální adresa funkce procedury okna pro toto okno. Toto pole také označuje, zda je toto okno oknem Unicode a zda je roztříděné.|
|**Obdélník**|Ohraničující obdélník okna Zobrazí se také velikost obdélníku. Jednotky jsou pixely v souřadnicích obrazovky.|
|**Obnovený Rect**|Ohraničující obdélník pro obnovené okno Zobrazí se také velikost obdélníku. Obnovený Rect se bude lišit od obdélníku jenom v případě, že se okno maximalizuje nebo minimalizuje. Jednotky jsou pixely v souřadnicích obrazovky.|
|**Rect klienta**|Ohraničující obdélník oblasti klienta okna. Zobrazí se také velikost obdélníku. Jednotky jsou pixely relativní vzhledem k levému hornímu rohu klientské oblasti okna.|
|**Popisovač instance**|Popisovač instance aplikace Obslužné rutiny instancí nejsou jedinečné.|
|**ID ovládacího prvku nebo obslužná rutina nabídky**|Pokud se okno zobrazí jako podřízené okno, zobrazí se popisek ID ovládacího prvku. ID ovládacího prvku je celé číslo, které identifikuje ID ovládacího prvku podřízeného okna. Pokud okno, které se zobrazuje, není podřízené okno, zobrazí se popisek popisovače nabídky. Obslužná rutina nabídky je celé číslo, které identifikuje popisovač nabídky přidružené k tomuto oknu.|
|**Uživatelská data**|Data specifická pro aplikaci, která jsou připojena k této struktuře oken.|
|**Bajty oken**|Počet dalších bajtů přidružených k tomuto oknu. Význam těchto bajtů určuje aplikace. Rozbalením seznamu zobrazíte hodnoty bajtů ve formátu DWORD.|