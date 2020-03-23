---
title: Varování a chyby | Testovací nástroj pro vývojáře IntelliTest společnosti Microsoft
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c3f5fe55a4e1afb1a9551d43d0d61ae9f76b81e4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275438"
---
# <a name="warnings-and-errors"></a>Upozornění a chyby

## <a name="warnings-and-errors-by-category"></a>Varování a chyby podle kategorie

* **Hranice**
  * [MaxBranches – překročeno](#maxbranches-exceeded)
  * [MaxConstraintSolverTime exceeded – překročeno](#maxconstraintsolvertime-exceeded)
  * [MaxConditions – překročeno](#maxconditions-exceeded)
  * [MaxCalls – překročeno](#maxcalls-exceeded)
  * [MaxStack – překročeno](#maxstack-exceeded)
  * [MaxRuns – překročeno](#maxruns-exceeded)
  * [MaxRunsWithoutNewTests – překročeno](#maxrunswithoutnewtests-exceeded)

* **Řešení omezení**
  * [Nelze konkretizovat řešení](#cannot-concretize-solution)

* **Domény nebo runtime**
  * [Potřebujete pomoc při vytváření objektu](#help-construct)
  * [Potřebujete pomoc při hledání typů](#help-types)
  * [Uhodnoutelný typ](#usable-type-guessed)

* **Spouštěcí**
  * [Neočekávané selhání během průzkumu](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)

* **Instrumentation**
  * [Neinstrumentovaná metoda volána](#uninstrumented-method-called)
  * [Externí metoda volána](#external-method-called)
  * [Neinstrumentovatelná metoda nazývaná](#uninstrumentable-method-called)
  * [Problém testovatelnosti](#testability-issue)
  * [Omezení](#limitation)

* **Tlumočník**
  * [Neshoda pozorovaného volání](#observed-call-mismatch)
  * [Hodnota uložená ve statickém poli](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>MaxBranches – překročeno

IntelliTest omezuje délku libovolné cesty spuštění, kterou zkoumá během [generování vstupu](input-generation.md). Tato funkce zabraňuje IntelliTest přestane reagovat, když program přejde do nekonečné smyčky.

Do tohoto limitu se započítává každá podmíněná a bezpodmínečná větev provedeného a monitorovaného kódu, včetně větví, které nezávisí na vstupech [parametrizovaného testu částí](test-generation.md#parameterized-unit-testing).

Například následující kód spotřebovává větve v pořadí 100:

```csharp
for (int i=0; i<100; i++) { }
```

Můžete upravit možnost **MaxBranches** atributu odvozeného z **PexSettingsAttributeBase**, například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Následující příklad účinně odebere tuto vazbu:

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Můžete také nastavit **TestExcludePathBoundsExceeded** možnost informovat IntelliTest, jak obecně řešit tyto problémy.

V testovacím kódu můžete použít [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) ignorovat omezení generovaná podmínkou smyčky:

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>MaxConstraintSolverTime exceeded – překročeno

IntelliTest používá [řešič omezení](input-generation.md#constraint-solver) k výpočtu nových testovacích vstupů. Řešení omezení může být velmi časově náročný proces, takže IntelliTest umožňuje konfigurovat hranice - zejména **MaxConstraintSolverTime**.

U mnoha aplikací výrazně zvýšení časového opojení nebude mít za následek lepší pokrytí. Důvodem je, že většina časových opovenek jsou způsobeny omezení systémy, které nemají žádná řešení. IntelliTest však nemusí být schopen určit, že je nekonzistentní bez vyzkoušení všech možných řešení, což bude mít za následek časový čas.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>MaxConditions – překročeno

IntelliTest omezuje délku libovolné cesty spuštění, kterou zkoumá během [generování vstupu](input-generation.md). Tato funkce zabraňuje IntelliTest přestane reagovat, když program zadá nekonečné smyčky.

Každá podmíněná větev, která závisí na vstupech [parametrizovaného testu částí,](test-generation.md#parameterized-unit-testing) se započítává do tohoto limitu.

Například každá cesta v následujícím kódu spotřebovává podmínky **n+1:**

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    // conditions are "0<n", "1<n", ..., "!(n<n)"
    for (int i=0; i<n; i++)
    { ... }

    // irrelevant for MaxConditions, since conditions do not depend on input
    for (int i=0; i<100; i++)
    { ... }
}
```

Můžete upravit možnost **MaxConditions** atributu odvozeného z **PexSettingsAttributeBase**, například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Například:

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

Můžete také nastavit **TestExcludePathBoundsExceeded** možnost informovat IntelliTest, jak obecně řešit tyto problémy.

[Hodnotu PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) můžete použít k ignorování omezení generovaných podmínkou smyčky:

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    int nshadow = PexSymbolicValue.Ignore(n); // IntelliTest looses track of 'n'

    // irrevelant for MaxConditions, since nshadow is not related to input
    for (int i=0; i<nshadow; i++)
    {...}
}
```

<a name="maxcalls-exceeded"></a>
## <a name="maxcalls-exceeded"></a>MaxCalls – překročeno

IntelliTest omezuje délku libovolné cesty spuštění, kterou zkoumá během [generování vstupu](input-generation.md). Tato funkce zabraňuje IntelliTest přestane reagovat, když program přejde vstoupí do nekonečné smyčky.

Každé volání (přímé, nepřímé, virtuální nebo skok) provedeného a monitorovaného kódu se započítává do tohoto limitu.

Můžete upravit možnost **MaxCalls** atributu odvozeného z **PexSettingsAttributeBase**, například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Následující příklad účinně odebere tuto vazbu:

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Můžete také nastavit **TestExcludePathBoundsExceeded** možnost informovat IntelliTest, jak obecně řešit tyto problémy.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>MaxStack – překročeno

IntelliTest omezuje velikost zásobníku volání jakékoli cesty spuštění, kterou zkoumá během [generování vstupu](input-generation.md). Tato funkce zabraňuje ukončení intellitestu, když dojde k přetečení zásobníku.

Můžete upravit možnost **MaxStack** atributu odvozeného z **PexSettingsAttributeBase**, například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Následující příklad účinně odebere tuto vazbu (nedoporučuje se):

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Můžete také nastavit **TestExcludePathBoundsExceeded** možnost informovat IntelliTest, jak obecně řešit tyto problémy.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>MaxRuns – překročeno

IntelliTest omezuje počet cest spuštění, které zkoumá během [generování vstupu](input-generation.md). Tato funkce zajišťuje, že IntelliTest ukončí, když program má smyčky nebo rekurze.

Nemusí to být případ, že pokaždé, když IntelliTest spustí parametrizovaný test s konkrétními vstupy, vydává nový testovací případ. Další informace naleznete v tématu [TestEmissionFilter.](exploration-bounds.md#testemissionfilter)

Můžete upravit možnost **MaxRuns** atributu odvozeného z **PexSettingsAttributeBase**, například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Následující příklad účinně odebere tuto vazbu (nedoporučuje se):

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>MaxRunsWithoutNewTests – překročeno

IntelliTest omezuje počet cest spuštění, které zkoumá během [generování vstupu](input-generation.md). Tato funkce zajišťuje, že IntelliTest ukončí, když program má smyčky nebo rekurze.

Nemusí to být případ, že pokaždé, když IntelliTest spustí parametrizovaný test s konkrétními vstupy, vydává nový testovací případ. Další informace naleznete v tématu [TestEmissionFilter.](exploration-bounds.md#testemissionfilter)

Zatímco IntelliTest často najde mnoho zajímavých testovacích vstupů zpočátku, nemusí - po chvíli - vyzařovat žádné další testy. Tato možnost určuje, jak dlouho může intelliTest stále snažit najít jiný relevantní testovací vstup.

Můžete upravit **maxrunswithoutNewTests** možnost atributu odvozeného z **PexSettingsAttributeBase**, například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Následující příklad účinně odebere tuto vazbu (nedoporučuje se):

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Nelze konkretizovat řešení

Tato chyba je často důsledkem dřívější chyby. IntelliTest používá [řešič omezení](input-generation.md#constraint-solver) k určení nových testovacích vstupů. V některých případě jsou testovací vstupy navržené [řešičem omezení](input-generation.md#constraint-solver) neplatné. K tomu může dojít, když:

* některá omezení nejsou známa
* Pokud jsou hodnoty vytvářeny uživatelem definovaným způsobem, což způsobuje chyby v uživatelském kódu
* některé typy mají inicializační logiku, která není řízena intelliTest (například třídy COM)

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Potřebujete pomoc s konstrukcí objektu

IntelliTest [generuje testovací vstupy](input-generation.md)a některé vstupy mohou být objekty s poli.
Zde IntelliTest pokusí generovat instanci třídy, která má soukromé pole a předpokládá, že dojde k zajímavé chování programu dojde, když toto soukromé pole má určitou hodnotu.

Však zatímco to je možné s reflexe, IntelliTest nevyrábí objekty s libovolnými hodnotami pole.
Místo toho v těchto případech spoléhá na uživatele poskytnout rady o tom, jak používat veřejné metody třídy k vytvoření objektu a přivést ji do stavu, kde jeho soukromé pole má požadovanou hodnotu.

Přečtěte si [vytváření instancí existujících tříd,](input-generation.md#existing-classes) abyste se dozvěděli, jak můžete intelliTestu pomoci vytvořit zajímavé objekty.

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Potřebujete pomoct najít typy

IntelliTest [generuje testovací vstupy](input-generation.md) pro libovolný typ .NET. Zde IntelliTest pokusí vytvořit instanci, která je odvozena z abstraktní třídy nebo implementuje abstraktní rozhraní a IntelliTest neví o žádném typu, který splňuje omezení.

IntelliTest můžete pomoci tak, že ukážete na jeden nebo více typů, které odpovídají omezením. Obvykle pomůže jeden z následujících atributů:

* **PexUseTypeAttribute**, který odkazuje na určitý typ.

  Například pokud IntelliTest hlásí, že "neví o žádné typy přiřaditelné **System.Collections.IDictionary**", můžete pomoci připojením následující **PexUseTypeAttribute** k testu (nebo k uchycení třídy):

  ```csharp
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **Atribut na úrovni sestavení**

  ```csharp
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>Odhadnutí použitelného typu

IntelliTest [generuje testovací vstupy](input-generation.md) pro všechny typy .NET. Pokud je typ abstraktní nebo rozhraní, IntelliTest musí zvolit konkrétní implementaci tohoto typu. Chcete-li tuto volbu, musí vědět, které typy existují.

Pokud je toto upozornění zobrazeno, znamená to, že IntelliTest se podíval na některé odkazované sestavení a našel typ implementace, ale není si jistý, zda by měl používat tento typ, nebo pokud existují vhodnější typy k dispozici jinde. IntelliTest jednoduše zvolil typ, který vypadal slibně.

Chcete-li se vyhnout tomuto upozornění, můžete buď přijmout volbu typu IntelliTest, nebo pomoci společnosti IntelliTest při používání jiných typů přidáním odpovídajícího [typu PexUseType](attribute-glossary.md#pexusetype).

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Neočekávaná chyba při průzkumu

Při zkoumání testu byla zachycena neočekávaná výjimka.

[Nahlaste to prosím jako chybu](#report-bug).

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

V uživatelském kódu došlo k výjimce. Zkontrolujte trasování zásobníku a odeberte chybu v kódu.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>Volání neinstrumentované metody

IntelliTest [generuje testovací vstupy](input-generation.md) sledováním spuštění programu. Je nezbytné, aby příslušný kód je správně instrumentované tak, aby IntelliTest můžete sledovat jeho chování.

Toto upozornění se zobrazí, když instrumentovaný kód volá metody v jiném, neinstrumentované sestavení.
Pokud chcete, aby IntelliTest prozkoumal interakci obou, musíte také instrumentovat druhou sestavu (nebo její části).

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Volání externí metody

IntelliTest [generuje testovací vstupy](input-generation.md) sledováním provádění aplikací .NET.
IntelliTest nemůže generovat smysluplné testovací vstupy pro kód, který není napsán v jazyce .NET.

Toto upozornění se zobrazí, když instrumentovaný kód volá nespravovanou nativní metodu, kterou intelliTest nelze analyzovat. Pokud chcete, aby IntelliTest prozkoumal interakci obou, musíte zesměšňovat nespravovanou metodu.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>Volání neinstrumentovatelné metody

IntelliTest [generuje testovací vstupy](input-generation.md) sledováním provádění aplikací .NET. Existují však některé metody, které z technických důvodů intelliTest nelze sledovat . Například IntelliTest nelze sledovat statický konstruktor.

Toto upozornění se zobrazí, když instrumentovaný kód volá metodu, kterou intelliTest nemůže sledovat.

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Problém s testovatelností

IntelliTest [generuje testovací vstupy](input-generation.md) sledováním provádění programu. Může generovat relevantní testovací vstupy pouze v případě, že je program deterministický a pokud je příslušné chování řízeno testovacími vstupy.

Toto upozornění se zobrazí, protože během provádění testovacího případu byla volána metoda, která se chová nedeterministicky nebo spolupracuje s prostředím. Příklady jsou metody **System.Random** a **System.IO.File**. Pokud chcete, aby IntelliTest vytvořit smysluplné testovací vstupy, musíte zesměšňovat metody, které IntelliTest příznaky jako problémy testovatelnost.

<a name="limitation"></a>
## <a name="limitation"></a>Omezení

IntelliTest [generuje testovací vstupy](input-generation.md) pomocí [řešiče omezení](input-generation.md#constraint-solver).
Existují však některé operace, které jsou nad rámec [řešiče omezení](input-generation.md#constraint-solver).
To v současné době zahrnuje:

* většina operací s plovoucí desetinnou čárkou (u čísel s plovoucí desetinnou čárkou je podporována pouze některá lineární aritmetika)
* převody mezi čísly s plovoucí desetinnou a celá čísla
* všechny operace na typu **System.Decimal**

Toto upozornění se zobrazí, když spouštěný kód provede operaci nebo zavolá metodu, kterou intelliTest nelze interpretovat.

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Pozorovaná neshoda ve volání

IntelliTest [generuje testovací vstupy](input-generation.md) sledováním spuštění programu. IntelliTest však nemusí být schopen sledovat všechny pokyny. Například nemůže sledovat nativní kód a nemůže sledovat kód, který není instrumentovaný.

Pokud IntelliTest nemůže sledovat kód, nemůže generovat testovací vstupy, které jsou relevantní pro tento kód.
Často IntelliTest není vědoma skutečnosti, že nelze sledovat metodu, dokud volání této metody vrátí. Příčinou tohoto upozornění je však:

* IntelliTest monitoroval nějaký kód, který inicioval volání neinstrumentované metody
* Neinstrumentovaná metoda volaná metodou, která je instrumentována
* IntelliTest monitoruje instrumentovanou metodu, která byla volána

IntelliTest neví, co neinstrumentované mezilehlé metody udělal, takže nemusí být schopen generovat testovací vstupy, které jsou relevantní pro vnořené instrumentované volání.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>Hodnota uložená ve statickém poli

IntelliTest může systematicky určit [příslušné testovací vstupy](input-generation.md) pouze v případě, že test částí je deterministický; jinými slovy, vždy se chová stejným způsobem pro stejné testovací vstupy. Zejména to znamená, že test by měl ponechat systém ve stavu, který umožňuje znovu provést tento test.
V ideálním případě by testování částí nemělo měnit žádný globální stav, ale všechny interakce s globálními by měly být zesměšňovány.

Toto upozornění označuje, že bylo změněno statické pole. To může způsobit, že test chovat nedeterministicky.

V některých situacích je změna statického pole přijatelná:

* Když testovací vstupy způsobí, že instalační nebo vyčištění kód vrátit změnu
* pokud je pole zahájeno pouze jednou a hodnota se poté nezmění

<a name="report-bug"></a>

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Své nápady a žádosti o funkce můžete zadávat na webu [Developer Community](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
