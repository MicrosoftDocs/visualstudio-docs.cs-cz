---
title: Třídy statických pomocných rutin | Nástroj pro testování Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a5c635c8fb3def61b8278b7b7c4b66aa196d82b8
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000474"
---
# <a name="static-helper-classes"></a>Třídy statických pomocných rutin

Poskytuje sadu statickou pomocnou třídu, která se dá použít při vytváření Intellitestu [parametrizované testy částí](test-generation.md#parameterized-unit-testing):

* [PexAssume](#pexassume): slouží k definování předpoklady na vstupy a je užitečné pro filtrování nežádoucí vstupy
* [PexAssert](#pexassert): Třída jednoduché kontrolní výraz pro použití testovacího rozhraní neposkytne-li
* [PexChoose](#pexchoose): datový proud další testovací vstupy, které spravuje Intellitestu
* [PexObserve](#pexobserve): protokoly konkrétní hodnoty a v případě potřeby je ověřuje v generovaném kódu

Některé třídy umožňují pracovat s modulem reasoning IntelliTest v nízké úrovně:

* [PexSymbolicValue](#pexsymbolicvalue): nástroje zkontrolovat nebo upravit symbolické omezení pro proměnné

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

Statická třída použitá pro express předpoklady, například [předběžné podmínky](test-generation.md#precondition)v [parametrizované testy částí](test-generation.md#parameterized-unit-testing). Metody této třídy lze použít k filtrování nežádoucí testovací vstupy.

Pokud se předpokládá, že podmínka pro některé zkušební vstup, neobsahuje **PexAssumeFailedException** je vyvolána výjimka. To způsobí, že test tiše ignorováno.

**Příklad**

Následující parametrizovaný test nebude považovat za **j = 0**:

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Poznámky**

Výše uvedený kód je téměř ekvivalentní:

```csharp
     if (j==0)
          return;
```

s tím rozdílem, že neúspěšného **PexAssume** výsledkem žádné testovací případy. V případě třídy **Pokud** příkazu, IntelliTest se vytvoří samostatný testovací případ k pokrytí **pak** větev **Pokud** příkaz.

**PexAssume** obsahuje také specializované vnořené třídy pro předpoklady o řetězce, pole a kolekce.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

Statická třída použitá pro kontrolní výrazy, jako například express [vstupních](test-generation.md#postcondition)v [parametrizované testy částí](test-generation.md#parameterized-unit-testing).

Podmínka s potvrzením pro některé zkušební vstup, neobsahuje-li **PexAssertFailedException** je vyvolána výjimka, která způsobí selhání testu.

**Příklad**

Následující kontrolní výrazy, absolutní hodnotu celého čísla je pozitivní:

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

Statická třída poskytující pomocné vstupní hodnoty do testu, který slouží k implementaci [parametrizované Mocks](input-generation.md#parameterized-mocks).

**PexChoose** třídy nepomůže při určování, zda testovací projde nebo selže pro konkrétní vstupní hodnoty. **PexChoose** jednoduše zadá vstupní hodnoty, které jsou také označovány jako *volby*. Je stále maximálně uživatele omezit vstupní hodnoty a vytvářet kontrolní výrazy, které definují, kdy testovací projde nebo selže.

**Režimy činnosti**

**PexChoose** třídy můžete pracovat ve dvou režimech:

* Zatímco IntelliTest provádí symbolické analýzy testu a testovaný kód během [vstup generování](input-generation.md), vrátí výběru libovolné hodnoty a IntelliTest sleduje, jak každá hodnota se používá v testu a testovaný kód. IntelliTest vygeneruje příslušné hodnoty pro aktivaci spuštění různých cest v testu a testovaný kód.

* Generovaný kód pro konkrétní testovací případy nastaví poskytovatele podle výběru určitým způsobem, tak, aby opakované spuštění testovacího případu se konkrétní možnosti k aktivaci cestu konkrétního spuštění.

**Využití**

* Jednoduché volání **PexChoose.Value** ke generování novou hodnotu:

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Statické třídy do protokolu pojmenovaných hodnot.

Když inteligentní testování vám umožní prozkoumat kód, **PexObserve** se používá k zaznamenání vypočítané hodnoty pomocí jejich reprezentace formátovaný řetězec. Hodnoty jsou spojeny s jedinečnými názvy.

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

Statická třída slouží k Ignorovat omezení parametrů a tisknout symbolické informace související s hodnotami.

**Využití**

Za normálních okolností IntelliTest se pokusí zahrnují všechny cesty provádění kódu během provádění. Ale zejména v případě výpočetních předpokladů a kontrolní výraz podmínky, by neměla prozkoumat všechny možné případy.

**Příklad**

Tento příklad ukazuje implementaci **PexAssume.Arrays.ElementsAreNotNull** metody. V metodě můžete ignorovat omezení na délce hodnotu pole, aby se zabránilo IntelliTest pokoušeli vygenerovat různé velikosti pole. Omezení jsou jenom tady ignoruje. Pokud testovaný kód chová odlišně pro různé pole délky, Intellitestu nelze generovat různé velikosti pole z omezení testovaného kódu.

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

## <a name="got-feedback"></a>Máte nějakou zpětnou vazbu?

Publikovat své nápady a funkce na požadavky [komunity vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).