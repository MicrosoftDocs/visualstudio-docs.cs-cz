---
title: Analýza využití databáze pro projekty .NET Core | Microsoft Docs
description: Pomocí databázového nástroje zaznamenejte databázové dotazy vaší aplikace a pak je Analyzujte, abyste našli způsob, jak zvýšit výkon.
ms.custom: SEO-VS-2020
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- database, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: a8518e3f43bec3a9d5f696a07613dee84829dbc2
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205460"
---
# <a name="analyze-database-performance-using-the-database-tool"></a>Analýza výkonu databáze pomocí nástroje Database Tool

Použijte databázový nástroj k záznamu databázových dotazů, které vaše aplikace provede během diagnostické relace. Pak můžete analyzovat informace o jednotlivých dotazech a najít místa pro zlepšení výkonu vaší aplikace.

> [!NOTE]
> Databázový nástroj vyžaduje Visual Studio 2019 verze 16,3 nebo novější a projekt .NET Core ve Windows s použitím [ADO.NET]( https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) nebo [Entity Framework Core](/ef/core/).

## <a name="setup"></a>Nastavení

1. Kliknutím na **ALT + F2** otevřete Profiler výkonu v aplikaci Visual Studio.

1. Zaškrtněte políčko **databáze** .

   ![Vybraný databázový nástroj](./media/db-launch.png "Vybraný databázový nástroj")

   > [!NOTE]
   > Pokud nástroj není k dispozici pro výběr, zrušte zaškrtnutí políčka u všech ostatních nástrojů, protože některé nástroje potřebují spustit samostatně. Další informace o spuštění nástrojů společně najdete v tématu [použití nástrojů pro profilaci z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md).
   >
   > Pokud nástroj stále není k dispozici, ověřte, že projekt splňuje předchozí požadavky. Ujistěte se, že je váš projekt v režimu vydání, aby bylo možné zachytit nejpřesnější data.

1. Kliknutím na tlačítko **Spustit** nástroj spustíte.

1. Po spuštění nástroje si Projděte scénář, který chcete profilovat ve své aplikaci. Pak vyberte **Zastavit shromažďování** nebo zavřít aplikaci, aby se zobrazila vaše data.

1. Po zastavení shromažďování se zobrazí tabulka dotazů, které byly spuštěny během relace profilování.

   ![Databázový nástroj se zastavil.](./media/db-after.png "Databázový nástroj se zastavil.")

Dotazy jsou uspořádány chronologicky, ale můžete je seřadit podle kteréhokoli sloupce. Další sloupce můžete zobrazit tak, že kliknete pravým tlačítkem myši na záhlaví sloupců. Výběr sloupce **Trvání** seřadí dotazy od nejdéle po nejkratší.

Po nalezení dotazu, který chcete prozkoumat, klikněte pravým tlačítkem na dotaz. Pak vyberte **Přejít ke zdrojovému souboru** a podívejte se, jaký kód je zodpovědný za tento dotaz.

![Přejít na vybraný zdrojový soubor](./media/db-gotosource.png "Přejít na vybraný zdrojový soubor")

Pokud v grafu vyberete časový rozsah, v tabulce dotazu se zobrazí pouze dotazy, k nimž došlo během daného časového rozsahu. Toto chování je zvlášť užitečné, když také spustíte [Nástroj využití CPU](./cpu-usage.md?view=vs-2019&preserve-view=true).

## <a name="see-also"></a>Viz také

- [Optimalizace nastavení profileru](../profiling/optimize-profiler-settings.md)