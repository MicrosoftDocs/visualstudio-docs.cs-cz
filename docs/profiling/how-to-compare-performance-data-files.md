---
title: Porovnání datových souborů výkonu | Microsoft Docs
description: Přečtěte si, jak porovnat výsledky dvou různých datových souborů profileru (. vsp nebo. vsps), abyste zjistili rozdíly, regrese výkonu a vylepšení výkonu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d47f51b5c46538bdeeb50db0627c5bd0840bcc14
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886142"
---
# <a name="how-to-compare-performance-data-files"></a>Postupy: Porovnání datových souborů výkonu
Můžete porovnat výsledky dvou různých datových souborů profileru (.*VSP* nebo. *vsps*) vytvořením sestavy nebo zobrazením porovnání (diff). Porovnání znázorňuje rozdíly, regrese výkonu a vylepšení, k nimž došlo z jedné relace profilování do druhé.

 Sestava rozdílů představuje zobrazení tabulky dat. V tabulce se zobrazí rozdílová hodnota nebo se změní ze směrného plánu. To se počítá pomocí určení rozdílu mezi starou hodnotou, základní hodnotou a výsledné hodnoty z nové analýzy.

 Porovnání dat profileru může být založeno na funkcích v kódu, modulech aplikace, řádcích, ukazateli instrukcí (IP) a typech.

 Prahovou hodnotu lze nastavit tak, aby snižovala šum a vyfiltroval všechna data v zobrazení tabulky řádků, které se nezměnily o zadanou hodnotu.

### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Chcete-li vytvořit zobrazení srovnávacího souboru pro projekt v Prohlížeč výkonu

1. V **prohlížeč výkonu** v části **sestavy** vyberte. *VSP* nebo. soubor sestavy *vsps* , který chcete použít jako hodnoty směrného plánu pro porovnání.

2. Vyberte. *VSP* nebo. *vsps* soubory sestav, které chcete porovnat.

3. Klikněte pravým tlačítkem na jeden z vybraných souborů a pak klikněte na **Porovnat sestavy**.

### <a name="to-compare-values"></a>Porovnání hodnot

1. Vyberte kartu **Sestava porovnání** v okně zobrazení sestav.

2. V rozevíracím seznamu **tabulka** vyberte buď funkci, nebo moduly, které chcete porovnat.

3. V rozevíracím seznamu **sloupec** vyberte hodnotu, kterou chcete porovnat.

4. volitelné Zadejte hodnotu **prahové** hodnoty.

5. Klikněte na **Použít**.

### <a name="to-compare-report-files"></a>Porovnání souborů sestav

1. V nabídce **analyzovat** vyberte **Porovnat sestavy výkonu**.

2. V okně **Vybrat soubory analýzy pro porovnání** vyhledejte a vyberte soubor analýzy **souborů standardních hodnot** (.*VSP* nebo. *vsps*) a **soubor porovnání** (.*VSP* nebo. *vsps*).

3. Klikněte na **OK**.
