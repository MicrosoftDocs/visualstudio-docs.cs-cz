---
title: Statické pomocné třídy | Testovací nástroj pro vývojáře IntelliTest společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302614"
---
# <a name="static-helper-classes"></a>Třídy statických pomocných rutin

IntelliTest poskytuje sadu statické pomocné třídy, kterou lze použít při vytváření [parametrizovaných testů částí](test-generation.md#parameterized-unit-testing):

* [PexAssume](#pexassume): slouží k definování předpokladů na vstupech a je užitečné pro filtrování nežádoucích vstupů
* [PexAssert](#pexassert): jednoduchá třída assertion pro použití, pokud testovací rámec neposkytuje
* [PexChoose](#pexchoose): datový proud dalších testovacích vstupů, které intelliTest spravuje
* [PexObserve](#pexobserve): zaznamenává konkrétní hodnoty a volitelně je ověřuje ve generovaném kódu

Některé třídy umožňují interakci s intelliTest uvažování motoru na nízké úrovni:

* [PexSymbolicValue](#pexsymbolicvalue): nástroje pro kontrolu nebo úpravu symbolických omezení proměnných

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

Statická třída používaná k vyjádření předpokladů, jako jsou [například předpoklady](test-generation.md#precondition), v [parametrizovaných jednotkových testech](test-generation.md#parameterized-unit-testing). Metody této třídy lze odfiltrovat nežádoucí zkušební vstupy.

Pokud předpokládaná podmínka neobsahuje pro některé zkušební vstup, **PexAssumeFailedException** je vyvolána. To způsobí, že test tiše ignorovány.

**Příklad**

Následující parametrizovaný test nebude brát v úvahu **j=0**:

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

s tím rozdílem, že selhání **PexAssume** výsledky v žádné testovacích případů. V případě **příkazu if** intelliTest generuje samostatný testovací případ, který pokrývá **tehdejší** větvi příkazu **if.**

**PexAssume** také obsahuje specializované vnořené třídy pro předpoklady na řetězec, pole a kolekce.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

Statická třída používaná k vyjádření kontrolních výrazů, například [postconditions](test-generation.md#postcondition), v [parametrizovaných jednotkových testech](test-generation.md#parameterized-unit-testing).

Pokud je uplatněná podmínka neobsahuje pro některé testovací vstup, Je vyvolána **PexAssertFailedException,** která způsobí selhání testu.

**Příklad**

Následující tvrzení, že absolutní hodnota celého čísla je pozitivní:

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

Statická třída, která dodává pomocné vstupní hodnoty testu, který lze použít k implementaci [Parametrizované mocks](input-generation.md#parameterized-mocks).

**PexChoose** Třída nepomůže při určování, zda test projde nebo selže pro konkrétní vstupní hodnoty. **PexChoose** jednoduše poskytuje vstupní hodnoty, které jsou také označovány jako *volby*. Je stále na uživateli omezit vstupní hodnoty a psát kontrolní výrazy, které definují, když test projde nebo selže.

**Režimy činností**

Třída **PexChoose** může pracovat ve dvou režimech:

* Zatímco IntelliTest provádí symbolickou analýzu testu a testovaný kód během [generování vstupu](input-generation.md), výběr vrátí libovolné hodnoty a IntelliTest sleduje, jak se jednotlivé hodnoty používají v testu a testovaný kód. IntelliTest bude generovat příslušné hodnoty pro aktivaci různých cest spuštění v testu a testovaný kód.

* Generovaný kód pro konkrétní testovací případy nastaví zprostředkovatele volby určitým způsobem tak, aby opětovné spuštění takového testovacího případu provede konkrétní volby pro aktivaci konkrétní cesty spuštění.

**Použití**

* Jednoduché volání **PexChoose.Value** pro generování nové hodnoty:

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Statická třída protokolu s pojmenovanými hodnotami.

Když IntelliTest zkoumá kód, **PexObserve** se používá k záznamu vypočítané hodnoty pomocí jejich reprezentace formátovaného řetězce. Hodnoty jsou spojeny s jedinečnými názvy.

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

Statická třída používaná k ignorování omezení parametrů a k tisku symbolických informací spojených s hodnotami.

**Použití**

Normálně IntelliTest se pokusí pokrýt všechny cesty spuštění kódu během provádění. Však zejména při výpočtu předpokladu a kontrolní podmínky, by neměla zkoumat všechny možné případy.

**Příklad**

Tento příklad ukazuje implementaci metody **PexAssume.Arrays.ElementsAreNotNull.**
V metodě ignorujete omezení délky hodnoty pole, abyste se vyhnuli pokusu o generování různých velikostí pole. Omezení jsou ignorovány pouze zde. Pokud testovaný kód chová odlišně pro různé délky pole, IntelliTest nelze generovat různé velikosti polí z omezení testovaného kódu.

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

Své nápady a žádosti o funkce můžete zadávat na webu [Developer Community](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
