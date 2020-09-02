---
title: Karta paměť, dialogové okno vlastností procesu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bdfc2740094c807818922f09ca3fef0a21c9e1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62931282"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Karta Paměť, dialogové okno vlastností procesu
Pomocí karty **paměť** můžete zobrazit, jak proces používá paměť. Chcete-li zobrazit [dialogové okno Vlastnosti procesu](../debugger/process-properties-dialog-box.md), přesuňte fokus do okna [zobrazení procesů](../debugger/processes-view.md) . Ve stromové struktuře vyberte libovolný uzel procesu a pak v nabídce **zobrazení** zvolte možnost **vlastnosti** .

 Na kartě **paměť** jsou k dispozici následující nastavení:

|Entry|Popis|
|-----------|-----------------|
|**Virtuální bajty**|Aktuální velikost (v bajtech) virtuálního adresního prostoru používaného procesem. Použití virtuálního adresního prostoru nemusí nutně znamenat odpovídající použití na disku nebo hlavní paměťové stránky. Virtuální prostor je však konečný a použití příliš mnoho může omezit schopnost procesu načíst knihovny.|
|**Virtuální bajty ve špičce**|Maximální počet bajtů virtuálního adresního prostoru, který proces v jednom okamžiku použil.|
|**Pracovní sada**|Sada stránek paměti, které byly v poslední době změněny vlákny procesu. Pokud je volná paměť v počítači nad prahovou hodnotou, stránky zůstanou v pracovní sadě procesu, i když se nepoužívají. Když volná paměť klesne pod prahovou hodnotu, stránky se z pracovní sady oříznou. Pokud jsou potřeba, budou v pracovní sadě před opuštěním hlavní paměti opět podmíněné.|
|**Špičková pracovní sada**|Maximální počet stránek v pracovní sadě tohoto procesu v jakémkoli bodě v čase.|
|**Bajty stránkovaného fondu**|Aktuální velikost stránkovaného fondu, který byl přidělen procesu. Stránkovaného fondu je oblast systémové paměti, kde součásti operačního systému získávají místo, které provádějí jejich určené úkoly. Stránky stránkovaného fondu je možné stránkovat pro stránkovací soubor, když ho systém nepoužívá za účelem udržování časových období.|
|**Bajty nestránkovaného fondu**|Aktuální počet bajtů v nestránkovaném fondu přiděleném procesem. Nestránkovaného fondu je oblast systémové paměti, ve které se při provádění jejich určených úkolů získává prostor pro součásti operačního systému. Stránky nestránkovaného fondu nelze stránkovat na stránkovací soubor; zůstávají v hlavní paměti, pokud jsou přiděleny.|
|**Soukromé bajty**|Aktuální počet bajtů, které tento proces přidělen, nemůže být sdílen s jinými procesy.|
|**Bezplatné bajty**|Celkový nevyužitý virtuální adresní prostor tohoto procesu.|
|**Rezervované bajty**|Celková velikost virtuální paměti rezervované pro budoucí použití tímto procesem.|
|**Bajty volných imagí**|Velikost virtuálního adresního prostoru, který není používán nebo rezervován obrázky v rámci tohoto procesu.|
|**Rezervované bajty imagí**|Součet všech virtuálních paměť vyhrazených pro Image spouštěných v rámci tohoto procesu.|