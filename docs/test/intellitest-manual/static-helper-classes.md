---
title: Statické pomocné třídy | Nástroj Microsoft IntelliTest Developer test Tool
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 5010761213cf79756cf8da3d2fffe60dd0b61efd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591564"
---
# <a name="static-helper-classes"></a>Třídy statických pomocných rutin

IntelliTest poskytuje sadu statických pomocných tříd, které lze použít při vytváření [parametrizovaných testů jednotek](test-generation.md#parameterized-unit-testing):

* [PexAssume](#pexassume): slouží k definování předpokladů pro vstupy a je užitečné pro filtrování nežádoucích vstupů.
* [PexAssert](#pexassert): jednoduchá třída kontrolního výrazu pro použití, pokud testovací rozhraní neposkytuje žádný
* [PexChoose](#pexchoose): datový proud dalších testovacích vstupů, které IntelliTest spravuje
* [PexObserve](#pexobserve): protokoluje konkrétní hodnoty a volitelně je ověřuje ve vygenerovaném kódu.

Některé třídy vám umožňují pracovat s IntelliTestm důvodem pro modul na nízké úrovni:

* [PexSymbolicValue](#pexsymbolicvalue): pomůcky pro kontrolu a úpravy symbolických omezení u proměnných

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

Statická třída, která se používá k vyjádření předpokladů, jako jsou například [předběžné podmínky](test-generation.md#precondition), v [parametrizovaných testech testování částí](test-generation.md#parameterized-unit-testing). Metody této třídy lze použít k vyfiltrování nežádoucích testovacích vstupů.

Pokud předpokládaná podmínka není pro nějaký vstup testu podržena, je vyvolána výjimka **PexAssumeFailedException** . Tím dojde k tichému ignorování testu.

**Příklad**

Následující parametrizovaný test nebude brát v úvahu **j = 0**:

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Poznámky**

Výše uvedený kód je skoro ekvivalent:

```csharp
     if (j==0)
          return;
```

s tím rozdílem, že selhání **PexAssume** vede k žádným testovacím případům. V případě příkazu **if** vygeneruje IntelliTest samostatný testovací případ pro **pokrytí větve příkazu** **if** .

**PexAssume** obsahuje také specializované vnořené třídy pro předpoklady v řetězcích, polích a kolekcích.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

Statická třída, která se používá k vyjádření kontrolních výrazů, jako je například [následné podmínky](test-generation.md#postcondition), v [parametrizovaných testech testování částí](test-generation.md#parameterized-unit-testing).

Pokud podmínka vyhodnocení není pro nějaký vstup testu podržena, je vyvolána výjimka **PexAssertFailedException** , která způsobí selhání testu.

**Příklad**

Následující výrazy vyhodnotí, že absolutní hodnota celého čísla je kladná:

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

Statická třída, která poskytuje pomocné vstupní hodnoty k testu, který lze použít k implementaci [parametrizovaných modelů](input-generation.md#parameterized-mocks).

Třída **PexChoose** vám nepomáhá určit, zda test projde nebo se nezdařil pro konkrétní vstupní hodnoty. **PexChoose** jednoduše poskytuje vstupní hodnoty, které jsou také označovány jako *volby*. Je stále až uživateli omezit vstupní hodnoty a napsat kontrolní výrazy, které definují, kdy test projde nebo dojde k chybě.

**Režimy provozu**

Třída **PexChoose** může fungovat ve dvou režimech:

* I když IntelliTest provádí symbolické analýzy testu a testovaný kód při [vstupní generaci](input-generation.md), výběr vrací libovolné hodnoty a IntelliTest sleduje, jak se jednotlivé hodnoty používají v testu a testovaném kódu. IntelliTest vygeneruje relevantní hodnoty pro aktivaci různých prováděcích cest v rámci testu a testovaného kódu.

* Vygenerovaný kód pro konkrétní testovací případy nastaví poskytovatele výběru určitým způsobem, aby opětovné spuštění takového testovacího případu provedlo konkrétní volby pro aktivaci konkrétní cesty spuštění.

**Využití**

* Jednoduchá volání **PexChoose. Value** pro vygenerování nové hodnoty:

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Statická třída pro protokolování pojmenovaných hodnot.

Když IntelliTest prozkoumá kód, **PexObserve** se používá k záznamu vypočítaných hodnot pomocí jejich formátovaná reprezentace řetězce. Hodnoty jsou přidruženy k jedinečným názvům.

```csharp
PexObserve.Value<string>("result", result);
```

**Příklad**

```csharp
// product code
public static class MathEx {
     public static int Square(int value) { return value * value; }
}

// fixture
[TestClass]
public partial class MathExTests {
     [PexMethod]
     public int SquareTest(int a) {
        int result = MathEx.Square(a);
        // storing result
        return result;
     }
}
```

<a name="pexsymbolicvalue"></a>
## <a name="pexsymbolicvalue"></a>PexSymbolicValue

Statická třída, která slouží k ignorování omezení u parametrů a k vytištění symbolických informací přidružených k hodnotám.

**Využití**

V normálním případě se IntelliTest pokusí pokrýt všechny cesty provádění kódu během provádění. Zejména při výpočtu podmínek předpokladu a podmínky vyhodnocení by se však nemělo prozkoumat všechny možné případy.

**Příklad**

Tento příklad ukazuje implementaci metody **PexAssume. Array. ElementsAreNotNull** .
V metodě můžete ignorovat omezení pro lengh hodnoty pole, abyste se vyhnuli IntelliTest pokusu o generování různých velikostí pole. Omezení se tady ignorují. Pokud testovaný kód se chová jinak u různých délek pole, IntelliTest nemůže generovat různá pole velikosti z omezení testovaného kódu.

```csharp
public static void AreElementsNotNull<T>(T[] value)
    where T : class
{
    PexAssume.NotNull(value);
    // the followings prevents the exploration of all array lengths
    int len = PexSymbolicValue.Ignore<int>(value.Length);

    // building up a boolean value as follows prevents exploration
    // of all combinations of non-null (instead, there are just two cases)
    bool anyNull = false;
    for (int i = 0; i < len; ++i)
        anyNull |= value[i] == null;

    // was any element null?
    if (anyNull)
        PexAssume.Fail("some element of array is a null reference");
}
```

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Publikujte své nápady a žádosti o funkce na [komunitě vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
