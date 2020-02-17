---
title: Upozornění a chyby | Nástroj Microsoft IntelliTest Developer test Tool
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
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275438"
---
# <a name="warnings-and-errors"></a>Upozornění a chyby

## <a name="warnings-and-errors-by-category"></a>Upozornění a chyby podle kategorie

* **Mimo**
  * [MaxBranches – překročeno](#maxbranches-exceeded)
  * [MaxConstraintSolverTime exceeded – překročeno](#maxconstraintsolvertime-exceeded)
  * [MaxConditions – překročeno](#maxconditions-exceeded)
  * [MaxCalls – překročeno](#maxcalls-exceeded)
  * [MaxStack – překročeno](#maxstack-exceeded)
  * [MaxRuns – překročeno](#maxruns-exceeded)
  * [MaxRunsWithoutNewTests – překročeno](#maxrunswithoutnewtests-exceeded)

* **Řešení omezení**
  * [Nejde Konkretizovatovat řešení](#cannot-concretize-solution)

* **Domény nebo modul runtime**
  * [Potřebujete pomáhat s konstrukcí objektu.](#help-construct)
  * [Potřebujete pomáhat najít typy](#help-types)
  * [Byl vyodhadnut použitelný typ](#usable-type-guessed)

* **Spuštění**
  * [Neočekávaná chyba při průzkumu](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)

* **Instrumentace**
  * [Neinstrumentovaná metoda s názvem](#uninstrumented-method-called)
  * [Externí metoda je volána](#external-method-called)
  * [Neinstrumentovaná metoda s názvem](#uninstrumentable-method-called)
  * [Problém s testováním](#testability-issue)
  * [Omezení](#limitation)

* **Interpret**
  * [Pozorovaná neshoda volání](#observed-call-mismatch)
  * [Hodnota uložená ve statickém poli](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>MaxBranches překročil

IntelliTest omezuje délku všech cest spuštění, které prozkoumává při [vytváření vstupu](input-generation.md). Tato funkce zabrání tomu, aby IntelliTest přestane reagovat, když se program dostane do nekonečné smyčky.

Každou podmíněnou a nepodmínkovou větev spouštěného a monitorovaného kódu se započítávají do tohoto limitu, včetně větví, které nejsou závislé na vstupech [parametrizovaného testu jednotek](test-generation.md#parameterized-unit-testing).

Například následující kód spotřebovává větve v pořadí od 100:

```csharp
for (int i=0; i<100; i++) { }
```

Můžete upravit možnost **MaxBranches** atributu odvozeného z **PexSettingsAttributeBase**, jako je například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Následující příklad efektivně odstraní tuto vazbu:

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Můžete také nastavit možnost **TestExcludePathBoundsExceeded** , která bude informovat IntelliTest, jak se tyto problémy všeobecně týkají.

V testovacím kódu můžete použít [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) k ignorování omezení vygenerovaných podmínkou smyčky:

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>MaxConstraintSolverTime překročil

IntelliTest používá k výpočtu nových testovacích vstupů [Řešitel omezení](input-generation.md#constraint-solver) . Řešení omezení může být časově náročný proces, takže IntelliTest umožňuje konfigurovat meze – konkrétně **MaxConstraintSolverTime**.

U mnoha aplikací se významně zvýšil časový limit, což nevede k lepšímu pokrytí. Důvodem je, že většina časových limitů je způsobena systémy omezení, které nemají žádná řešení. IntelliTest ale nemusí být schopné určit, že je nekonzistentní, aniž by bylo potřeba zkoušet všechna možná řešení, což způsobí vypršení časového limitu.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>MaxConditions překročil

IntelliTest omezuje délku všech cest spuštění, které prozkoumává při [vytváření vstupu](input-generation.md). Tato funkce zabrání tomu, aby IntelliTest přestane reagovat, když program zadá nekonečnou smyčku.

Každou podmíněnou větev, která závisí na vstupech [parametrizovaných testů jednotek](test-generation.md#parameterized-unit-testing) , se započítávají do tohoto limitu.

Například každá cesta v následujícím kódu spotřebovává **n + 1** podmínky:

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

Můžete upravit možnost **MaxConditions** atributu odvozeného z **PexSettingsAttributeBase**, jako je například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Například:

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

Můžete také nastavit možnost **TestExcludePathBoundsExceeded** , která bude informovat IntelliTest o tom, jak se tyto problémy všeobecně týkají.

Pomocí [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) můžete ignorovat omezení vygenerovaná podmínkou smyčky:

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
## <a name="maxcalls-exceeded"></a>MaxCalls překročil

IntelliTest omezuje délku všech cest spuštění, které prozkoumává při [vytváření vstupu](input-generation.md). Tato funkce zabrání tomu, aby IntelliTest přestane reagovat, když se program dostane do nekonečné smyčky.

Každé volání (přímý, nepřímý, virtuální nebo skok) spouštěného a monitorovaného kódu se započítává k tomuto limitu.

Můžete upravit možnost **MaxCalls** atributu odvozeného z **PexSettingsAttributeBase**, jako je například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Následující příklad efektivně odstraní tuto vazbu:

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Můžete také nastavit možnost **TestExcludePathBoundsExceeded** , která bude informovat IntelliTest o tom, jak se tyto problémy všeobecně týkají.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>MaxStack překročil

IntelliTest omezuje velikost zásobníku volání jakékoli cesty spuštění, kterou prozkoumává při [vytváření vstupu](input-generation.md). Tato funkce zabrání ukončení IntelliTest, když dojde k přetečení zásobníku.

Můžete upravit možnost **MaxStack** atributu odvozeného z **PexSettingsAttributeBase**, jako je například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Následující příklad efektivně odstraní tuto vazbu (nedoporučuje se):

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Můžete také nastavit možnost **TestExcludePathBoundsExceeded** , která bude informovat IntelliTest o tom, jak se tyto problémy všeobecně týkají.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>MaxRuns překročil

IntelliTest omezuje počet cest spuštění, které prozkoumává při [vytváření vstupu](input-generation.md). Tato funkce zajišťuje, že se IntelliTest ukončí, když má program smyčky nebo rekurzi.

Nemusí se jednat o případ, že při každém spuštění parametrizovaného testu s konkrétními vstupy vygeneruje nový testovací případ. Další informace najdete v tématu [TestEmissionFilter](exploration-bounds.md#testemissionfilter) .

Můžete upravit možnost **MaxRuns** atributu odvozeného z **PexSettingsAttributeBase**, jako je například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Následující příklad efektivně odstraní tuto vazbu (nedoporučuje se):

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>MaxRunsWithoutNewTests překročil

IntelliTest omezuje počet cest spuštění, které prozkoumává při [vytváření vstupu](input-generation.md). Tato funkce zajišťuje, že se IntelliTest ukončí, když má program smyčky nebo rekurzi.

Nemusí se jednat o případ, že při každém spuštění parametrizovaného testu s konkrétními vstupy vygeneruje nový testovací případ. Další informace najdete v tématu [TestEmissionFilter](exploration-bounds.md#testemissionfilter) .

I když IntelliTest často vyhledává mnoho zajímavých testovacích vstupů, může se stát, že po nějakou dobu vygeneruje další testy. Tato možnost určuje, jak dlouho může IntelliTest při hledání dalšího relevantního testovacího vstupu.

Můžete upravit možnost **MaxRunsWithoutNewTests** atributu odvozeného z **PexSettingsAttributeBase**, jako je například [PexClass](attribute-glossary.md#pexclass) nebo [PexMethod](attribute-glossary.md#pexmethod). Následující příklad efektivně odstraní tuto vazbu (nedoporučuje se):

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Nejde konkretizovatovat řešení

Tato chyba je často v důsledku předchozí chyby. IntelliTest pomocí [řešitele omezení](input-generation.md#constraint-solver) určí nové vstupy testu. Testovací vstupy navržené [řešitelem omezení](input-generation.md#constraint-solver) jsou někdy neplatné. K této situaci mohlo dojít, pokud:

* některá omezení nejsou známa.
* Pokud jsou hodnoty vytvořeny uživatelem definovaným způsobem, způsobujících chyby v uživatelském kódu
* Některé z obsažených typů mají logiku inicializace, kterou neřídí IntelliTest (například třídy COM).

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Potřebujete pomáhat s konstrukcí objektu.

IntelliTest [vygeneruje testovací vstupy](input-generation.md)a některé ze vstupů mohou být objekty s poli.
Zde se IntelliTest pokusí vygenerovat instanci třídy, která má soukromé pole, a předpokládá, že k chování zajímavého programu dojde, když má toto soukromé pole konkrétní hodnotu.

Nicméně i když je to možné s reflexí, IntelliTest nevyrábí objekty s libovolnými hodnotami polí.
Místo toho se v těchto případech spoléhá na to, že uživatel poskytne rady, jak použít veřejné metody třídy pro vytvoření objektu a převést ho do stavu, kde jeho soukromé pole má požadovanou hodnotu.

Přečtěte si téma [vytvoření instance stávajících tříd](input-generation.md#existing-classes) , abyste se dozvěděli, jak můžete IntelliTest vytvářet zajímavé objekty.

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Potřebujete pomáhat najít typy

IntelliTest [vygeneruje testovací vstupy](input-generation.md) pro libovolný typ .NET. Zde se IntelliTest pokusí vytvořit instanci, která je odvozena z abstraktní třídy, nebo implementuje abstraktní rozhraní a IntelliTest neznáte žádný typ, který splňuje omezení.

IntelliTest můžete přispět tak, že odkazujete na jeden nebo více typů, které se shodují s omezeními. Obvykle se může jednat o jeden z následujících atributů:

* **PexUseTypeAttribute**, která odkazuje na konkrétní typ.

  Například pokud IntelliTest hlásí, že "neznáte žádné typy, které lze přiřadit k **System. Collections. IDictionary**", můžete k němu případně připojit následující **PexUseTypeAttribute** k testu (nebo k třídě pro vypravení):

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
## <a name="usable-type-guessed"></a>Byl vyodhadnut použitelný typ

IntelliTest [vygeneruje testovací vstupy](input-generation.md) pro všechny typy rozhraní .NET. Pokud je typ abstraktní nebo rozhraní, musí IntelliTest zvolit konkrétní implementaci tohoto typu. Chcete-li provést tuto volbu, je nutné zjistit, které typy existují.

Pokud se zobrazí toto upozornění, znamená to, že IntelliTest prohlédlo na některých odkazovaných sestaveních a našel typ implementace, ale není vhodné, pokud by měl používat daný typ, nebo pokud jsou k dispozici vhodnější typy jinde. IntelliTest jednoduše zvolí typ, který prohlédlo jako slíbených.

Aby se zabránilo tomuto upozornění, můžete buď přijmout volbu typu IntelliTest, nebo pomáhat IntelliTest v používání jiných typů přidáním odpovídajícího [PexUseType](attribute-glossary.md#pexusetype).

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Neočekávaná chyba při průzkumu

Při zkoumání testu byla zachycena Neočekávaná výjimka.

[Ohlaste to prosím jako chybu](#report-bug).

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException –

V uživatelském kódu došlo k výjimce. Zkontrolujte trasování zásobníku a odstraňte chybu ve vašem kódu.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>Neinstrumentovaná metoda s názvem

IntelliTest [vygeneruje testovací vstupy](input-generation.md) monitorováním provádění programu. Je důležité, aby příslušný kód byl správně instrumentované, aby IntelliTest mohl monitorovat jeho chování.

Toto upozornění se zobrazí, když instrumentující kód volá metody v jiném neinstrumentované sestavení.
Pokud chcete, aby IntelliTest prozkoumala interakci obou, je nutné také instrumentovat ostatní sestavení (nebo jejich části).

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Externí metoda je volána

IntelliTest [vygeneruje testovací vstupy](input-generation.md) monitorováním provádění aplikací .NET.
IntelliTest nemůže generovat smysluplné testovací vstupy pro kód, který není napsaný v jazyce .NET.

Toto upozornění se zobrazí, když instrumentující kód volá nespravovanou nativní metodu, kterou IntelliTest nemůže analyzovat. Pokud chcete, aby IntelliTest prozkoumala interakci obou, je nutné napodobovat nespravovanou metodu.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>Neinstrumentovaná metoda s názvem

IntelliTest [vygeneruje testovací vstupy](input-generation.md) monitorováním provádění aplikací .NET. Existují však některé metody, které z technických důvodů IntelliTest nemůžou monitorovat. IntelliTest například nemůže monitorovat statický konstruktor.

Toto upozornění se zobrazí, když instrumentující kód volá metodu, kterou IntelliTest nemůže monitorovat.

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Problém s testováním

IntelliTest [vygeneruje testovací vstupy](input-generation.md) monitorováním provádění programu. Může generovat pouze relevantní vstupy testu, když je program deterministický, a když je příslušné chování řízeno testovacími vstupy.

Toto upozornění se zobrazí, protože během provádění testovacího případu byla volána metoda, která se buď chová jako nedeterministické, nebo spolupracuje s prostředím. Příklady jsou metody **System. Random** a **System. IO. File**. Pokud chcete, aby IntelliTest vytváření smysluplných testovacích vstupů, je nutné napodobovat metody, které IntelliTest příznaky jako problémy s testováním.

<a name="limitation"></a>
## <a name="limitation"></a>Omezení

IntelliTest [generuje testovací vstupy](input-generation.md) pomocí [řešitele omezení](input-generation.md#constraint-solver).
Existují však některé operace, které překračují rozsah [řešitele omezení](input-generation.md#constraint-solver).
V současné době zahrnuje:

* Většina operací s plovoucí desetinnou čárkou (pro čísla s plovoucí desetinnou čárkou jsou podporované jenom některé lineární aritmetické
* převody mezi čísly a celými čísly s plovoucí desetinnou čárkou
* všechny operace s typem **System. Decimal**

Toto upozornění se zobrazí, pokud spuštěný Kód provede operaci nebo volá metodu, kterou IntelliTest nemůže interpretovat.

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Pozorovaná neshoda volání

IntelliTest [vygeneruje testovací vstupy](input-generation.md) monitorováním provádění programu. IntelliTest ale nemusí být schopný monitorovat všechny pokyny. Například nemůže monitorovat nativní kód a nemůže monitorovat kód, který není instrumentované.

Pokud IntelliTest nemůže monitorovat kód, nemůže vygenerovat vstupy testu, které jsou relevantní pro daný kód.
IntelliTest často neobsahuje informace o tom, že nemůže monitorovat metodu, dokud volání této metody nevrátí. Příčinou tohoto upozornění je ale:

* IntelliTest sleduje nějaký kód, který inicioval volání neinstrumentované metody.
* Neinstrumentovaná metoda nazývaná metoda, která je instrumentovaná.
* IntelliTest sleduje vyvolanou metodu instrumentace.

IntelliTest neví, co neinstrumentovaná mezilehlá metoda obsahovala, takže nemusí být schopna generovat vstupy testu, které jsou relevantní pro vložené instrumentované volání.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>Hodnota uložená ve statickém poli

IntelliTest může systematicky určit [relevantní testovací vstupy](input-generation.md) pouze v případě, že je test jednotky deterministický; Jinými slovy, vždy se chová stejně jako u stejných testovacích vstupů. Konkrétně to znamená, že test by měl opustit systém ve stavu, který umožňuje znovu spustit tento test.
V ideálním případě by test jednotek neměl měnit žádný globální stav, ale všechny interakce s Globals by měly být navýšené.

Toto upozornění indikuje, že se změnilo statické pole. To může vést k tomu, že se test chová nedeterministické.

V některých situacích je změna statického pole přijatelná:

* Když vstupy testu způsobí, že se změna zruší, instalační program nebo kód pro vyčištění
* Když je pole iniciováno pouze jednou a hodnota se nezmění později

<a name="report-bug"></a>

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Své nápady a žádosti o funkce můžete zadávat na webu [Developer Community](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
