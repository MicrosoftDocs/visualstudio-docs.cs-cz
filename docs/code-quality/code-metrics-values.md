---
title: Vypočítat metriky kódu
ms.date: 11/02/2018
description: Přečtěte si o složitosti cyklomatická, párování tříd a dalších metrikách kódu sady Visual Studio. Podívejte se, jak metriky můžou sledovat průběh vývoje a identifikovat rizika.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.codemetrics.toolwindow
dev_langs:
- CSharp
- VB
- FSharp
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e77667feae806b66092195f30b028ccca653b2b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860448"
---
# <a name="code-metrics-values"></a>Hodnoty metrik kódu

Zvýšená složitost moderních softwarových aplikací také zvyšuje obtížnost zajištění spolehlivého a udržovatelného kódu. Metriky kódu jsou sada softwarových opatření, která vývojářům poskytují lepší přehled o kódu, který vyvíjí. Díky využití metrik kódu můžou vývojáři pochopit, které typy a metody by se měly přepracovat nebo podrobně testovat. Vývojové týmy můžou identifikovat potenciální rizika, pochopit aktuální stav projektu a sledovat průběh během vývoje softwaru.

Vývojáři mohou použít sadu Visual Studio k vygenerování dat metrik kódu, které měří složitost a udržovatelnost jejich spravovaného kódu. Data metrik kódu je možné vygenerovat pro celé řešení nebo pro jeden projekt.

Informace o tom, jak generovat data metrik kódu v aplikaci Visual Studio, naleznete v tématu [How to: Generate data metriky Code](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Měření softwaru

V následujícím seznamu jsou uvedeny výsledky metrik kódu, které Visual Studio vypočítá:

- **Index udržovatelnosti** – vypočítá hodnotu indexu mezi 0 a 100, která představuje relativní snadné udržování kódu. Vysoká hodnota znamená lepší udržovatelnost. Barevná hodnocení lze použít k rychlé identifikaci problémů v kódu. Zelené hodnocení je mezi 20 a 100 a indikuje, že kód má dobrou udržovatelnost. Žluté hodnocení je mezi 10 a 19 a označuje, že je kód moderovanější. Červené hodnocení je hodnocení mezi 0 a 9 a označuje nízkou udržovatelnost. Další informace najdete v tématu [Rozsah indexů údržby a význam](code-metrics-maintainability-index-range-and-meaning.md).

- **Cyklomatická složitosti** – měří strukturální složitost kódu. Vytvoří se tak, že se vypočítává počet různých cest kódu v toku programu. Program, který má složitý tok řízení, vyžaduje více testů pro dosažení dobrého pokrytí kódu a je méně udržovatelný. Další informace najdete v [záznamu Wikipedii pro Cyklomatická složitost](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Hloubka dědičnosti** – určuje počet různých tříd, které dědí od sebe, až po zpět k základní třídě. Hloubka dědičnosti je podobná párování tříd v tom, že změna základní třídy může ovlivnit jakoukoli z jeho zděděných tříd. Čím vyšší je toto číslo, tím hlubší je dědění a čím vyšší je potenciál u úprav základní třídy za následek zásadní změnu. Pro hloubku dědičnosti je nízká hodnota dobrá a vysoká hodnota je špatná.

- **Párování tříd** – měří připojení k jedinečným třídám prostřednictvím parametrů, místních proměnných, návratových typů, volání metod, obecných nebo šablonových instancí, základních tříd, implementací rozhraní, polí definovaných pro externí typy a dekorace atributů. Dobrý návrh softwaru určuje, že typy a metody by měly mít vysokou soudržnost a malý spoj. Vysoké propojení indikuje návrh, který je obtížné znovu použít a udržovat z důvodu jeho mnoha vzájemných závislostí na jiných typech. Další informace najdete v tématu [párování tříd](code-metrics-class-coupling.md).

::: moniker range=">=vs-2019"

- **Řádky zdrojového kódu** – označuje přesný počet řádků zdrojového kódu, které jsou přítomny ve zdrojovém souboru, včetně prázdných řádků. Tato metrika je k dispozici počínaje verzí Visual Studio 2019 verze 16,4 a Microsoft. CodeAnalysis. Metrics (2.9.5).

- **Řádky spustitelného kódu** – označuje přibližný počet spustitelných řádků kódu nebo operací. Toto je počet operací ve spustitelném kódu. Tato metrika je k dispozici počínaje verzí Visual Studio 2019 verze 16,4 a Microsoft. CodeAnalysis. Metrics (2.9.5). Hodnota je obvykle blízkou shodu s předchozí metrikou, **řádky kódu**, což je metrika založená na INSTRUKCÍCH jazyka MSIL použitá v režimu starší verze.
::: moniker-end
::: moniker range="vs-2017"

- **Řádky kódu** – označuje přibližný počet řádků v kódu. Počet je založen na kódu IL a není tak přesný počet řádků v souboru zdrojového kódu. Vysoký počet může ukazovat, že typ nebo metoda se snaží provést příliš mnoho práce a měla by být rozdělena. Může také indikovat, že typ nebo metoda může být obtížné udržovat.

   > [!NOTE]
   > [Verze příkazového řádku](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) nástroje metriky kódu počítá skutečné řádky kódu, protože analyzuje zdrojový kód místo Il.
::: moniker-end

## <a name="anonymous-methods"></a>Anonymní metody

*Anonymní metoda* je pouze metoda, která nemá žádný název. Anonymní metody se nejčastěji používají k předání bloku kódu jako parametru delegáta. Výsledky metrik kódu pro anonymní metodu, která je deklarována v členu, jako je například metoda nebo přistupující objekt, je přidružena ke členu, který deklaruje metodu. Nejsou přidruženy ke členu, který volá metodu.

## <a name="generated-code"></a>Generovaný kód

Některé softwarové nástroje a kompilátory generují kód, který je přidán do projektu a který vývojář projektu buď nevidí, nebo by neměl být změněn. Ve většině případů metriky kódu ignorují generovaný kód při výpočtu hodnot metrik. To umožňuje hodnotám metriky odrážet, co může vývojář zobrazit a změnit.

Kód vygenerovaný pro model Windows Forms není ignorován, protože se jedná o kód, který může vývojář zobrazit a změnit.

## <a name="next-steps"></a>Další kroky

- [Postupy: generování dat metrik kódu](../code-quality/how-to-generate-code-metrics-data.md)
- [Použití okna výsledků metrik kódu](../code-quality/working-with-code-metrics-data.md)