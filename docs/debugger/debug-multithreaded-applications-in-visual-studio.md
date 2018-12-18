---
title: Ladění vícevláknových aplikací | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/06/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ea1af90ae775ed24f5cceabeca04cdc901f545f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059675"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Ladění vícevláknových aplikací v sadě Visual Studio
Vlákno je řada pokynů, pro které operační systém uděluje času procesoru. Každý proces, na kterém běží v operačním systému se skládá z alespoň jednoho vlákna. Procesy, které mají více než jedno vlákno, se nazývají s více vlákny.  
  
Počítače s více procesory, vícejádrovými procesory nebo procesy využívající hyperthreading lze spustit několik souběžných vláken. Paralelní zpracování pomocí několika vlákny může výrazně zlepšit výkon aplikace, ale to může také ztížit ladění protože sledujete mnoho vláken.  
  
Multithreading můžete zavést nové typy možných chyb. Například dvě či více vláken možná bude nutné pro přístup k stejného prostředku, ale současně pouze jedno vlákno může bezpečně přistupovat k prostředku. Některé forma vzájemného vyloučení je nezbytné, abyste měli jistotu, že pouze jedno vlákno k prostředku v každém okamžiku. Pokud vzájemného vyloučení je implementovaná správně, můžete vytvořit *zablokování* stavu, ve kterém se spustí žádné vlákno. Zablokování je často obtížné problémem při ladění.

## <a name="tools-for-debugging-multithreaded-apps"></a>Nástroje pro ladění vícevláknových aplikací

Visual Studio poskytuje různé nástroje pro použití při ladění aplikace s více vlákny.

- Pro vlákna, jsou primární nástroje pro ladění vláken **vlákna** okna, značky vlákna ve zdrojových oknech **paralelní zásobníky** okně **paralelního sledování** okno a **umístění ladění** nástrojů. Další informace o **vlákna** okno a **umístění ladění** nástrojů, naleznete v tématu [návod: ladění pomocí okna vlákna](../debugger/how-to-use-the-threads-window.md). Další informace o použití **paralelní zásobníky** a **paralelní sledování** naleznete zde [Začínáme s laděním vícevláknových aplikacích](../debugger/get-started-debugging-multithreaded-apps.md). Obě témata ukazují, jak používat značky vlákna.
  
- Pro kód, který se používá [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) nebo [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime/), jsou základními nástroji pro ladění **paralelní zásobníky** okno, **Paralelní sledování** okně a **úlohy** okno, které podporuje také jazyk JavaScript. Abyste mohli začít, najdete v článku [návod: ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md) a [návod: ladění aplikace C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application). 

- Pro ladění vláken v GPU je primárním nástrojem **vlákna GPU** okna. Zobrazit [postupy: použití okna vláken GPU](../debugger/how-to-use-the-gpu-threads-window.md).  

- Pro procesy, jsou primární nástroje **připojit k procesu** dialogovém okně **procesy** okně a **umístění ladění** nástrojů.  
  
Visual Studio také poskytuje výkonné zarážky a trasování, což může být užitečné při ladění aplikací s více vlákny. Použití podmínky zarážky a filtrů k umístění zarážek na jednotlivá vlákna. Zarážky s trasováním umožňuje trasování spuštění programu bez narušení zkoumání problémů například zablokování. Další informace najdete v tématu [akce zarážek a zarážky s trasováním](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Ladění aplikace s více vlákny s uživatelským rozhraním může být zvláště obtížné. Zvažte spuštění aplikace na druhém počítači a použití vzdáleného ladění. Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).  
  
## <a name="articles-about-debugging-multithreaded-apps"></a>Články týkající se ladění vícevláknových aplikací

 [Začínáme s laděním vícevláknových aplikací](../debugger/get-started-debugging-multithreaded-apps.md)   
 Prohlídka funkcemi, kdy se klade důraz funkce ladění vlákna **paralelní zásobníky** okno a **paralelní sledování** okno.

 [Nástroje pro ladění vláken a procesů](../debugger/debug-threads-and-processes.md)  
 Obsahuje seznam funkcí nástroje pro ladění vláken a procesů.  
  
 [Ladění více procesů](../debugger/debug-multiple-processes.md)  
 Vysvětluje, jak ladění více procesů.

 [Návod: Ladění pomocí okna vlákna](../debugger/how-to-use-the-threads-window.md).  
 Návod, který ukazuje způsob použití **vlákna** okno a **umístění ladění** nástrojů. 

 [Návod: Ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Návod, který ukazuje způsob použití **paralelní zásobníky** a **úlohy** systému windows.  
  
 [Postupy: Přepnutí na jiné vlákno během ladění](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Několik způsobů, jak přepnout kontext ladění na jiný podproces.  
  
 [Postupy: Označení a odstranění označení vlákna](../debugger/how-to-flag-and-unflag-threads.md)  
 Opatřete značkou nebo příznakem vlákna, které chcete věnovat zvláštní pozornost při ladění.    
  
 [Postupy: ladění na vysoký výkon clusteru](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Techniky ladění aplikace, která běží na vysoký výkon clusteru.  

 [Tipy k ladění vláken v nativním kódu](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Jednoduché techniky, které mohou být užitečné při ladění nativních vláken. 

 [Postupy: Nastavení názvu vlákna v nativním kódu](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Pojmenujte vašeho vlákna, která se zobrazí v **vlákna** okna.  
  
 [Postupy: Nastavení názvu vlákna ve spravovaném kódu](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Pojmenujte vašeho vlákna, která se zobrazí v **vlákna** okna. 
  
## <a name="see-also"></a>Viz také:  

[Použití zarážek](../debugger/using-breakpoints.md)  
[Dělení na vlákna](/dotnet/standard/threading/index)  
[Multithreading u komponent](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
[Podpora multithreadingu ve starším kódu (Visual C++)](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)  
 [Ladění vláken a procesů](../debugger/debug-threads-and-processes.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)