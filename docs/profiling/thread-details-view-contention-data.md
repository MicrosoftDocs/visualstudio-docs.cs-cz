---
title: Zobrazení podrobností vlákna – data konfliktů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 679fd9fd039fa903f5df5a479fa4f0e119bb7a9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778164"
---
# <a name="thread-details-view---contention-data"></a>Zobrazení podrobností vlákna – data tvrzení
Zobrazení Podrobnosti vlákna představuje graf časové osy blokování událostí ve vybraném vlákně profilování spustit, které byly způsobeny konflikty nad prostředky. Blokování událost nastane, když je vlákno vynuceno pozastavit spuštění, protože jiné vlákno má uzamčen přístup k prostředku.

 Toto zobrazení představuje časovou osu provádění vlákna jako vodorovný pruh a blokování událostí jako svislý pruh na vodorovné časové ose pro vlákno. V případě potřeby můžete přiblížit část časové osy a zobrazit jednotlivé události. Chcete-li zobrazit cestu spuštění funkcí, které vedly k události, klepněte na panel událostí. Funkce se zobrazí v okně **Zásobník volání.** Pokud je k dispozici zdrojový kód funkce, můžete klepnutím na název funkce upravit zdrojový soubor v rozhraní IDE sady Visual Studio.

## <a name="navigate-the-timeline"></a>Navigace na časové ose

#### <a name="to-zoom-in-on-a-timeline-segment"></a>Přiblížení segmentu časové osy

- Klepnutím a přetažením ukazatele myši vyberte oblast časové osy.

     Když uvolníte myš, zobrazení se přiblíží k vybranému časovému segmentu. Chcete-li přiblížit podrobnosti, můžete tento proces zopakovat. Posuvník na posuvníku času představuje relativní velikost časového segmentu, který je zobrazen v zobrazení.

#### <a name="to-zoom-out-on-a-timeline"></a>Oddálení na časové ose

- Kliknutím na **Oddálit** se vrátíte na předchozí úroveň přiblížení.

- Kliknutím na **Reset lupy** zobrazíte celou časovou osu v zobrazení.

#### <a name="to-view-the-call-stack-of-an-event"></a>Zobrazení zásobníku volání události

- V grafu časové osy klikněte na svislý pruh, který představuje událost.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Zobrazení nebo úprava zdrojového kódu funkce v zásobníku volání

- V okně **Zásobník volání** klikněte na název funkce.

  Zdrojový kód funkce musí být součástí aktuálního projektu.

#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>Zobrazení konfliktních událostí prostředku ve všech vláknech v profilování spustit

- V grafu časové osy klikněte na název nebo ID prostředku.

     Zobrazí se [zobrazení podrobností o zdroji](../profiling/resource-details-view-contention-data.md) pro vybraný zdroj.

#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>Zobrazení dat tvrzení vlákna v okně Procesy

- V grafu časové osy klikněte na **Součet**.

     Zobrazí [se zobrazení procesu](../profiling/process-view-contention-data.md) s vybraným vláknem.
