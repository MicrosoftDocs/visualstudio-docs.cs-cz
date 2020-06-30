---
title: Kanály (zobrazení vláken) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.channelnames
helpviewer_keywords:
- Concurrency Visualizer, Channels (Threads View)
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f18a636d83210b2329d103b1babdf47e697fd5c7
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537082"
---
# <a name="channels-threads-view"></a>Kanály (zobrazení vláken)
Vizualizátor souběžnosti zobrazuje čtyři druhy kanálů: kanály vláken, kanály disku, kanály značek a grafické kanály GPU.

## <a name="thread-channels"></a>Kanály vláken
 Kanál vlákna zobrazuje stav vlákna podle barvy pro pouze jedno vlákno. Když na název kanálu pozastavíte, zobrazí se funkce spuštění daného vlákna. Vizualizátor souběžnosti detekuje několik druhů vláken. Nejběžnější druhy jsou uvedeny v následující tabulce.

|Thread|Popis|
|-|-|
|Hlavní vlákno|Vlákno, které aplikaci spustilo.|
|Pracovní vlákno|Vlákno, které bylo vytvořeno hlavním vláknem aplikace.|
|Pracovní vlákno CLR|Pracovní vlákno, které bylo vytvořeno modulem CLR (Common Language Runtime).|
|Pomocník pro ladicí program|Pracovní vlákno, které vytvořil ladicí program sady Visual Studio.|
|Vlákno ConcRT|Vlákno, které vytvořila aplikace Microsoft Concurrency Runtime.|
|Vlákno GDI|Vlákno, které vytvořila služba GDIPlus.|
|Vlákno OLE/RPC|Vlákno, které bylo vytvořeno jako pracovní vlákno RPC.|
|Vlákno RPC|Vlákno, které bylo vytvořeno jako vlákno RPC.|
|Vlákno rozhraní Winsock|Vlákno, které bylo vytvořeno jako vlákno rozhraní Winsock.|
|Fond vláken|Vlákno, které bylo vytvořeno fondem vláken CLR.|

## <a name="disk-channels"></a>Diskové kanály
 Diskové kanály odpovídají fyzickým jednotkám v počítači. Vzhledem k tomu, že pro každou fyzickou jednotku v systému existují samostatné kanály pro operace čtení a zápisu, mají jednotlivé jednotky dva kanály. Čísla disků odpovídají názvům zařízení jádra. Diskový kanál se zobrazí jenom v případě, že disk obsahuje aktivitu.

## <a name="marker-channels"></a>Kanály značek
 Kanály značek odpovídají událostem generovaným aplikací a knihovnám, které používá. Například úloha paralelní knihovna, knihovna paralelních vzorů a C++ AMP generuje události, které jsou zobrazeny jako značky. Každý kanál značek je přidružen k ID vlákna, které se zobrazí vedle popisu kanálu. ID identifikuje vlákno, které událost vygenerovalo. Popis kanálu zahrnuje název poskytovatele trasování událostí pro Windows (ETW), který události vygeneroval. Pokud kanál zobrazuje události ze [sady Vizualizátor souběžnosti SDK](../profiling/concurrency-visualizer-sdk.md), zobrazí se také název řady.

## <a name="gpu-channels"></a>Kanály GPU
 Kanály GPU zobrazují informace o aktivitě rozhraní DirectX 11 v systému.  Každý modul DirectX, který je přidružený k grafické kartě, má samostatný kanál.  Jednotlivé segmenty reprezentují čas strávený zpracováním paketu DMA.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)