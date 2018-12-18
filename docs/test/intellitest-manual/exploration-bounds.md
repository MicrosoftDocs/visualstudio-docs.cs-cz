---
title: Hranice průzkumu | Nástroj pro testování Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9d1ac08a2314119c924417191ca509a4bcd18021
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000650"
---
# <a name="exploration-bounds"></a>Hranice průzkumu

**PexSettingsAttributeBase** je abstraktní základní třída pro nastavení hranice jako atributy. Zobrazit [Vodopádové nastavení](settings-waterfall.md) přehledné informace o nastavení Intellitestu.

Nastavení můžete upravit pomocí s názvem vlastnosti tohoto a jeho odvozené atributy:

```csharp
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Omezení řešení hranice**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime) -počet sekund [Řešitel omezení](input-generation.md#constraint-solver) má ke zjištění vstupy, které způsobí, že cesta nová a také různé provedení postupovat.
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory) – velikost v megabajtech, který [Řešitel omezení](input-generation.md#constraint-solver) může použít ke zjištění vstupy.<p />
* **Cesta hranice průzkumu**
  * [MaxBranches](#maxbranches) – maximální počet větví, které mohou být přijata cestě jedno provedení.
  * [MaxCalls](#maxcalls) – maximální počet volání, které mohou být provedeny během spuštění jednu cestu.
  * [MaxStack](#maxstack) – maximální velikost zásobníku kdykoli během spuštění jednu cestu, měřeno jako počet rámců aktivního volání.
  * [MaxConditions](#maxconditions) – maximální počet podmínek přes vstupy, které může kontrolován během spuštění jednu cestu.<p />
* **Hranice průzkumu**
  * [MaxRuns](#maxruns) – maximální počet běhů, které se provedou při vysvětlení.
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests) – maximální počet po sobě jdoucích spuštění bez nového testu probíhá emitovány.
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths) – maximální počet spuštění pomocí cesty jedinečný spuštění, které se provedou při vysvětlení.
  * [MaxExceptions](#maxexceptions) – maximální počet výjimek nalezené pro kombinaci všechny zjištěné provádění cesty.<p />
* **Nastavení generování kódu sady testů**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded) -případě hodnoty true, cesty spuštění, které žádné hranice cesty překročí ([MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [ MaxConditions](#maxconditions)) jsou ignorovány.
  * [TestEmissionFilter](#testemissionfilter) – Určuje, za jakých podmínek by měly vydávat IntelliTest testy.
  * [TestEmissionBranchHits](#testemissionbranchhits) – Určuje, kolik testů IntelliTest vydává.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

Počet sekund [Řešitel omezení](input-generation.md#constraint-solver) má vypočítat vstupy, které způsobí spuštění nové a jiné cesty mají být provedeny. To je jednou z možností **PexSettingsAttributeBase** a jeho odvozených typů.

Čím hlouběji této IntelliTest zkoumá cesty spuštění programu, tím složitější stát omezení systémy, které navazuje IntelliTest v toku řízení a toku dat programu. V závislosti na vaší časové omezení můžete nastavit tato hodnota umožňuje IntelliTest se víc nebo míň času cesty zjišťování nové spuštění.

Obvykle důvodem pro vypršení časového limitu je, že IntelliTest se pokouší vyhledat řešení systému omezení, který nemá žádné řešení, ale nemá žádné informace o této skutečnosti. Protože je to nejběžnější případ pro vypršení časového limitu, nemusí mít smysl pro zvýšení je mez.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

V megabajtech, který [Řešitel omezení](input-generation.md#constraint-solver) má vypočítat vstupy, které způsobí spuštění nové a jiné cesty mají být provedeny. To je jednou z možností *PexSettingsAttributeBase** a jeho odvozených typů.

Hlubší IntelliTest se věnuje cesty spuštění programu, tím složitější stát omezení systémy, které navazuje IntelliTest v toku řízení a toku dat programu. V závislosti na dostupné paměti v počítači můžete nastavit tato hodnota umožňuje IntelliTest řešit složitějších systémech omezení.

Obvykle důvodem pro vypršení časového limitu je, že IntelliTest se pokouší vyhledat řešení systému omezení, který nemá žádné řešení, ale nemá žádné informace o této skutečnosti. Protože toto je nejčastější příčinou situaci na více instancí z důvodu nedostatku paměti, nemusí mít smysl pro zvýšení je mez.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

Maximální počet větví, které mohou být přijata cestě jedno provedení.

Motivace za tento průzkum vázán je omezit délka všechny cesty spuštění, který vám umožní prozkoumat IntelliTest během [vstup generování](input-generation.md). Zabraňuje především IntelliTest přestává reagovat, pokud program přejde do nekonečné smyčky.

Každá větev nepodmíněnou a podmíněné kód spuštěný a monitorované se započítává tento limit, včetně větví, které nezávisí na vstupy parametrizovaný test.

Například následující kód využívá větví v pořadí 100:

```csharp
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

Maximální počet volání, které mohou být provedeny během spuštění jednu cestu.

Motivace za tento průzkum vázán je omezit délka všechny cesty spuštění, který vám umožní prozkoumat IntelliTest během [vstup generování](input-generation.md). Zabraňuje především IntelliTest přestává reagovat, pokud program volá rekurzivně metoda neomezený počet dobu, která by způsobila přetečení zásobníku, který IntelliTest nelze obnovit z.

Na toto omezení se počítá každé volání (přímý, nepřímý, virtuální, přechod) spuštěné a monitorované kódu.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

Maximální velikost zásobníku kdykoli během jednoho spuštění cestu, změřit podle počtu snímků aktivního volání.

Motivace za tento průzkum vázán je omezit velikost zásobníku všechny cesty spuštění, která IntelliTest zkoumá během [vstup generování](input-generation.md). Konkrétně se zabrání IntelliTest v používání všechny dostupné zásobníku místa, což by způsobilo přetečení zásobníku, který IntelliTest nelze obnovit z.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

Číslo emaximum podmínky za vstupy, které může kontrolován během spuštění jednu cestu.

Motivace za tento průzkum vázán je omezit složitost žádné spuštění cestu, která IntelliTest zkoumá během [vstup generování](input-generation.md). Na toto omezení se počítá každé podmíněné větvi, která závisí na vstupech parametrizovaný test.

Například každá cesta v následujícím kódu využívá n + 1 podmínky:

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

Tou emaximum počet spuštění, které IntelliTest se pokusí při průzkumu testu.

Motivace za tento průzkum vázán je, že veškerý kód, který bude obsahovat smyčky nebo rekurze může mít libovolný počet cesty spuštění a proto musí být omezený během IntelliTest [vstup generování](input-generation.md).

Dvě nastavení **MaxRuns** a **MaxRunsWithUniquePaths** souvisejí následujícím způsobem:

* IntelliTest se volání metody parametrizovaný test až **MaxRuns** časy s různými testovacími vstupy.
* Pokud je spuštěný kód je deterministická, bude se IntelliTest trvat cestu různých pracovních pokaždé, když. Ale za určitých podmínek spuštěný kód může díky tomuhle cestu k provádění učinil už dřív, a s různými vstupy.
* IntelliTest se počítá počet cesty jedinečný spuštění, které nalezne; Toto číslo je omezena **MaxRunsWithUniquePaths** možnost.

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

Maximální počet po sobě jdoucích spustí se bez nového testu probíhá emitovány.

Zatímco IntelliTest často najdou mnoho zajímavých testovací vstupy během krátké doby, po nějakou dobu, nenajde žádné další nové testovací vstupy a bude generovat žádné další testy jednotek. Tato možnost konfigurace umístí vázaný na počet po sobě jdoucích pokusů, které může provádět IntelliTest bez generování nového testu. Po dosažení zastaví průzkum.

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

Maximální počet jedinečné cesty, které IntelliTest se vezměte v úvahu při vysvětlení.

Motivace za tento průzkum vázán je, že libovolný kód, který obsahuje smyčky nebo rekurzi může mít libovolný počet cesty spuštění a proto musí být omezený během IntelliTest [vstup generování](input-generation.md).

Dvě nastavení **MaxRuns** a **MaxRunsWithUniquePaths** souvisejí následujícím způsobem: 

* IntelliTest se volání metody parametrizovaný test až **MaxRuns** časy s různými testovacími vstupy.
* Pokud je spuštěný kód je deterministická, bude se IntelliTest trvat cestu různých pracovních pokaždé, když. Ale za určitých podmínek spuštěný kód může díky tomuhle cestu k provádění učinil už dřív, a s různými vstupy. 
* IntelliTest se počítá počet cesty jedinečný spuštění, které nalezne; Toto číslo je omezena **MaxRunsWithUniquePaths** možnost.

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

Maximální počet výjimek, může být došlo před zastavit průzkum.

Motivace za tento průzkum vázán, je zastavit průzkum kód, který obsahuje mnoho chyb. Pokud IntelliTest najde příliš mnoho chyb v kódu, je zastavena průzkumu.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

Cesty spuštění, které překračují hranice nakonfigurovaná cesta [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), a [MaxConditions](#maxconditions) jsou ignorovány.

Motivace za tento průzkum vázán je se (pravděpodobně) neukončující testy. Když IntelliTest dosáhne vysvětlení vázaný jako [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), nebo [MaxConditions](#maxconditions), předpokládá že test nebudou nezpůsobí ukončení procesu a později nezpůsobí přetečení zásobníku. Tyto testovací případy mohou představovat problémů do dalších testovacích architektur a tento atribut poskytuje způsob, jak zabránit IntelliTest generování testovacích případů pro potenciálně neukončující procesy nebo testovacích případů, které způsobí přetečení zásobníku.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

Určuje typy testů, které by měly vydávat IntelliTest. Možné hodnoty jsou:

* **Všechny** – generování testů pro vše, včetně předpokladů porušení.
* **FailuresAndIncreasedBranchHits** (výchozí) – generování testů pro všechny jedinečné chyby a vždy, když testovací případ, se prodlužuje pokrytí řídí [TestEmissionBranchHits](#testemissionbranchhits).
* **FailuresAndUniquePaths** – generování testů pro všechny chyby IntelliTest najde, a také pro každou zkušební vstup, který způsobí, že cesta jedinečný provedení.
* **Selhání** – generování testů pro jenom selhání.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

V závislosti na aktuální [TestEmissionFilter](#testemissionfilter) nastavení Intellitestu vydává nové testovací případy při pokrývají větve v programu, který nebyl před zahrnuté.

**TestEmissionBranchHits** nastavení určuje, že pokud IntelliTest právě zvažte, jestli větev zkušebním vůbec (**TestEmissionBranchHits = 1**), pokud se test pokrýt ho jednou nebo dvakrát ( **TestEmissionBranchHits = 2**), a tak dále.

**TestEmissionBranchHits = 1** vytvoří velmi malé sady testů, který se bude vztahovat na všechny větve IntelliTest může kontaktovat. Zejména této sady testů také zahrnuje všechny základní bloky a příkazy, které se dosáhlo.

Výchozí hodnota pro tuto možnost je **TestEmissionBranchHits = 2**, které generují více výrazovými možnostmi testovací sadu, která je také vhodnější vhodné k odhalování chyb budoucí regrese.

## <a name="got-feedback"></a>Máte nějakou zpětnou vazbu?

Publikovat své nápady a funkce na požadavky [komunity vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
