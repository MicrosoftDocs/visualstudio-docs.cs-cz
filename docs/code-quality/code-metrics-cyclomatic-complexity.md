---
title: Metriky kódu – Cyclomatic complexity
ms.date: 5/7/2021
description: Přečtěte si o metrikě složitosti pro metriky kódu v nástroji Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1798b0faa1b0cf44ae490f5b27571e5466b82ca9
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2021
ms.locfileid: "109682655"
---
# <a name="code-metrics---cyclomatic-complexity"></a>Metriky kódu – Cyclomatic complexity

Při práci s metrikami kódu se zdá, že jedna z nejméně srozumitelných položek je cyklická složitost. S cyclomatickými složitostmi jsou v podstatě vyšší čísla chybná a nižší čísla jsou dobrá. Pomocí cyclomaticky složitého kódu můžete získat přehled o tom, jak obtížné může být testování, údržba nebo řešení potíží s libovolným kódem, a také indikovat, s jakou pravděpodobností bude kód způsobovat chyby. Na nejvyšší úrovni určíme hodnotu cyclomaticky složité složitosti tím, že počítáme počet rozhodnutí provedených ve zdrojovém kódu. V tomto článku začnete jednoduchým příkladem cyclomaticky složitosti, abyste koncept rychle pochopili, a pak se podíváte na další informace o skutečném využití a navrhovaných omezeních. Nakonec je tu část citací, kterou můžete použít k hlubšímu prohloupení tohoto tématu.

## <a name="example"></a>Příklad

Cyclomatic complexity is defined as measuring "the amount of decision logic in a source code function" [NIST235](#nist235). Jednoduše řečeno, čím více rozhodnutí je třeba udělat v kódu, tím složitější je.

Pojďme se na to podívat v akci. Vytvořte novou konzolovou aplikaci a okamžitě vypočítejte metriky kódu tak, že v > **Výpočet metrik kódu pro řešení**.

![Příklad 1 pro cyclomatickou složitost](media/cyclomatic-complexity-example-1.png)

Všimněte si, že kyklidická složitost má hodnotu 2 (nejnižší možná hodnota). Pokud přidáte kód bez rozhodování, všimněte si, že složitost se nemění:

![Příklad 2 pro cyclomatickou složitost](media/cyclomatic-complexity-example-2.png)

Pokud přidáte rozhodnutí, hodnota cyclomatic complexity se zvyšuje o 1:

![Příklad 3 pro cyclomatickou složitost](media/cyclomatic-complexity-example-3.png)

Když změníte příkaz if na příkaz switch se 4 rozhodnutími, která je třeba udělat, přejde z původních 2 na 6:

![Příklad složitosti cyklomatická 4](media/cyclomatic-complexity-example-4.png)

Pojďme se podívat na větší základ kódu (hypotetické).

![Příklad složitosti cyklomatická 5](media/cyclomatic-complexity-example-5.png)

Všimněte si, že většina položek, jak přejít k podrobnostem Products_Related třídy, má hodnotu 1, ale jedna z nich má složitost 5. Sám o sobě to nemusí být velká, ale vzhledem k tomu, že většina dalších členů má 1 ve stejné třídě, byste měli jednoznačně Hledat na těchto dvou položkách a zjistit, co je v nich. To můžete provést tak, že kliknete pravým tlačítkem myši na položku a zvolíte **Přejít ke zdrojovému kódu** z místní nabídky. Podívejte se blíže na `Product.set(Product)` :

![Příklad složitosti cyklomatická 6](media/cyclomatic-complexity-example-6.png)

V případě všech příkazů IF můžete zjistit, proč je složitá cyklomatickáá na 5. V tomto okamžiku se můžete rozhodnout, že jde o přijatelnou úroveň složitosti, nebo můžete Refaktorovat složitost, abyste snížili složitost.

## <a name="the-magic-number"></a>Magic Number

Stejně jako u řady metrik v tomto odvětví neexistuje přesný limit cyklomatická složitosti, který by vyhovoval všem organizacím. [NIST235](#nist235) však indikuje, že limit 10 je dobrým výchozím bodem:

"Přesné číslo, které se má použít jako limit, však zůstává trochu kontroverznímo. Původní limit 10, jak navrhuje McCabe, má významný podpůrný důkaz, ale omezuje se i na maximum, protože se úspěšně používala i hodnota 15. Omezení nad 10 by se měla rezervovat pro projekty, které mají několik provozních výhod oproti typickým projektům, jako jsou například zkušení zaměstnanci, formální návrh, Moderní programovací jazyk, strukturované programování, návody pro kód a komplexní testovací plán. Jinými slovy, organizace může vybrat omezení složitosti větší než 10, ale jenom v případě, že ví, co dělá a je ochotno vyhradit další testovací úsilí vyžadované složitějšími moduly. " [NIST235](#nist235)

## <a name="cyclomatic-complexity-and-line-numbers"></a>Cyklomatická složitost a čísla řádků

Stačí, když přesně prohlížíte počet řádků kódu, a to na nejvyšší úrovni, což je nejlepší pro velmi velký odhad kvality kódu. Existuje několik základních pravdivých informací o tom, že čím více řádků kódu ve funkci je, tím pravděpodobněji dojde k chybám. Pokud ale zkombinujte cyclomatickou složitost s řádky kódu, máte mnohem jasnější přehled o možném chybách.

Jak je popsáno v Software Assurance Technology Center (SATC) v NASA:

"Satc zjistil, že nejefektivnějším vyhodnocením je kombinace velikosti a (cyclomatic) složitosti. Moduly s vysokou složitostí i velkou velikostí mají tendenci mít nejnižší spolehlivost. Moduly s nízkou velikostí a vysokou složitostí jsou také riziko spolehlivosti, protože mají tendenci být velmi odchýlný kód, který se obtížně mění nebo upravuje." [SATC](#satc)

## <a name="code-analysis"></a>analýza kódu

Analýza kódu zahrnuje kategorii Pravidla udržovatelnosti. Další informace najdete v tématu [Pravidla udržovatelnosti.](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings) Při použití starší verze analýzy kódu obsahuje sada pravidel Rozšířené pokyny k návrhu oblast udržovatelnosti:

![Sady pravidel pro cyclomatic complexity design guidelines](media/cyclomatic-complexity-design-guidelines.png)

V oblasti udržovatelnosti je pravidlo pro složitost:

![Pravidlo udržovatelnosti pro cyclomatickou složitost](media/cyclomatic-complexity-maintainability-rule.png)

Toto pravidlo zobrazí upozornění, když cyklická složitost dosáhne hodnoty 25, takže vám pomůže vyhnout se nadměrné složitosti. Další informace o pravidle najdete v tématu [CA1502.](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)

## <a name="putting-it-all-together"></a>Zušli jsme všechno dohromady.

Celkovým číslem je, že vysoké číslo složitosti znamená větší pravděpodobnost chyb s delším časem na údržbu a řešení potíží. Podívejte se blíže na všechny funkce, které mají vysokou složitost, a rozhodněte se, jestli by se měly refaktorovat, aby byly méně složité.

## <a name="citations"></a>Citace

### <a name="mccabe5"></a>MCCABE5

McCabe, T. and A. Watson (1994), Software Complexity (CrossTalk: The Journal of Defense Software Engineering).

### <a name="nist235"></a>NIST235

Watson, A. H., & McCabe, T. J. (1996). Strukturované testování: Metodologie testování s využitím cyclomatic complexity Metric (speciální publikace NIST 500-235). Načteno 14. května 2011 z webu McCabe Software: [http://www.mccabe.com/pdf/mccabe-nist235r.pdf](http://www.mccabe.com/pdf/mccabe-nist235r.pdf)

### <a name="satc"></a>SATC

Rosenberg, L., Automaticky, T., Naž, J. (1998). Software Metrics and Reliability (Proceedings of IEEE International Symposium on Software Reliability Engineering). Načteno 14. května 2011 z webu Nan State University: [http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf)