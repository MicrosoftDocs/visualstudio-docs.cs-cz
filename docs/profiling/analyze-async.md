---
title: Analýza výkonu asynchronního kódu .NET | Microsoft Docs
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- asynchronous, async, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: e6f690b77b7e573fdf1c54fdaeca6237c6bbc146
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037540"
---
# <a name="analyze-performance-of-net-asynchronous-code"></a>Analýza výkonu asynchronního kódu .NET

Použijte nástroj .NET Async k analýze výkonu asynchronního kódu ve vaší aplikaci.

> [!NOTE]
> Nástroj .NET Async vyžaduje Visual Studio 2019 verze 16,7 nebo novější a projekt .NET, který používá **Async** a **await**.

## <a name="setup"></a>Nastavení

1. Kliknutím na **ALT + F2** otevřete Profiler výkonu v aplikaci Visual Studio.

1. Zaškrtněte políčko **.NET Async** .

   ![Je vybraný .NET Async Tool](../profiling/media/async-tool-selected.png "Je vybraný .NET Async Tool")

1. Kliknutím na tlačítko **Spustit** nástroj spustíte.

1. Po spuštění nástroje si Projděte scénář, který chcete profilovat ve své aplikaci. Pak vyberte **Zastavit shromažďování** nebo zavřít aplikaci, aby se zobrazila vaše data.

1. Po zastavení shromažďování se zobrazí tabulka aktivit, ke kterým došlo během relace profilování.

   ![Asynchronní nástroj .NET se zastavil.](../profiling/media/async-tool-opened.png "Asynchronní nástroj .NET se zastavil.")

Asynchronní události jsou uspořádané do aktivit chronologicky. Každý zobrazuje čas spuštění, čas ukončení a dobu trvání.

Každý řádek, který odpovídá [úkolu](/dotnet/api/system.threading.tasks) , je označený ve sloupci **název** . Pro libovolný název úlohy, který nelze vyřešit, se zobrazí **úkol v** popisku. Následuje název metody, ve které se úkol vyskytuje. Pokud se asynchronní aktivita v rámci relace shromažďování nedokončila, zobrazí se ve sloupci **koncový čas** **neúplný** popisek.

Chcete-li dále prozkoumat konkrétní úkol nebo aktivitu, klikněte na něj pravým tlačítkem. Pak vyberte **Přejít ke zdrojovému souboru** a podívejte se, kde došlo k aktivitě ve vašem kódu.

![.NET Async Tool s vybraným souborem přejít ke zdrojovému souboru](../profiling/media/async-tool-gotosource.png ".NET Async Tool s vybraným souborem přejít ke zdrojovému souboru")

## <a name="see-also"></a>Viz také

- [Optimalizace nastavení profileru](../profiling/optimize-profiler-settings.md)