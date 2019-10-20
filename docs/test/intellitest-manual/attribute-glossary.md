---
title: Glosář atributů | Nástroj Microsoft IntelliTest Developer test Tool
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: dce8d33f876ee34e18812cb744d7d3d6f53a5506
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653235"
---
# <a name="attribute-glossary"></a>Glosář atributů

## <a name="attributes-by-namespace"></a>Atributy podle oboru názvů

* **Microsoft. Pex. Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
    * [PexExplorationAttributeBase](#pexexplorationattributebase)

* **Microsoft. Pex. Framework. Settings**
  * [PexAssemblySettings](#pexassemblysettings)

* **Microsoft. Pex. Framework. instrumentace**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)

* **Microsoft. Pex. Framework. using**
  * [PexUseType](#pexusetype)

* **Microsoft. Pex. Framework. Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Tento atribut vyhodnotí, že upravená hodnota nemůže být **null**. Dá se připojit k:

* **parametr** parametrizované testovací metody

  ```csharp
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* **pole**

  ```csharp
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* **typ**

  ```csharp
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

Dá se taky připojit k testovacímu sestavení, testovacímu přípravku nebo testovací metodě; v takovém případě musí první argumenty označovat, na které pole se předpoklady vztahují. Pokud atribut platí pro typ, platí pro všechna pole s tímto formálním typem.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Tento atribut označuje třídu, která obsahuje *průzkumy*. Je ekvivalentem MSTest **atribut TestClassAttribute** (nebo nunit **TestFixtureAttribute**). Tento atribut je nepovinný.

Třídy označené jako [PexClass](#pexclass) musí být *výchozí constructible*:

* veřejně exportovaný typ
* výchozí konstruktor
* neabstraktní

Pokud třída tyto požadavky nesplňuje, je hlášena chyba a průzkum se nezdařil.

Je také velmi doporučeno, aby tyto třídy byly **částečně** tak, aby IntelliTest mohli generovat nové testy, které jsou součástí třídy, ale v samostatném souboru. Tento přístup řeší mnohé problémy z důvodu [viditelnosti](input-generation.md#visibility) a je typickou technikou v C#.

**Další sada a kategorie**:

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Určení testovaného typu**:

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

Třída může obsahovat metody s poznámkou s [PexMethod](#pexmethod). IntelliTest také rozumí [nastavení a odtrhnout metody](test-generation.md#setup-teardown).

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Tento atribut poskytuje řazenou kolekci členů typu pro vytvoření instance [obecného parametrizovaného testu jednotek](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Tento atribut označuje metodu jako [parametrizovaný test jednotky](test-generation.md#parameterized-unit-testing).
Metoda se musí nacházet v rámci třídy označené atributem [PexClass](#pexclass) .

IntelliTest bude generovat tradiční testy bez parametrů, které volají [parametrizovaný test jednotek](test-generation.md#parameterized-unit-testing) s různými parametry.

Parametrizovaný test jednotek:

* musí být metoda instance.
* musí být [viditelný](input-generation.md#visibility) pro třídu testu, do které jsou vygenerované testy umístěny podle [Nastavení vodopádu](settings-waterfall.md) .
* může mít libovolný počet parametrů
* může být obecný

**Příklad**

```csharp
[PexClass]
public partial class MyTests {
     [PexMethod]
     public void MyTest(int i)
     { ... }
}
```

<a name="pexexplorationattributebase"></a>
## <a name="pexexplorationattributebase"></a>PexExplorationAttributeBase

[Další informace](xref:Microsoft.Pex.Framework.PexExplorationAttributeBase)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

Tento atribut lze nastavit na úrovni sestavení a přepsat tak výchozí hodnoty nastavení pro všechny průzkumy.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "MSTestv2")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Tento atribut určuje sestavení, které je Testováno pomocí aktuálního testovacího projektu.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Tento atribut slouží k určení sestavení, které má být instrumentované.

**Příklad**

```csharp
using Microsoft.Pex.Framework;

// the assembly containing ATypeFromTheAssemblyToInstrument should be instrumented
[assembly: PexInstrumentAssembly(typeof(ATypeFromTheAssemblyToInstrument))]

// the assembly name can be used as well
[assembly: PexInstrumentAssembly("MyAssemblyName")]
```

<a name="pexusetype"></a>
## <a name="pexusetype"></a>PexUseType

Tento atribut oznamuje IntelliTest, že může použít konkrétní typ pro vytvoření instance (abstraktních) základních typů nebo rozhraní.

**Příklad**

```csharp
[PexMethod]
[PexUseType(typeof(A))]
[PexUseType(typeof(B))]
public void MyTest(object testParameter)
{
     ... // IntelliTest will consider types A and B to instantiate 'testParameter'
}
```

<a name="pexallowedexception"></a>
## <a name="pexallowedexception"></a>PexAllowedException

Pokud je tento atribut připojen k [PexMethod](#pexmethod) (nebo k [PexClass](#pexclass), změní výchozí IntelliTest logiku, která indikuje, kdy testy selžou. Test se nepovažuje za neúspěšný, a to i v případě, že vyvolá určenou výjimku.

**Příklad**

Následující test určuje, že konstruktor **zásobníku** může vyvolat výjimku **ArgumentOutOfRangeException**:

```csharp
class Stack {
  int[] _elements;
  int _count;
  public Stack(int capacity) {
    if (capacity<0) throw new ArgumentOutOfRangeException();
    _elements = new int[capacity];
    _count = 0;
  }
  ...
}
```

Filtr je připojen k přípravné následujícím způsobem (lze také definovat na úrovni sestavení nebo testu):

```csharp
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[Další informace](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromAssemblyAttribute)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[Další informace](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeAttribute)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[Další informace](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeUnderTestAttribute)

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Publikujte své nápady a žádosti o funkce na [komunitě vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
