---
title: Ladění vícevláknových aplikací
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cb43c9a32f3dfd0a6383d466f7cd283acf0ab3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691284"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Ladění vícevláknových aplikací v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vlákno je posloupnost pokynů, na které operační systém přiděluje čas procesoru. Každý proces, který běží v operačním systému, se skládá alespoň z jednoho vlákna. Procesy, které mají více než jedno vlákno, se nazývají multithreading.

 Počítače s více procesory, procesory s více jádry nebo procesy s jedním vláknem mohou spouštět více vláken současně. Paralelní zpracování více vláken může významně zlepšit výkon programu, ale může také vést ke složitějšímu ladění, protože zavádí nutnost sledovat více vláken.

 Kromě toho multithreading přináší některé nové typy potenciálních chyb. Například dva nebo více vláken musí mít přístup ke stejnému prostředku, ale pouze jedno vlákno může k prostředkům bezpečně přistupovat. Některá forma vzájemného vyloučení je nezbytná, aby bylo zajištěno, že přístup k prostředku probíhá pouze v jednom vlákně. Pokud je vzájemné vyloučení provedeno nesprávně, může vytvořit stav *zablokování* , pokud nelze spustit žádné vlákno. Zablokování může být obzvláště pevný problém pro ladění.

 Visual Studio poskytuje okno **vláken** , okno vláken GPU, paralelní okno kukátko a další funkce, které usnadňují ladění s více vlákny. Nejlepším způsobem, jak získat informace o funkcích pro práci s vlákny, je Projděte si návody. Viz [Návod: Ladění vícevláknové aplikace](../debugger/walkthrough-debugging-a-multithreaded-application.md) a [Návod: ladění aplikace C++ amp](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).

 Visual Studio také poskytuje výkonné zarážky a trasováním, což může být velmi užitečné při ladění aplikací s více vlákny. Filtry zarážek lze použít k umístění zarážek na jednotlivá vlákna. Viz [použití zarážek](../debugger/using-breakpoints.md) .

 Ladění vícevláknové aplikace, která má uživatelské rozhraní, může být obzvláště obtížné. V takovém případě můžete zvážit spuštění aplikace v druhém počítači a použití vzdáleného ladění. Informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

## <a name="in-this-section"></a>V tomto oddílu
 [Ladění vláken a procesů](../debugger/debug-threads-and-processes.md) Vysvětluje základy ladění vláken a procesů.

 [Ladění více procesů](../debugger/debug-multiple-processes.md) Vysvětluje, jak ladit více procesů.

 [Postupy: použití okna vláken](../debugger/how-to-use-the-threads-window.md) Užitečné postupy pro ladění vláken s oknem **vláken** .

 [Postupy: přepnutí na jiné vlákno během ladění](../debugger/how-to-switch-to-another-thread-while-debugging.md) Tři způsoby přepínání kontextu ladění na jiné vlákno.

 [Postupy: příznak a odoznačení vláken](../debugger/how-to-flag-and-unflag-threads.md) Označte nebo označte vlákna, kterým chcete poskytnout zvláštní pozornost při ladění.

 [Postupy: nastavení názvu vlákna v nativním kódu](../debugger/how-to-set-a-thread-name-in-native-code.md) Dejte vláknu název, který se zobrazí v okně **vlákna** .

 [Postupy: nastavení názvu vlákna ve spravovaném kódu](../debugger/how-to-set-a-thread-name-in-managed-code.md) Dejte vláknu název, který se zobrazí v okně **vlákna** .

 [Návod: Ladění vícevláknové aplikace](../debugger/walkthrough-debugging-a-multithreaded-application.md)
Průvodce pro funkce ladění vlákna s důrazem na funkce, jak na to [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] .

 [Postupy: ladění v clusteru s vysokým výkonem](../debugger/how-to-debug-on-a-high-performance-cluster.md) Techniky pro ladění aplikace, která běží v clusteru s vysokým výkonem.

 [Tipy pro ladění vláken v nativním kódu](../debugger/tips-for-debugging-threads-in-native-code.md) Jednoduché techniky, které mohou být užitečné pro ladění nativních vláken.

 [Používání okna úlohy](../debugger/using-the-tasks-window.md) Zobrazuje seznam všech spravovaných a nativních objektů úloh, včetně jejich stavu a dalších užitečných informací.

 [Použití okna Paralelní zásobníky](../debugger/using-the-parallel-stacks-window.md) Zobrazuje zásobníky volání s více vlákny (nebo úkoly) v jednom zobrazení a také spojí hodnotu segmenty zásobníku, které jsou společné mezi vlákny (nebo úkoly).

 [Návod: ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md) Návod, který ukazuje, jak používat okna paralelních úkolů a paralelních zásobníků.

 [Postupy: použití okna paralelního sledování](../debugger/how-to-use-the-parallel-watch-window.md) Zkontrolujte hodnoty a výrazy napříč více vlákny.

 [Postupy: použití okna vláken GPU](../debugger/how-to-use-the-gpu-threads-window.md) Prověřte a pracujte s vlákny, která běží na GPU během ladění.

## <a name="related-sections"></a>Související oddíly

[Použití zarážek](../debugger/using-breakpoints.md)
- Použijte filtry zarážek, pokud chcete umístit zarážku na jednotlivá vlákna.

- Trasováním vám umožní trasovat provádění programu bez přerušení. To může být užitečné pro zkoumání problémů, jako je například zablokování.

  [Dělení na vlákna](https://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) Koncepce dělení na vlákna v [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] programování, včetně příkladu kódu.

  [Multithreading v součástech](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) Jak používat multithreading v [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] komponentách.

  [Podpora multithreadingu pro starší kód (Visual C++)](https://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) Koncepty a příklady kódu pro programátory v jazyce C++ pomocí knihovny MFC.

## <a name="see-also"></a>Viz také
 [Ladění vláken a procesů](../debugger/debug-threads-and-processes.md) [vzdálené ladění](../debugger/remote-debugging.md)
