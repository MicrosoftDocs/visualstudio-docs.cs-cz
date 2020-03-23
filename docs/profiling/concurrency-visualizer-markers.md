---
title: Značky vizualizéru souběžnosti | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab5e4b65db5c3d96b16a68a7b8e21a2786b9110b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "63001054"
---
# <a name="concurrency-visualizer-markers"></a>Značky vizualizéru souběžnosti
Ve vizualizéru souběžnosti jsou značky ikony, které představují události v aplikaci.  Aplikace obvykle generuje tyto události k určení fáze nebo výskyty v aplikaci.  Události mohou být generovány aplikací nebo knihovnami a runtimes, které aplikace používá.

## <a name="kinds-of-markers"></a>Druhy značek
 Vizualizér souběžnosti používá tři druhy značek k reprezentaci událostí aplikace: příznaky, zprávy a rozpětí.

1. Pomocí *příznaku* označte zajímavý časový bod v aplikaci.  Můžete například použít příznak k označení, že hodnota proměnné dosáhla určité prahové hodnoty nebo že byla vyvolána výjimka.

2. *Zpráva* také označuje bod v čase, ale můžete ji použít pro trasování ve stylu protokolu.  Například co může být vypovězeno do souboru protokolu, můžete nyní zabalit volání zprávy, abyste ho mohli sledovat a zobrazit v vizualizéru souběžnosti. Vizualizátor souběžnosti můžete také použít k exportu těchto dat do souboru CSV.

3. *Rozpětí* představuje časový interval ve vaší aplikaci, například jednu z jeho fází.

## <a name="marker-linkage-to-threads"></a>Propojení značek s vlákny
 Každé vlákno, které generuje značky, má samostatný kanál časové osy.  ID vlákna, které je zodpovědné za generování událostí značky, se zobrazí vedle popisu kanálu značky.  ID, které je zobrazeno na levé straně kanálu značky, odpovídá ID jiného vlákna v aktuálním procesu.

## <a name="marker-importance"></a>Význam značky
 Značky mohou mít jednu ze čtyř úrovní důležitosti: nízká, normální, vysoká a kritická.  Zdroje značek můžete filtrovat na základě úrovně důležitosti.  Chcete-li například zobrazit pouze značky z určitého zdroje, který má normální nebo kritický význam, můžete filtr nakonfigurovat v dialogovém okně [Upřesnit nastavení.](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) Důležitost značky je zobrazena v popisku a v [sestavě značek](../profiling/markers-report.md).

## <a name="marker-category"></a>Kategorie značky
 Kategorie značky označuje skupinu událostí značky, které pocházejí ze stejného zdroje.  Vizualizér souběžnosti používá barvu k rozlišení různých kategorií příznaků a rozsahů. Vizualizátor souběžnosti můžete nakonfigurovat tak, aby používal kategorie k filtrování událostí značky od konkrétního poskytovatele událostí.  Ke konfiguraci filtru použijte dialogové okno [Upřesnit nastavení.](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md)

## <a name="known-sources-of-markers"></a>Známé zdroje markerů
 Každý zprostředkovatel ETW může generovat značky, pokud zprostředkovatel dodržuje určitá omezení. Můžete nakonfigurovat Akceptocurrency Visualizer poslouchat další zdroje událostí pro značky. Ve výchozím nastavení naslouchá těmto zdrojům událostí:

- [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)

- [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)

- [Tok dat](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)

- [Paralelní LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)

- [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)

- [Podpora značky scénářů](/previous-versions/visualstudio/visual-studio-2010/dd984115\(v\=vs.100\))

- [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)

  Kartu Značky můžete použít v dialogovém okně [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) k řízení, zda se značky z různých zdrojů zobrazí ve vizualizéru souběžnosti, a můžete filtrovat značky na základě důležitosti a kategorie.

## <a name="markers-from-eventsource"></a>Značky ze zdroje událostí
 Vizualizér souběžnosti může také zobrazit události EventSource.  Další informace naleznete [v tématu Vizualizace událostí EventSource jako značek](../profiling/visualizing-eventsource-events-as-markers.md).

## <a name="see-also"></a>Viz také
- [Značky příznaku](../profiling/flag-markers.md)
- [Značky zpráv](../profiling/message-markers.md)
- [Značky rozpětí](../profiling/span-markers.md)
- [Vizualizace událostí EventSource jako značek](../profiling/visualizing-eventsource-events-as-markers.md)