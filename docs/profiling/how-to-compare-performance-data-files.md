---
title: 'Postup: Porovnání datových souborů o výkonu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c6dc9d485f6f40eb345ade8f9680be9e0b948106
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778996"
---
# <a name="how-to-compare-performance-data-files"></a>Postupy: Porovnání datových souborů výkonu
Můžete porovnat výsledky dvou různých datových souborů profileru (.* vsp* nebo . *vsps*) vytvořením porovnání ("Diff") sestavy nebo zobrazení. Porovnání ukazuje rozdíly, regrese výkonu a vylepšení, ke kterým došlo z jedné relace profilování do druhé.

 Sestava Diff představuje zobrazení tabulky dat. Tabulka představuje rozdíl nebo změnu od směrného plánu. To se vypočítá určením rozdílu mezi starou hodnotou, hodnotou směrného plánu a výslednou hodnotou z nové analýzy.

 Porovnání dat profileru může být založeno na funkcích v kódu, modulech v aplikaci, řádcích, instrukčních ukazatelích (IP) a typech.

 Prahovou hodnotu lze nastavit tak, aby se snížil šum a odfiltrována všechna data v zobrazení tabulky řádků, které se nezměnily o zadané množství.

### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Vytvoření zobrazení souboru porovnání pro projekt v Průzkumníku výkonu

1. V **Průzkumníku výkonu**vyberte v části **Sestavy**položku . *vsp* nebo . *vsps* soubor sestavy, který chcete použít jako základní hodnoty pro porovnání.

2. Vyberte možnost . *vsp* nebo . *vsps* sestavy souborů, které chcete porovnat.

3. Klepněte pravým tlačítkem myši na jeden z vybraných souborů a potom klepněte na příkaz **Porovnat sestavy**.

### <a name="to-compare-values"></a>Porovnání hodnot

1. V okně Zobrazení sestavy vyberte kartu **Sestava porovnání.**

2. V rozevíracím seznamu **Tabulka** vyberte funkci nebo moduly, které chcete porovnat.

3. V rozevíracím seznamu **Sloupec** vyberte hodnotu, kterou chcete porovnat.

4. (nepovinné) Zadejte hodnotu **pro prahovou hodnotu**.

5. Klikněte na **Použít**.

### <a name="to-compare-report-files"></a>Porovnání souborů sestavy

1. V nabídce **Analyzovat** vyberte **možnost Porovnat zprávy o výkonu**.

2. V okně **Vybrat soubory analýzy pro porovnání** procházejte a vyberte soubor **analýzy souboru souboru směrného plánu** (.* vsp* nebo . *vsps*) a **srovnávací soubor** (.* vsp* nebo . *vsps*).

3. Klikněte na tlačítko **OK**.
