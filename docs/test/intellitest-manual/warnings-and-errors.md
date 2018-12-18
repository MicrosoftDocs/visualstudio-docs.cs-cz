---
title: Upozornění a chyby | Nástroj pro testování Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: efb82a7419ba58c27ccab864d2360538075a1089
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000611"
---
# <a name="warnings-and-errors"></a>Upozornění a chyby

## <a name="warnings-and-errors-by-category"></a>Upozornění a chyby podle kategorie

* **Hranice**
  * [MaxBranches překročena](#maxbranches-exceeded)
  * [MaxConstraintSolverTime překročena](#maxconstraintsolvertime-exceeded)
  * [MaxConditions překročena](#maxconditions-exceeded)
  * [MaxCalls překročena](#maxcalls-exceeded)
  * [MaxStack překročena](#maxstack-exceeded)
  * [MaxRuns překročena](#maxruns-exceeded)
  * [MaxRunsWithoutNewTests překročena](#maxrunswithoutnewtests-exceeded)<p />

* **Řešení omezení**
  * [Nejde konkretizovat řešení](#cannot-concretize-solution)<p />

* **domény**
  * [Potřebuji nápovědu k vytvoření objektu](#help-construct)
  * [Potřebujete najít typy](#help-types)
  * [Použitelný typ uhodnout](#usable-type-guessed)<p />

* **Spuštění**
  * [Neočekávaná chyba při průzkumu](#unexpected-exploration)
  * [Targetinvocationexception –](#targetinvocationexception)<p />

* **Instrumentace**
  * [Neinstrumentované metody, které volá](#uninstrumented-method-called)
  * [Externí metodu s názvem](#external-method-called)
  * [Neinstrumentovatelné metody, které volá](#uninstrumentable-method-called)
  * [Problém s testovatelností](#testability-issue)
  * [Omezení](#limitation)<p />

* **Interpret**
  * [Pozorovaná neshoda volání](#observed-call-mismatch)
  * [Hodnota uložená ve statické pole](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>MaxBranches překročena

IntelliTest omezuje délku žádné spuštění cestu, která vám umožní prozkoumat, a během [vstup generování](input-generation.md). Tato funkce zabraňuje IntelliTest přestává reagovat, když se program dostane do nekonečné smyčky.

Každou nepodmíněnou a podmíněné větev kód spuštěný a monitorované se započítává tento limit, včetně větve, které nezávisí na vstupy [parametrizovaný test jednotek](test-generation.md#parameterized-unit-testing).

Například následující kód využívá větví v pořadí 100:

```csharp
for (int i=0; i<100; i++) { }
```

Můžete upravit **MaxBranches** možnost atribut odvozený z **PexSettingsAttributeBase**, jako například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod) . Následující příklad odebere efektivně to vázán:

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Můžete také nastavit **TestExcludePathBoundsExceeded** možnost informovat IntelliTest jak obvykle pro vyřešení těchto problémů.

V kódu testu můžete použít [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) Ignorovat omezení generovaných vzniku smyčky:

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>MaxConstraintSolverTime překročena

Používá Intellitestu [Řešitel omezení](input-generation.md#constraint-solver) vypočítat nové vstupů testu. Řešení omezení může být velmi časově náročný proces, takže IntelliTest umožňuje nakonfigurovat hranice – zejména **MaxConstraintSolverTime**.

Pro mnoho aplikací výrazně zvyšuje časového limitu nebude mít za následek lepší pokrytí. Důvodem je, že většina vypršení časového limitu jsou způsobeny omezení systémy, které nemají žádné řešení. IntelliTest však nemusí být schopní určit, že je nekonzistentní, bez pokusu o všechna možná řešení, které způsobí vypršení časového limitu.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>MaxConditions překročena

IntelliTest omezuje délku žádné spuštění cestu, která vám umožní prozkoumat, a během [vstup generování](input-generation.md). Tato funkce zabraňuje IntelliTest přestává reagovat, když program přejde do nekonečné smyčky.

Každé podmíněné větvi, která závisí na vstupy [parametrizovaný test části](test-generation.md#parameterized-unit-testing) se započítává tento limit.

Například každá cesta v následujícím kódu využívá **n + 1** podmínky:

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

Můžete upravit **MaxConditions** možnost atribut odvozený z **PexSettingsAttributeBase**, jako například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Příklad:

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

Můžete také nastavit **TestExcludePathBoundsExceeded** možnost informovat IntelliTest jak obecně zacházet s těmito problémy.

Můžete použít [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) Ignorovat omezení generovaných vzniku smyčky:

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
## <a name="maxcalls-exceeded"></a>MaxCalls překročena

IntelliTest omezuje délku žádné spuštění cestu, která vám umožní prozkoumat, a během [vstup generování](input-generation.md). Tato funkce zabraňuje IntelliTest přestává reagovat, když se program dostane nekonečné smyčce.

Každé volání (přímý, nepřímý, virtuální nebo odkazů) spuštěné a monitorované kódu se započítává tento limit.

Můžete upravit **MaxCalls** možnost atribut odvozený z **PexSettingsAttributeBase**, jako například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Následující příklad odebere efektivně to vázán:

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Můžete také nastavit **TestExcludePathBoundsExceeded** možnost informovat IntelliTest jak obecně zacházet s těmito problémy.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>MaxStack překročena

IntelliTest omezuje velikost zásobníku volání jakékoli spuštění cestu, která vám umožní prozkoumat, a během [vstup generování](input-generation.md). Tato funkce zabraňuje IntelliTest ukončení dojde k přetečení zásobníku.

Můžete upravit **MaxStack** možnost atribut odvozený z **PexSettingsAttributeBase**, jako například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Následující příklad odebere efektivně tuto mez (nedoporučuje se):

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Můžete také nastavit **TestExcludePathBoundsExceeded** možnost informovat IntelliTest jak obecně zacházet s těmito problémy.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>MaxRuns překročena

IntelliTest omezuje počet cesty spuštění, které vám umožní prozkoumat, a během [vstup generování](input-generation.md). Tato funkce zajišťuje, že IntelliTest je ukončeno program má smyčky nebo rekurzi.

Nemusí být případ, že pokaždé, když IntelliTest spustí parametrizovaný test s konkrétní vstupů, vydá nový testovací případ. Zobrazit [TestEmissionFilter](exploration-bounds.md#testemissionfilter) Další informace.

Můžete upravit **MaxRuns** možnost atribut odvozený z **PexSettingsAttributeBase**, jako například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Následující příklad odebere efektivně tuto mez (nedoporučuje se):

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>MaxRunsWithoutNewTests překročena

IntelliTest omezuje počet cesty spuštění, které vám umožní prozkoumat, a během [vstup generování](input-generation.md). Tato funkce zajišťuje, že IntelliTest je ukončeno program má smyčky nebo rekurzi.

Nemusí být případ, že pokaždé, když IntelliTest spustí parametrizovaný test s konkrétní vstupů, vydá nový testovací případ. Zobrazit [TestEmissionFilter](exploration-bounds.md#testemissionfilter) Další informace.

Zatímco IntelliTest často najde mnoho zajímavých testovací vstupy původně, ji mohou není – po chvíli – vysílat jakékoli další testy. Tato možnost řídí, jak dlouho může IntelliTest zkusit najít další relevantní zkušební vstup.

Můžete upravit **MaxRunsWithoutNewTests** možnost atribut odvozený z **PexSettingsAttributeBase**, jako například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Následující příklad odebere efektivně tuto mez (nedoporučuje se):

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Nejde konkretizovat řešení

Tato chyba je často důsledkem dřívější chybě. Používá Intellitestu [Řešitel omezení](input-generation.md#constraint-solver) k určení nové vstupů testu. V některých případech testovací vstupy navrhovaná [Řešitel omezení](input-generation.md#constraint-solver) jsou neplatné. K tomu může dojít při:

* nejsou známy určitých omezení
* Pokud hodnoty jsou vytvořeny tak definovaný uživatelem, způsobí chyby v uživatelském kódu
* Některé typy používané mají logiku inicializace není řízen IntelliTest (například třídy modelu COM)

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Potřebuji nápovědu k vytvoření objektu

IntelliTest [generuje testovací vstupy](input-generation.md), a některých vstupních hodnot mohou být objekty s poli.
Tady IntelliTest pokusí o vytvoření instance třídy, která má privátní pole a předpokládá, že zvláštního chování programu dojde při tento privátní pole nemá určitou hodnotu.

Ale i to je možné pomocí reflexe, inteligentní testování není výroba objekty s hodnotami libovolného pole.
Místo toho v těchto případech se spoléhá na uživatele, poskytnout nápovědu, jak pomocí veřejné metody třídy pro vytvoření objektu a přenést je do stavu, kdy jeho soukromé pole má požadovanou hodnotu.

Čtení [vytvoření instance existujících tříd](input-generation.md#existing-classes) se dozvíte, jak může pomoct IntelliTest zajímavé objekty je možné vytvořit.

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Potřebujete najít typy

IntelliTest [generuje testovací vstupy](input-generation.md) pro jakýkoli typ .NET. Tady IntelliTest se pokusí vytvořit instanci, která je odvozena z abstraktní třídy nebo implementuje abstraktní rozhraní a IntelliTest nezná typ, který splňuje omezení.

IntelliTest může pomoct najetím myší na jeden nebo více typů, které odpovídají omezení. Obvykle vám pomůže jednu z následujících atributů:

* **PexUseTypeAttribute**, která odkazuje na konkrétní typ.

  Například, pokud IntelliTest hlásí, že "nezná typů lze přiřadit k **rozhraní System.Collections.IDictionary**", můžete ji připojením následující **PexUseTypeAttribute** testu (nebo do třídy testovacího přípravku):

  ```csharp
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **Atribut úrovně sestavení**

  ```csharp
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>Použitelný typ uhodnout

IntelliTest [generuje testovací vstupy](input-generation.md) pro všechny typy .NET. Když typ je abstraktní nebo rozhraní, musíte zvolit IntelliTest konkrétní implementaci daného typu. Tuto volbu, je potřeba vědět, jaké typy existovat.

Když se zobrazí toto upozornění, it indiicates, Intellitestu podívali se na některé z odkazovaných sestavení a najít typ implementace, ale není jistí, jestli je typ, nebo pokud jsou vhodnější typy dostupné jinde by měl používat. IntelliTest jednoduše zvolit typ, který hledá příslibů.

Pokud chcete tomuto upozornění předejít, můžete buď přijmout IntelliTest na typ výběru nebo při použití jiných typů tak, že přidáte odpovídající IntelliTest [PexUseType](attribute-glossary.md#pexusetype).

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Neočekávaná chyba při průzkumu

Při průzkumu testu byla zachycena neočekávaná výjimka.

Prosím [. ohlaste to jako chybu](#report-bug).

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>Targetinvocationexception –

V uživatelském kódu došlo k výjimce. Zkontrolovat trasování zásobníku a odeberte chyby v kódu.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>Neinstrumentované metody, které volá

IntelliTest [generuje testovací vstupy](input-generation.md) při sledování provádění programu. Je důležité, že příslušný kód správně instrumentovaná, tak, aby IntelliTest můžete monitorovat její chování.

Toto upozornění se zobrazí, když instrumentované kód volá metody v jiné, neinstrumentované sestavení.
Pokud chcete Intellitestu a prozkoumejte interakce obou, musí také instrumentace jiné sestavení (nebo jeho části).

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Externí metodu s názvem

IntelliTest [generuje testovací vstupy](input-generation.md) monitorování výkonu aplikací .NET.
IntelliTest nejde generovat vstupy smysluplné testu pro kód, který není napsané v jazyce .NET.

Toto upozornění se zobrazí, když instrumentované kód volá metodu nespravované, nativní, který nelze analyzovat IntelliTest. Pokud chcete Intellitestu a prozkoumejte interakce obou, musí napodobení nespravované metody.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>Neinstrumentovatelné metody, které volá

IntelliTest [generuje testovací vstupy](input-generation.md) monitorování výkonu aplikací .NET. Existují však některé metody, že z technických důvodů IntelliTest nemůže monitorovat. Například IntelliTest nelze monitorovat statický konstruktor.

Toto upozornění se zobrazí, když instrumentované kód volá metodu, která IntelliTest nemůže monitorovat.

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Problém s testovatelností

IntelliTest [generuje testovací vstupy](input-generation.md) při sledování provádění programu. Program je deterministická a data relevantní chování se řídí testovací vstupy může vygenerovat pouze relevantní testovací vstupy.

Toto upozornění se zobrazí proto, že během provádění testovacích případů, byla volána metoda, chová nedeterministicky nebo komunikuje s prostředím. Příklady jsou metody **System.Random** a **System.IO.File**. Pokud chcete IntelliTest vytvořit smysluplné testovací vstupy, musí napodobení metody, které IntelliTest označí příznakem jako problémy s testovatelností.

<a name="limitation"></a>
## <a name="limitation"></a>Omezení

IntelliTest [generuje testovací vstupy](input-generation.md) pomocí [Řešitel omezení](input-generation.md#constraint-solver).
Existují však některé operace, které jsou nad rámec [Řešitel omezení](input-generation.md#constraint-solver).
Toto aktuálně zahrnuje:

* operace s nejvíce plovoucí desetinnou (pouze některé lineární aritmetické operace je podporována na plovoucí desetinnou čárkou)
* převody mezi čísel s plovoucí desetinnou a celá čísla
* všechny operace na **System.Decimal** typu

Toto upozornění se zobrazí, když spuštěný kód provádí operaci, nebo volá metodu, která IntelliTest nelze interpretovat.

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Pozorovaná neshoda volání

IntelliTest [generuje testovací vstupy](input-generation.md) při sledování provádění programu. IntelliTest však nemusí být schopen monitorovat všechny pokyny. Například jej nelze monitorovat nativního kódu a ho nelze monitorovat kód, který není instrumentovaný.

Když IntelliTest nelze sledovat kódu, nemůže generovat testovací vstupy, které souvisí s tímto kódem.
IntelliTest často není vědět skutečnost, metodě ho nelze sledovat, dokud volání této metody vrátí. Příčinou tohoto upozornění je však:

* IntelliTest monitorovat nějaký kód, který inicioval volání neinstrumentované metody
* Neinstrumentované metody volá metodu, která je instrumentováno
* IntelliTest monitoruje instrumentované metodu, která byla volána

IntelliTest neví, co neinstrumentované metody zprostředkující udělal, proto nemusí být schopna generovat testovací vstupy, které jsou relevantní pro vnořené instrumentované volání.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>Hodnota uložená ve statické pole

Inteligentní testování systematicky určit [relevantní testovací vstupy](input-generation.md) pouze při testování jednotek je deterministická; jinými slovy, vždy chová se stejně jako u stejné testovací vstupy. Konkrétně to znamená, že test měli nechat systém ve stavu, který umožňuje znovu provést tento test.
V ideálním případě testování částí by neměly měnit žádné globální stav, ale všechny interakce s globals by měl být imitace.

Toto upozornění signalizuje, že byl změněn statické pole; To by mohlo způsobit nepoužitelnost test chovat nedeterministicky.

V některých situacích je přijatelné změna statické pole:

* Když způsobí, že testovací vstupy vrátilo zpět změnu nastavení nebo čištění kódu
* Když pole je zahájeno pouze jednou, a hodnota nemění později

<a name="report-bug"></a>

## <a name="got-feedback"></a>Máte nějakou zpětnou vazbu?

Publikovat své nápady a funkce na požadavky [komunity vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).