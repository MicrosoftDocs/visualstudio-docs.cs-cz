---
title: Ladění vícevláknových aplikací | Microsoft Docs
description: Ladění vícevláknových aplikací v aplikaci Visual Studio. Přečtěte si nástroje a další články o ladění aplikací s více vlákny.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/06/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fed6580219964ab71f5a5010060c1af193375df
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727135"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Ladění vícevláknových aplikací v aplikaci Visual Studio
Vlákno je posloupnost pokynů, na které operační systém uděluje čas procesoru. Každý proces, který běží v operačním systému, se skládá alespoň z jednoho vlákna. Procesy, které mají více než jedno vlákno, se nazývají multithreading.

Počítače s více procesory, procesory s více jádry nebo procesy s jedním vláknem můžou spouštět několik současných vláken. Paralelní zpracování pomocí mnoha vláken může významně zlepšit výkon programu, ale může to také ztížit ladění, protože sledujete mnoho vláken.

Multithreading může zavést nové typy potenciálních chyb. Například dva nebo více vláken může potřebovat přístup ke stejnému prostředku, ale přístup k prostředku může mít pouze jeden podproces současně. Některá forma vzájemného vyloučení je nezbytná, aby se zajistilo, že přístup k prostředku je kdykoli k dispozici pouze v jednom vlákně. Pokud je vzájemné vyloučení nesprávně implementováno, může vytvořit stav *zablokování* , když se neprovede žádné vlákno. Vzájemné zablokování často představují pevný problém k ladění.

## <a name="tools-for-debugging-multithreaded-apps"></a>Nástroje pro ladění aplikací s více vlákny

Visual Studio poskytuje různé nástroje pro použití při ladění aplikací s více vlákny.

- Pro vlákna jsou primární nástroje pro ladění vlákna okno **vlákna** , značky vláken ve zdrojových oknech, **okna paralelních** sledování a okno **paralelního sledování** a panel nástrojů **umístění ladění** . Další informace o okně **vlákna** a panelu nástrojů **umístění ladění** naleznete v tématu [Návod: ladění pomocí okna vlákna](../debugger/how-to-use-the-threads-window.md). Informace o tom, jak používat **paralelní zásobníky** a okna **paralelního sledování** , najdete v tématu Začínáme [s laděním vícevláknové aplikace](../debugger/get-started-debugging-multithreaded-apps.md). Obě témata ukazují, jak používat značky vláken.

- Pro kód, který používá [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) nebo [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime/), jsou primární nástroje pro ladění okno **paralelní zásobníky** , okno **paralelního sledování** a okno **úlohy** , které také podporuje jazyk JavaScript. Chcete-li začít, přečtěte si [Návod: ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md) a [Návod: ladění aplikace C++ amp](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application).

- Pro ladění vláken na GPU je primárním nástrojem okno **vlákna GPU** . Viz [Postupy: použití okna vláken GPU](../debugger/how-to-use-the-gpu-threads-window.md).

- Pro procesy jsou primární nástroje v dialogovém okně **připojit k procesu** , v okně **procesy** a na panelu nástrojů **umístění ladění** .

Visual Studio také poskytuje výkonné zarážky a trasováním, což může být užitečné při ladění aplikací s více vlákny. Použijte podmínky a filtry zarážek k umístění zarážek na jednotlivá vlákna. Trasováním vám umožní trasovat provádění programu bez přerušení, abyste mohli zkoumat problémy, jako je zablokování. Další informace naleznete v tématu [Akce zarážky a trasováním](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Ladění vícevláknové aplikace, která má uživatelské rozhraní, může být obzvláště obtížné. Můžete zvážit spuštění aplikace na druhém počítači a použití vzdáleného ladění. Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

## <a name="articles-about-debugging-multithreaded-apps"></a>Články o ladění aplikací s více vlákny

 [Začínáme s laděním vícevláknové aplikace](../debugger/get-started-debugging-multithreaded-apps.md)

Prohlídka funkcí ladění vlákna a zdůraznění funkcí v okně **paralelní zásobníky** a v okně **paralelní kukátko** .

 [Nástroje pro ladění vláken a procesů](../debugger/debug-threads-and-processes.md)

Uvádí funkce nástrojů pro ladění vláken a procesů.

 [Ladění více procesů](../debugger/debug-multiple-processes.md)

Vysvětluje, jak ladit více procesů.

 [Návod: ladění pomocí okna vlákna](../debugger/how-to-use-the-threads-window.md).

Návod, který ukazuje, jak použít okno **vlákna** a panel nástrojů **umístění ladění** .

 [Návod: Ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md)

Návod, který ukazuje, jak používat okna **paralelní zásobníky** a **úlohy** .

 [Postupy: Přepnutí na jiné vlákno během ladění](../debugger/how-to-switch-to-another-thread-while-debugging.md)

Několik způsobů přepínání kontextu ladění na jiné vlákno.

 [Postupy: příznak a odoznačení vláken](../debugger/how-to-flag-and-unflag-threads.md)

Označte nebo označte vlákna, kterým chcete poskytnout zvláštní pozornost při ladění.

 [Postupy: ladění v clusteru s vysokým výkonem](../debugger/how-to-debug-on-a-high-performance-cluster.md)

Techniky pro ladění aplikace, která běží v clusteru s vysokým výkonem.

 [Tipy k ladění vláken v nativním kódu](../debugger/tips-for-debugging-threads-in-native-code.md)

Jednoduché techniky, které mohou být užitečné pro ladění nativních vláken.

 [Postupy: nastavení názvu vlákna v nativním kódu](../debugger/how-to-set-a-thread-name-in-native-code.md)

Dejte vláknu název, který se zobrazí v okně **vlákna** .

 [Postupy: nastavení názvu vlákna ve spravovaném kódu](../debugger/how-to-set-a-thread-name-in-managed-code.md)

Dejte vláknu název, který se zobrazí v okně **vlákna** .

## <a name="see-also"></a>Viz také

- [Použití zarážek](../debugger/using-breakpoints.md)
- [Dělení na vlákna](/dotnet/standard/threading/index)
- [Multithreading v součástech](/previous-versions/3es4b6yy(v=vs.140))
- [Podpora multithreadingu pro starší kód](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [Ladění vláken a procesů](../debugger/debug-threads-and-processes.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)