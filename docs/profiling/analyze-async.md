---
title: Analýza výkonu asynchronního kódu .NET | Microsoft Docs
description: Použijte nástroj .NET Async k analýze výkonu asynchronního kódu. Pro každý uvedený úkol existuje časování. Chcete-li zobrazit kód, použijte příkaz Přejít ke zdrojovému souboru.
ms.custom: SEO-VS-2020
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- asynchronous, async, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 86575cd71c41ac8ac874e9b62f8273ee46e02c57
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205486"
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