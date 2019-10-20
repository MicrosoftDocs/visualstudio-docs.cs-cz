---
title: Meze průzkumu | Nástroj Microsoft IntelliTest Developer test Tool
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: f6b29b8bc2a9755f5f2e2ced237a5a1ce6acfd6e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653229"
---
# <a name="exploration-bounds"></a>Hranice průzkumu

**PexSettingsAttributeBase** je abstraktní základní třída pro nastavení, která je vázaná jako atributy. Přehled nastavení v IntelliTest najdete v tématu [Nastavení vodopádu](settings-waterfall.md) .

Můžete upravit nastavení pomocí pojmenovaných vlastností tohoto a odvozených atributů:

```csharp
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Rozsahy řešení omezení**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime) – počet sekund, po které má [Řešitel omezení](input-generation.md#constraint-solver) zjistit vstupy, které způsobí, že se budou dodržovat nové a jiné cesty spuštění.
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory) – velikost v megabajtech, kterou může [Řešitel omezení](input-generation.md#constraint-solver) použít ke zjištění vstupů.
* **Meze cesty průzkumu**
  * [MaxBranches](#maxbranches) – maximální počet větví, které mohou být provedeny společně s jednou cestou spuštění.
  * [MaxCalls](#maxcalls) – maximální počet volání, která lze provést během jedné cesty spuštění.
  * [MaxStack](#maxstack) – maximální velikost zásobníku v jednom okamžiku v rámci jedné cesty spuštění, měřená jako počet aktivních rámců volání.
  * [MaxConditions](#maxconditions) – maximální počet podmínek nad vstupy, které mohou být kontrolovány během jedné cesty spuštění.
* **Meze průzkumu**
  * [MaxRuns](#maxruns) – maximální počet spuštění, který se bude zkoušet během průzkumu.
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests) – maximální počet po sobě jdoucích běhů bez nového vygenerování testu.
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths) – maximální počet spuštění s jedinečnými cestami spuštění, které se budou zkoušet během průzkumu.
  * [MaxExceptions](#maxexceptions) – maximální počet výjimek, které mohou být nalezeny pro kombinaci všech zjištěných cest spuštění.
* **Nastavení generování kódu sady testů**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded) – při hodnotě true se budou ignorovat cesty spuštění, které překračují jakékoli hranice cesty ([MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [MaxConditions](#maxconditions)).
  * [TestEmissionFilter](#testemissionfilter) – určuje, za jakých okolností by IntelliTest měla generovat testy.
  * [TestEmissionBranchHits](#testemissionbranchhits) – určuje, kolik testů IntelliTest emituje.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

Doba v sekundách, po kterou má [Řešitel omezení](input-generation.md#constraint-solver) vypočítat vstupy, které způsobí, že bude provedena nová a jiná cesta spuštění. Jedná se o možnost **PexSettingsAttributeBase** a jeho odvozených typů.

Hlubší, co IntelliTest zkoumá cesty provádění programu, složitější systémy omezení, které IntelliTest sestavuje z toku řízení a toku dat programu. V závislosti na časovém limitu můžete nastavit tuto hodnotu tak, aby IntelliTest mohla trvat více nebo méně času a zjišťovat nové cesty provádění.

Většinou je důvodem, že se IntelliTest pokouší najít řešení pro systém omezení, který nemá řešení, ale neví o této skutečnosti. Vzhledem k tomu, že se jedná o Nejběžnější případ časového limitu, nemusí mít smysl zvýšit vazbu.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

Počet megabajtů, které [Řešitel omezení](input-generation.md#constraint-solver) má vypočítat vstupy, které způsobí, že bude provedena nová a jiná cesta spuštění. Jedná se o možnost *PexSettingsAttributeBase** a jeho odvozených typů.

Hlubší IntelliTest prozkoumá cesty provádění programu, složitější systémy omezení, které IntelliTest sestavuje z toku řízení a toku dat programu. V závislosti na paměti, kterou máte v počítači k dispozici, můžete nastavit tuto hodnotu tak, aby IntelliTest mohla řešit složitější systémy omezení.

Většinou je důvodem, že se IntelliTest pokouší najít řešení pro systém omezení, který nemá řešení, ale neví o této skutečnosti. Vzhledem k tomu, že se jedná o nejběžnější příčinu nedostatku paměti, nemusí mít smysl zvýšit vazbu.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

Maximální počet větví, které mohou být provedeny společně s jednou cestou spuštění.

Motivace za tímto vázaným průzkumem slouží k omezení délky prováděcí cesty, kterou IntelliTest prozkoumat během [vytváření vstupu](input-generation.md). Konkrétně brání tomu, aby IntelliTest přestane reagovat, pokud se program dostane do nekonečné smyčky.

Každou podmíněnou a nepodmínkovou větev spouštěného a monitorovaného kódu se započítávají do tohoto limitu, včetně větví, které nezávisí na vstupech parametrizovaného testu.

Například následující kód spotřebovává větve v pořadí 100:

```csharp
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

Maximální počet volání, která lze provést během jedné cesty spuštění.

Motivace za tímto vázaným průzkumem slouží k omezení délky prováděcí cesty, kterou IntelliTest prozkoumat během [vytváření vstupu](input-generation.md). Konkrétně brání tomu, aby IntelliTest přestane reagovat, pokud program zavolá metodu rekurzivně nekonečným počtem výskytů, což by způsobilo přetečení zásobníku, ze kterého IntelliTest nemůže provést obnovení.

Každé volání (přímý, nepřímý, virtuální, skok) spouštěného a monitorovaného kódu se započítává do tohoto limitu.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

Maximální velikost zásobníku kdykoli během jedné cesty spuštění, měřená počtem aktivních rámců volání.

Motivace za tímto vázaným průzkumem slouží k omezení velikosti zásobníku všech cest spuštění, které IntelliTest prozkoumat během [vytváření vstupu](input-generation.md). Konkrétně zabrání IntelliTest v používání veškerého dostupného místa v zásobníku, což by způsobilo přetečení zásobníku, ze kterého IntelliTest nemůže provést obnovení.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

Emaximum počet podmínek nad vstupy, které mohou být zkontrolovány během jedné cesty spuštění.

Motivace za tímto vázaným průzkumem slouží k omezení složitosti každé cesty spuštění, kterou IntelliTest prozkoumává při [vytváření vstupu](input-generation.md). Každou podmíněnou větev, která závisí na vstupech parametrizovaného testu, se počítá vůči tomuto limitu.

Například každá cesta v následujícím kódu spotřebovává n + 1 podmínky:

```csharp
[PexMethod]
void ParameterizedTest(int n)
{
     for (int i=0; i<n; i++) { // conditions are "0<n", "1<n", ..., "!(n<n)"
          ...
     }
     for (int i=0; i<100; i++) { // irrelevant for MaxConditions, since conditions do not depend on input
          ...
     }
}
```

<a name="maxruns"></a>
## <a name="maxruns"></a>MaxRuns

Emaximum počet spuštění, které se IntelliTest pokusí během průzkumu testu.

Motivace za tímto vázaným průzkumem je, že jakýkoli kód, který obsahuje smyčky nebo rekurzi, může mít neomezený počet cest spuštění, a proto musí být IntelliTest při [vytváření vstupu](input-generation.md)omezen.

Tato dvě nastavení **MaxRuns** a **MaxRunsWithUniquePaths** jsou spojená následujícím způsobem:

* IntelliTest bude volat parametrizovanou testovací metodu až do **MaxRuns** časů s různými testovacími vstupy.
* Pokud je spuštěný Kód deterministický, IntelliTest pokaždé pokaždé, když bude pokaždé trvat jinou cestu spuštění. Za určitých podmínek však může spuštěný Kód následovat po spuštění, které již bylo dříve provedeno, s různými vstupy.
* IntelliTest počítá, kolik jedinečných cest provádění najde; Toto číslo je omezené možností **MaxRunsWithUniquePaths** .

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

Maximální počet po sobě jdoucích spuštění bez vygenerování nového testu.

I když IntelliTest může často najít mnoho zajímavých testovacích vstupů v krátkém čase, po době, kdy se nenaleznou žádné další nové testovací vstupy a nevygeneruje žádné další testy jednotek. Tato možnost konfigurace umístí meze na počet po sobě jdoucích pokusů, které IntelliTest může provést bez vygenerování nového testu. Po dosažení se průzkum zastaví.

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

Maximální počet jedinečných cest, které IntelliTest bude během průzkumu brát v úvahu.

Motivace za tímto vázaným průzkumem je, že jakýkoli kód obsahující smyčky nebo rekurzi může mít neomezený počet cest spuštění, a proto musí být IntelliTest během [generování vstupu](input-generation.md)omezen.

Tato dvě nastavení **MaxRuns** a **MaxRunsWithUniquePaths** jsou spojená následujícím způsobem:

* IntelliTest bude volat parametrizovanou testovací metodu až do **MaxRuns** časů s různými testovacími vstupy.
* Pokud je spuštěný Kód deterministický, IntelliTest pokaždé pokaždé, když bude pokaždé trvat jinou cestu spuštění. Za určitých podmínek však může spuštěný Kód následovat po spuštění, které již bylo dříve provedeno, s různými vstupy.
* IntelliTest počítá, kolik jedinečných cest provádění najde; Toto číslo je omezené možností **MaxRunsWithUniquePaths** .

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

Maximální počet výjimek, které mohou být zjištěny před zastavením průzkumu.

Motivace za touto vazbou průzkumu je zastavit zkoumání kódu, který obsahuje mnoho chyb. Pokud IntelliTest najde v kódu příliš mnoho chyb, průzkum se zastaví.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

Cesty spuštění, které překračují nakonfigurovanou cestu [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack)a [MaxConditions](#maxconditions) , se ignorují.

Motivace za tímto vázaným průzkumem slouží k tomu, aby se jednalo o (nejpravděpodobnější) neukončující testy. Když IntelliTest dosáhne hranice průzkumu, jako je [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack)nebo [MaxConditions](#maxconditions), předpokládá, že test nebude neukončující proces a nebude přetečení zásobníku později. Takové testovací případy mohou představovat problémy s jinými testovacími rozhraními a tento atribut poskytuje způsob, jak zabránit IntelliTest v generování testovacích případů pro potenciálně neukončující procesy nebo testovací případy, které způsobí přetečení zásobníku.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

Určuje typy testů, které by měl IntelliTest generovat. Možné hodnoty jsou:

* **Vše** – vygeneruje testy pro všechno, včetně porušení předpokladů.
* **FailuresAndIncreasedBranchHits** (výchozí) – vygeneruje testy pro všechny jedinečné chyby a pokaždé, když testovací případ zvyšuje pokrytí, jak je řízeno [TestEmissionBranchHits](#testemissionbranchhits).
* **FailuresAndUniquePaths** – vygeneruje testy pro všechny chyby, které IntelliTest najde, a také pro každý vstup testu, který způsobí jedinečnou cestu spuštění.
* **Chyby** – vygenerují testy jenom pro selhání.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

V závislosti na aktuálním nastavení [TestEmissionFilter](#testemissionfilter) IntelliTest emituje nové testovací případy, když pokrývají větev v programu, na který se nezabývá.

Nastavení **TestEmissionBranchHits** určuje, zda má IntelliTest přesně zvážit, zda byla větev pokryta vůbec (**TestEmissionBranchHits = 1**), pokud se test pokryje buď jednou, nebo dvakrát (**TestEmissionBranchHits = 2**), a tak dále.

**TestEmissionBranchHits = 1** vytvoří velmi malou testovací sadu, která bude pokrývat všechny větve, které IntelliTest může dosáhnout. Konkrétně tato sada testů bude pokrývat také všechny základní bloky a příkazy, které byly dosaženy.

Výchozí hodnota pro tuto možnost je **TestEmissionBranchHits = 2**, která generuje pokročilejší testovací sadu, která je také lépe vhodná pro detekci budoucích chyb regrese.

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Publikujte své nápady a žádosti o funkce na [komunitě vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
