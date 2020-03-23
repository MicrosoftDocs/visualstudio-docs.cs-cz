---
title: Kanály (zobrazení vláken) | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 94ac6e9e85a2d7dd504b2d2bd83bd1bbdb265ea0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62776774"
---
# <a name="channels-threads-view"></a>Kanály (zobrazení vláken)
Vizualizér souběžnosti zobrazuje čtyři druhy kanálů: kanály vláken, diskové kanály, kanály značek a kanály GPU.

## <a name="thread-channels"></a>Kanály vláken
 Kanál vlákna zobrazuje stav vlákna podle barvy pouze pro jedno vlákno. Když pozastavíte název kanálu, zobrazí se počáteční funkce pro dané vlákno. Vizualizér souběžnosti detekuje několik druhů vláken. Nejběžnější druhy jsou uvedeny v následující tabulce.

|||
|-|-|
|Hlavní vlákno|Podproces, který spustil aplikaci.|
|Pracovní podproces|Podproces, který byl vytvořen hlavní vlákno aplikace.|
|Pracovní podproces CLR|Pracovní podproces, který byl vytvořen za běhu společného jazyka (CLR).|
|Pomocník ladicího programu|Pracovní podproces, který byl vytvořen ladicím programem sady Visual Studio.|
|Vlákno ConcRT|Podproces, který byl vytvořen Microsoft Souběžnost Runtime.|
|Vlákno GDI|Podproces, který byl vytvořen GDIPlus.|
|Vlákno OLE/RPC|Podproces, který byl vytvořen jako pracovní podproces vzdáleného volání procedur.|
|Podproces vzdáleného volání procedur|Podproces, který byl vytvořen jako vlákno RPC.|
|Vlákno rozhraní Winsock|Podproces, který byl vytvořen jako podproces rozhraní Winsock.|
|Fond vláken|Podproces, který byl vytvořen fondu vláken CLR.|

## <a name="disk-channels"></a>Diskové kanály
 Diskové kanály odpovídají fyzickým jednotkám v počítači. Vzhledem k tomu, že pro každou fyzickou jednotku v systému existují samostatné kanály pro operace čtení a zápisu, má každá jednotka dva kanály. Čísla disků odpovídají názvům zařízení jádra. Diskový kanál se zobrazí pouze v případě, že na disku byla aktivita.

## <a name="marker-channels"></a>Značkovací kanály
 Kanály značek odpovídají událostem generovaným aplikací a knihovnám, které používá. Například paralelní knihovna úloh, paralelní vzorky knihovny a C++ AMP generovat události, které jsou zobrazeny jako značky. Každý kanál značky je spojen s ID vlákna, které se zobrazí vedle popisu kanálu. ID identifikuje vlákno, které vygenerovalo událost. Popis kanálu zahrnuje název zprostředkovatele trasování událostí pro Windows (ETW), který vygeneroval události. Pokud kanál zobrazuje události z [akcerobětu Visualizer SDK](../profiling/concurrency-visualizer-sdk.md), zobrazí se také název řady.

## <a name="gpu-channels"></a>Kanály GPU
 Kanály GPU zobrazují informace o aktivitě rozhraní DirectX 11 v systému.  Každý modul DirectX, který je přidružen k grafické kartě, má samostatný kanál.  Jednotlivé segmenty představují čas strávený zpracováním paketu DMA.

## <a name="see-also"></a>Viz také
- [zobrazení vláken](../profiling/threads-view-parallel-performance.md)