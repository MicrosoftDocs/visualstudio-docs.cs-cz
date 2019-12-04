---
title: Začínáme s nástroji pro výkon | Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
helpviewer_keywords:
- getting started, performance
- getting started, profiling tools
ms.assetid: 02085214-a8e4-40fd-9b26-32391a7a7082
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: faba7a6d2e698e919c0f0adca6fa574838b8b3c4
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779204"
---
# <a name="getting-started-with-performance-tools"></a>Začínáme s nástroji pro sledování výkonu

Visual Studio nabízí několik způsobů, jak shromažďovat, zobrazovat a analyzovat data o výkonu kódu. V mnoha případech nejlepší způsob, jak začít pracovat s nástroji pro výkon, je použít výchozí nastavení **Průvodce výkonem**. Průvodce shromažďuje statistiku aplikací, které mohou ukazovat na problémy s výkonem ve vašem kódu.

- Upozornění na výkon, která vás upozorňují na běžné problémy s kódováním, se zobrazí v okně Visual Studio **Seznam chyb** . Můžete přejít z upozornění na zdrojový kód a podrobná témata nápovědy, která vám pomohou psát efektivnější kód.

- Sestavy o výkonu poskytují zobrazení na různých úrovních struktury vaší aplikace, řádků zdrojového kódu a procesů. Sestavy o výkonu zobrazují data o spuštění aplikace od volajících a volaných funkcí konkrétní funkce do stromu volání celé aplikace.

Chcete-li rychle vytvořit profil projektu, aplikace nebo webu ASP.NET, vyberte možnost **ladit** > **Performance Profiler**a vyberte **Průvodce výkonem**. Podrobné pokyny najdete v tématu [Příručka pro začátečníky k profilaci výkonu](../profiling/beginners-guide-to-cpu-sampling.md) a [Postupy: shromažďování dat o výkonu pro web](../profiling/how-to-collect-performance-data-for-a-web-site.md).

Pokud chcete ručně zadat a nakonfigurovat relaci profilace výkonu, vyberte **ladit** > **Profiler** > **prohlížeč výkonu**. Ke konfiguraci relací použijte složku **cíle** a stránky **vlastností** v **prohlížeč výkonu** . Pokyny najdete v tématu [Postup: Ruční vytvoření relací výkonu](../profiling/how-to-manually-create-performance-sessions.md).

**Viz také:**

- [Přehledy nástrojů výkonu](../profiling/overviews-performance-tools.md)
- [Analýza dat nástrojů výkonu](../profiling/analyzing-performance-tools-data.md)
- [Použití pravidel výkonu k analýze dat](../profiling/using-performance-rules-to-analyze-data.md)
- [Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md)
