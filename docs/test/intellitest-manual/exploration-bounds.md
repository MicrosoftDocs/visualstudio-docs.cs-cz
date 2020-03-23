---
title: Průzkumné hranice | Testovací nástroj pro vývojáře IntelliTest společnosti Microsoft
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 2a57d79fb64675f90edf50e6a0d7d50b8a3c6fd7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302635"
---
# <a name="exploration-bounds"></a>Hranice průzkumu

**PexSettingsAttributeBase** je abstraktní základní třída pro hranice nastavení jako atributy. Přehled nastavení v IntelliTestu najdete v tématu [Vodopád nastavení.](settings-waterfall.md)

Nastavení můžete upravit pomocí pojmenovaných vlastností tohoto a jeho odvozených atributů:

```csharp
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Hranice řešení omezení**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime) - Počet sekund, po které má [řešič omezení](input-generation.md#constraint-solver) ke zjištění vstupů, které způsobí, že bude následovat nová a jiná cesta spuštění.
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory) - Velikost v megabajtech, kterou může [řešitel omezení](input-generation.md#constraint-solver) použít ke zjišťování vstupů.
* **Hranice průzkumné stezky**
  * [MaxBranches](#maxbranches) - maximální počet větví, které mohou být přijata podél jedné cesty spuštění.
  * [MaxCalls](#maxcalls) - maximální počet volání, které mohou být provedeny během jedné cesty spuštění.
  * [MaxStack](#maxstack) - Maximální velikost zásobníku kdykoli během jedné cesty spuštění, měřeno jako počet aktivních rámců volání.
  * [MaxConditions](#maxconditions) - maximální počet podmínek nad vstupy, které mohou být kontrolovány během jedné cesty spuštění.
* **Hranice průzkumu**
  * [MaxRuns](#maxruns) - maximální počet spuštění, které se pokusí během průzkumu.
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests) - Maximální počet po sobě jdoucích spuštění bez vyzařování nového testu.
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths) - Maximální počet spuštění s jedinečnými cestami spuštění, které budou pokusy během průzkumu.
  * [MaxExceptions](#maxexceptions) - maximální počet výjimek, které mohou být nalezeny pro kombinaci všech zjištěných cest spuštění.
* **Nastavení generování kódu testovací sady**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded) - Pokud true, spuštění cesty, které překračují některou z hranice cesty ([MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [MaxConditions](#maxconditions)) jsou ignorovány.
  * [TestEmissionFilter](#testemissionfilter) - Označuje, za jakých okolností IntelliTest by měl vyzařovat testy.
  * [TestEmissionBranchHits](#testemissionbranchhits) - Určuje, kolik testů IntelliTest vyzařuje.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

Počet sekund, po které má [řešič omezení](input-generation.md#constraint-solver) k výpočtu vstupů, které způsobí, že bude přijata nová a jiná cesta spuštění. Toto je možnost **PexSettingsAttributeBase** a jeho odvozené typy.

Čím hlouběji, že IntelliTest zkoumá cesty spuštění programu, složitější omezení systémy, které IntelliTest staví z řízení toku a tok dat programu stát. V závislosti na časové omezení, můžete nastavit tuto hodnotu povolit IntelliTest trvat více či méně času zjišťování nové cesty spuštění.

Obvykle důvodem pro časový rozsah je, že IntelliTest se pokouší najít řešení pro omezení systému, který nemá řešení, ale není si vědom této skutečnosti. Vzhledem k tomu, že se jedná o nejběžnější případ pro časový čas, nemusí mít smysl zvýšit vazbu.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

Počet megabajtů, které má [řešič omezení](input-generation.md#constraint-solver) k výpočtu vstupů, které způsobí, že bude přijata nová a jiná cesta provádění. Toto je možnost *PexSettingsAttributeBase** a jeho odvozené typy.

Hlubší IntelliTest zkoumá cesty provádění programu, složitější omezení systémy, které IntelliTest staví z řízení toku a tok dat programu stát. V závislosti na dostupné paměti počítače můžete tuto hodnotu nastavit tak, aby intelliTest mohl řešit složitější systémy omezení.

Obvykle důvodem pro časový rozsah je, že IntelliTest se pokouší najít řešení pro omezení systému, který nemá řešení, ale není si vědom této skutečnosti. Vzhledem k tomu, že se jedná o nejčastější příčinu situace nedostatek paměti, nemusí mít smysl zvýšit vazbu.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

Maximální počet větví, které mohou být přijata podél jedné cesty spuštění.

Motivace za tento průzkum vázán je omezit délku jakékoli cesty spuštění, které IntelliTest zkoumá během [generování vstupu](input-generation.md). Zejména zabraňuje IntelliTest od stává neodpovídá, pokud program přejde do nekonečné smyčky.

Každá podmíněná a bezpodmínečná větev provedeného a monitorovaného kódu se započítává do tohoto limitu, včetně větví, které nezávisí na vstupech parametrizovaného testu.

Například následující kód spotřebovává větve v pořadí 100:

```csharp
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

Maximální počet volání, které mohou být provedeny během jedné cesty spuštění.

Motivace za tento průzkum vázán je omezit délku jakékoli cesty spuštění, které IntelliTest zkoumá během [generování vstupu](input-generation.md). Zejména zabraňuje IntelliTest přestane reagovat, pokud program volá metodu rekurzivně nekonečný počet opakování, což by způsobilo přetečení zásobníku, které IntelliTest nelze obnovit.

Každé volání (přímé, nepřímé, virtuální, skok) provedeného a monitorovaného kódu se započítává do tohoto limitu.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

Maximální velikost zásobníku kdykoli během jedné cesty spuštění, měřeno počtem aktivních rámců volání.

Motivace za tento průzkum vázán je omezit velikost zásobníku jakékoli cesty spuštění, které IntelliTest zkoumá během [generování vstupu](input-generation.md). Zejména zabraňuje IntelliTest z použití všech dostupných zásobníku prostor, což by způsobilo přetečení zásobníku, které IntelliTest nelze obnovit z.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

Emaximum počet podmínek nad vstupy, které mohou být kontrolovány během jedné cesty spuštění.

Motivace za tento průzkum vázán je omezit složitost jakékoli cesty spuštění, které IntelliTest zkoumá během [generování vstupu](input-generation.md). Každá podmíněná větev, která závisí na vstupech parametrizovaného testu, se započítává do tohoto limitu.

Například každá cesta v následujícím kódu spotřebovává podmínky n+1:

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

Maximální počet spuštění, které intelliTest se pokusí během zkoumání testu.

Motivace za tento průzkum vázán je, že jakýkoli kód, který obsahuje smyčky nebo rekurze může mít nekonečný počet cest spuštění, a proto IntelliTest musí být omezena během [generování vstupu](input-generation.md).

Dvě nastavení **MaxRuns** a **MaxRunsWithUniquePaths** související takto:

* IntelliTest bude volat parametrizovanou testovací metodu až **maxruns** časy s různými testovacími vstupy.
* Pokud je spuštěný kód deterministický, IntelliTest bude mít pokaždé jinou cestu spuštění. Však za určitých podmínek spustit kód může následovat cestu spuštění již přijata dříve, s různými vstupy.
* IntelliTest spočítá, kolik jedinečných cest spuštění najde; Toto číslo je omezeno volbou **MaxRunsWithUniquePaths.**

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

Maximální počet po sobě jdoucích spuštění bez emitovaného nového testu.

Zatímco IntelliTest může často najít mnoho zajímavých testovacích vstupů v krátké době, po chvíli nenajde žádné další nové testovací vstupy a nebude vypouštět žádné další testy částí. Tato možnost konfigurace umístí vazbu na počet po sobě jdoucích pokusů IntelliTest může provést bez vyzařování nového testu. Když je dosaženo, zastaví průzkum.

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

Maximální počet jedinečných cest, které IntelliTest zváží během průzkumu.

Motivace za tento průzkum vázán je, že jakýkoli kód obsahující smyčky nebo rekurze může mít nekonečný počet cest spuštění, a tak IntelliTest musí být omezena během [generování vstupu](input-generation.md).

Dvě nastavení **MaxRuns** a **MaxRunsWithUniquePaths** související takto:

* IntelliTest bude volat parametrizovanou testovací metodu až **maxruns** časy s různými testovacími vstupy.
* Pokud je spuštěný kód deterministický, IntelliTest bude mít pokaždé jinou cestu spuštění. Však za určitých podmínek spustit kód může následovat cestu spuštění již přijata dříve, s různými vstupy.
* IntelliTest spočítá, kolik jedinečných cest spuštění najde; Toto číslo je omezeno volbou **MaxRunsWithUniquePaths.**

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

Maximální počet výjimek, které lze narazit před průzkumje zastavena.

Motivace za tento průzkum vázán je zastavit zkoumání kódu, který obsahuje mnoho chyb. Pokud IntelliTest najde příliš mnoho chyb v kódu, průzkum je zastaven.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

Cesty spuštění, které překračují nakonfigurované hranice cesty [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack)a [MaxConditions](#maxconditions) jsou ignorovány.

Motivací tohoto průzkumu vázán a je vypořádat se (s největší pravděpodobností) non-ukončující testy. Když IntelliTest dosáhne průzkumu vázána jako [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), nebo [MaxConditions](#maxconditions), předpokládá, že test nebude proces neukončující a nezpůsobí přetečení zásobníku později. Tyto testovací případy mohou představovat problémy s jinými testovacími rámci a tento atribut poskytuje způsob, jak zabránit IntelliTest z emitování testovacích případů pro potenciálně neukončující procesy nebo testovacích případů, které způsobí přetečení zásobníku.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

Označuje typy testů, které by měl intelliTest vyzařovat. Možné hodnoty jsou:

* **Vše** - Emit testy pro všechno, včetně porušení předpokladů.
* **FailuresAndIncreasedBranchHits** (výchozí) - Emit testy pro všechny jedinečné poruchy a vždy, když testovací hočeká se zvýší pokrytí, jak je [řízentestEmissionBranchHits](#testemissionbranchhits).
* **ChybyAndUniquePaths** - Emit testy pro všechny chyby IntelliTest najde a také pro každý vstup testu, který způsobuje jedinečnou cestu spuštění.
* **Selhání** - Emit testy pouze pro selhání.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

V závislosti na aktuální [testEmissionFilter](#testemissionfilter) nastavení IntelliTest vydává nové testovací případy, pokud pokrývají větev v programu, který nebyl zahrnut dříve.

**TestEmissionBranchHits** nastavení určuje, zda IntelliTest by měl jen zvážit, zda větev byla pokryta vůbec **(TestEmissionBranchHits = 1**), pokud test na něž se vztahuje buď jednou nebo dvakrát **(TestEmissionBranchHits = 2**), a tak dále.

**TestEmissionBranchHits =1** vytvoří velmi malou testovací sadu, která pokryje všechny větve, kterých by intelliTest mohl dosáhnout. Zejména tato testovací sada bude také pokrývat všechny základní bloky a příkazy, kterých dosáhla.

Výchozí pro tuto možnost je **TestEmissionBranchHits=2**, který generuje výraznější testovací sadu, která je také vhodnější pro detekci budoucích regresních chyb.

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Své nápady a žádosti o funkce můžete zadávat na webu [Developer Community](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
