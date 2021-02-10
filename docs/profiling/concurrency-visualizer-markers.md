---
title: Značky Vizualizátor souběžnosti | Microsoft Docs
description: 'Přečtěte si o značkách v Vizualizátor souběžnosti. Značky jsou ikony, které představují události generované aplikací. Existují tři typy: příznaky, zprávy a rozsahy.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3ff013f546393447b8303575489164a3a7be00a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941135"
---
# <a name="concurrency-visualizer-markers"></a>Značky Vizualizátor souběžnosti
Ve Vizualizátor souběžnosti jsou značky označení ikony, které představují události v aplikaci.  Obvykle aplikace generuje tyto události pro určení fází nebo výskytů v aplikaci.  Události může generovat aplikace nebo knihovny a moduly runtime, které aplikace používá.

## <a name="kinds-of-markers"></a>Druhy značek
 Vizualizátor souběžnosti používá tři druhy značek k vyjádření událostí aplikace: příznaky, zprávy a rozsahy.

1. Použijte *příznak* k označení zajímavého bodu v čase vaší aplikace.  Příznak můžete například použít k reprezentaci, že hodnota proměnné dosáhla určité prahové hodnoty nebo že byla vyvolána výjimka.

2. *Zpráva* také označí bod v čase, ale můžete ho použít pro trasování ve stylu log.  Například to, co mohlo být v souboru protokolu dumpingové, teď můžete zalomit voláním zprávy, abyste ho mohli sledovat a zobrazit v Vizualizátor souběžnosti. K exportu těchto dat do souboru CSV můžete také použít Vizualizátor souběžnosti.

3. *Rozsah* představuje časový interval ve vaší aplikaci, například jedna z jeho fází.

## <a name="marker-linkage-to-threads"></a>Označení vazby na vlákna
 Každé vlákno, které generuje značky, má samostatný kanál časové osy.  ID podprocesu, který je zodpovědný za generování událostí značky, se zobrazí vedle popisu kanálu značky.  ID, které je zobrazeno na levé straně kanálu značky, odpovídá ID jiného vlákna v aktuálním procesu.

## <a name="marker-importance"></a>Důležitost značky
 Značky můžou mít jednu ze čtyř úrovní důležitosti: nízká, Normal, vysoká a kritická.  Můžete filtrovat zdroje značek na základě úrovně důležitosti.  Pokud například chcete zobrazit pouze značky z konkrétního zdroje, který má normální nebo kritické důležitost, můžete nakonfigurovat filtr v dialogovém okně [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) . Důležitost značky se zobrazí v popisu tlačítka a v [sestavě značek](../profiling/markers-report.md).

## <a name="marker-category"></a>Kategorie značek
 Kategorie značek označuje skupinu událostí značky, které pocházejí ze stejného zdroje.  Vizualizátor souběžnosti používá barvu k odlišení různých kategorií příznaků a rozsahů. Můžete nakonfigurovat, aby Vizualizér souběžnosti používal kategorie k filtrování událostí značek od určitého poskytovatele událostí.  Pomocí dialogového okna [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) můžete nakonfigurovat filtr.

## <a name="known-sources-of-markers"></a>Známé zdroje značek
 Libovolný poskytovatel trasování událostí pro Windows může generovat značky, pokud poskytovatel dodržuje určitá omezení. Můžete nakonfigurovat Vizualizátor souběžnosti, aby naslouchal dalším zdrojům událostí pro značky. Ve výchozím nastavení naslouchá těmto zdrojům událostí:

- [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)

- [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)

- [Tok dat](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)

- [Paralelní LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)

- [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)

- [Podpora značek scénářů](/previous-versions/visualstudio/visual-studio-2010/dd984115\(v\=vs.100\))

- [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)

  Kartu značky v dialogovém okně [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) můžete použít k určení, zda se ve Vizualizátor souběžnosti zobrazují značky z různých zdrojů, a můžete filtrovat značky na základě důležitosti a kategorie.

## <a name="markers-from-eventsource"></a>Značky z EventSource
 Vizualizátor souběžnosti může také zobrazit události EventSource.  Další informace najdete v tématu [Vizualizace událostí EventSource jako značek](../profiling/visualizing-eventsource-events-as-markers.md).

## <a name="see-also"></a>Viz také
- [Značky příznaků](../profiling/flag-markers.md)
- [Značky zpráv](../profiling/message-markers.md)
- [Značky span](../profiling/span-markers.md)
- [Vizualizace událostí EventSource jako značek](../profiling/visualizing-eventsource-events-as-markers.md)