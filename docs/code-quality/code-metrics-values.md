---
title: Vypočítat metriky kódu
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6caf63b2d1fb6b9206fe43da5c7a63818fd299f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587694"
---
# <a name="code-metrics-values"></a>Hodnoty metrik kódu

Zvýšení složitosti moderních aplikací také zvyšuje obtížnost zobecnění kódu, spolehlivé a udržovatelný. Metriky kódu je sada softwarových opatření, která vývojářům poskytují lepší přehled o kódu, který že vyvíjí. S využitím metrik kódu, vývojáři můžete pochopit, jaké typy nebo metody by měly být přepracována nebo více důkladně otestovali. Vývojové týmy můžete identifikovat potenciální rizika, porozumět aktuálnímu stavu projektu a sledování průběhu během vývoje softwaru.

Vývojářům můžete použít Visual Studio k vygenerování dat metrik kódu, který měření složitosti a udržovatelnosti spravovaného kódu. Daty metrik kódu je vygenerovat pro celé řešení nebo jednoho projektu.

Informace o tom, jak vygenerování dat metrik kódu v sadě Visual Studio najdete v tématu [postupy: vygenerování dat metrik kódu](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Měření softwaru

Následující seznam uvádí kód výsledků metrik, které vypočítá sady Visual Studio:

- **Index udržovatelnosti** – vypočítá hodnotu indexu 0 až 100, který představuje relativní snadností údržbu kódu. Vysoká hodnota znamená vyšší udržovatelnosti. Barevně odlišeny hodnocení je možné rychle identifikovat míst v kódu. Zelená hodnocení je 20 až 100 a označuje, že kód je dobrou udržovatelnost. Žlutý hodnocení je od 10 do 19 a označuje, že je mírně udržovatelný kód. Červené hodnocení je hodnocení 0 až 9 a označuje nízkou udržovatelnost. Další informace najdete v tématu [Rozsah indexu udržovatelnosti a význam](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/) příspěvku na blogu.

- **Cyklomatická složitost** – měří strukturální složitost kódu. Vytvoří se to vynásobením počtu odlišný kód cest v toku programu. Program, který má složitý tok řízení, vyžaduje více testů pro dosažení dobrého pokrytí kódu a je méně udržovatelný. Další informace najdete v [záznamu Wikipedii pro Cyklomatická složitost](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Hloubka dědičnosti** – určuje počet různých tříd, které dědí od sebe, až po zpět k základní třídě. Hloubka dědičnosti je podobná párování tříd v tom, že změna základní třídy může ovlivnit jakoukoli z jeho zděděných tříd. Čím vyšší je toto číslo, tím hlubší je dědění a čím vyšší je potenciál u úprav základní třídy za následek zásadní změnu. Pro hloubku dědičnosti je nízká hodnota dobrá a vysoká hodnota je špatná.

- **Třída párování** – měří párování na jedinečné třídy prostřednictvím parametrů, místní proměnné, návratové typy, volání metod, vytváření instancí obecného nebo šablony, základní třídy, implementací rozhraní, polí definovaných pro externí typy, a atribut dekorace. Software dobrý návrh přikazuje, typy a metody by měly mít vysokou soudržnost a nízkou párování. Vysoká párování označuje návrh, který je obtížné opakovaně používat a spravovat z důvodu jeho mnoho vzájemných závislostí na jiné typy. Další informace najdete v příspěvku na blogu ke [třídě](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/) .

- **Řádky kódu** -určuje přibližný počet řádků v kódu. Počet je založena na kód IL a není proto přesný počet řádků v souboru se zdrojovým kódem. Vysoký počet může ukazovat, že typ nebo metoda se snaží provést příliš mnoho práce a měla by být rozdělena. Může také znamenat, že tento typ nebo metoda může být obtížné spravovat.

   > [!NOTE]
   > [Příkazového řádku verze](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) nástroj metriky kódu počítá skutečné řádky kódu, protože analyzuje zdrojový kód namísto IL.

## <a name="anonymous-methods"></a>Anonymní metody

*Anonymní metoda* je právě metodu, která nemá žádný název. Anonymní metody se nejčastěji používají k předání bloku kódu jako parametr delegátu. Výsledky metrik kódu pro anonymní metodu, která je deklarována v členu, jako je například metoda nebo přistupující objekt, je přidružena ke členu, který deklaruje metodu. Nejsou přidružené člena, který volá metodu.

## <a name="generated-code"></a>Generovaný kód

Některé softwarové nástroje, kompilátory generují kód, který se přidá do projektu a že pro vývojáře projekt nezobrazí nebo by neměly měnit. Metriky kódu, většinou ignoruje generovaného kódu při výpočtu hodnoty metrik. To umožňuje hodnoty metrik tak, aby odrážely co může vývojář zobrazit a měnit.

Kód generovaný pro model Windows Forms není ignorována, protože je kód, který se může zobrazit a měnit vývojáře.

## <a name="next-steps"></a>Další kroky

- [Postupy: vygenerování dat metrik kódu](../code-quality/how-to-generate-code-metrics-data.md)
- [Použijte okno výsledků metrik kódu](../code-quality/working-with-code-metrics-data.md)
