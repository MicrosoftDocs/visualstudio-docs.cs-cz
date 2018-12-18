---
title: Vypočítat metriky kódu
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b56db0d54e198e0d6d25b19db528ac979a3d44b4
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056769"
---
# <a name="code-metrics-values"></a>Hodnoty metrik kódu

Zvýšení složitosti moderních aplikací také zvyšuje obtížnost zobecnění kódu, spolehlivé a udržovatelný. Metriky kódu je sada softwarových opatření, která vývojářům poskytují lepší přehled o kódu, který že vyvíjí. S využitím metrik kódu, vývojáři můžete pochopit, jaké typy nebo metody by měly být přepracována nebo více důkladně otestovali. Vývojové týmy můžete identifikovat potenciální rizika, porozumět aktuálnímu stavu projektu a sledování průběhu během vývoje softwaru.

Vývojářům můžete použít Visual Studio k vygenerování dat metrik kódu, který měření složitosti a udržovatelnosti spravovaného kódu. Daty metrik kódu je vygenerovat pro celé řešení nebo jednoho projektu.

Informace o tom, jak vygenerování dat metrik kódu v sadě Visual Studio najdete v tématu [postupy: vygenerování dat metrik kódu](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Měření softwaru

Následující seznam uvádí kód výsledků metrik, které vypočítá sady Visual Studio:

- **Index udržovatelnosti** – vypočítá hodnotu indexu 0 až 100, který představuje relativní snadností údržbu kódu. Vysoká hodnota znamená vyšší udržovatelnosti. Barevně odlišeny hodnocení je možné rychle identifikovat míst v kódu. Zelená hodnocení je 20 až 100 a označuje, že kód je dobrou udržovatelnost. Žlutý hodnocení je od 10 do 19 a označuje, že je mírně udržovatelný kód. Červené hodnocení je hodnocení 0 až 9 a označuje nízkou udržovatelnost.

- **Cyklomatická složitost** – měří strukturální složitost kódu. Vytvoří se to vynásobením počtu odlišný kód cest v toku programu. Program, který se má komplexní řízení toku bude vyžadovat další testů k dosažení dobré kód pokrytí a bude méně udržovatelný.

- **Hloubka dědičnosti** -určuje počet definice tříd, které rozšiřují do kořene hierarchie tříd. Čím hlouběji v hierarchii více obtížné pochopit, kde jsou definovány konkrétní metody a pole může být nebo / a Předefinovaná.

- **Třída párování** – měří párování na jedinečné třídy prostřednictvím parametrů, místní proměnné, návratové typy, volání metod, vytváření instancí obecného nebo šablony, základní třídy, implementací rozhraní, polí definovaných pro externí typy, a atribut dekorace. Software dobrý návrh přikazuje, typy a metody by měly mít vysokou soudržnost a nízkou párování. Vysoká párování označuje návrh, který je obtížné opakovaně používat a spravovat z důvodu jeho mnoho vzájemných závislostí na jiné typy.

- **Řádky kódu** -určuje přibližný počet řádků v kódu. Počet je založena na kód IL a není proto přesný počet řádků v souboru se zdrojovým kódem. Velmi vysoký počet může znamenat, že typ nebo metoda se pokouší příliš mnoho práce a by měl být rozdělení. Může také znamenat, že tento typ nebo metoda může být obtížné spravovat.

   > [!NOTE]
   > [Příkazového řádku verze](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) nástroj metriky kódu počítá skutečné řádky kódu, protože analyzuje zdrojový kód namísto IL.

## <a name="anonymous-methods"></a>Anonymní metody

*Anonymní metoda* je právě metodu, která nemá žádný název. Anonymní metody se nejčastěji používají k předání bloku kódu jako parametr delegátu. Výsledky metrik pro anonymní metody, která je deklarována v členu, například metoda nebo přístupový objekt, jsou spojeny s člena, který deklaruje metodu. Nejsou přidružené člena, který volá metodu.

Další informace o způsobu metriky kódu s anonymními metodami najdete v tématu [anonymní metody a analýza kódu](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Generovaný kód

Některé softwarové nástroje, kompilátory generují kód, který se přidá do projektu a že pro vývojáře projekt nezobrazí nebo by neměly měnit. Metriky kódu, většinou ignoruje generovaného kódu při výpočtu hodnoty metrik. To umožňuje hodnoty metrik tak, aby odrážely co může vývojář zobrazit a měnit.

Kód generovaný pro model Windows Forms není ignorována, protože je kód, který se může zobrazit a měnit vývojáře.

## <a name="next-steps"></a>Další kroky

- [Postupy: vygenerování dat metrik kódu](../code-quality/how-to-generate-code-metrics-data.md)
- [Použijte okno výsledků metrik kódu](../code-quality/working-with-code-metrics-data.md)