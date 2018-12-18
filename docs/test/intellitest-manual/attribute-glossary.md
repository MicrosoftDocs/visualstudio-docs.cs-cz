---
title: Glosář atributů | Nástroj pro testování Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 0a83a7bd2fc40862411bbfd85f72b804318983c5
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294211"
---
# <a name="attribute-glossary"></a>Glosář atributů

## <a name="attributes-by-namespace"></a>Atributy oboru názvů

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
     - [PexExplorationAttributeBase](#pexexplorationattributebase)<p />

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)<p />

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)<p />

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)<p />

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Tento atribut vyhodnotí, že řídí hodnota nemůže být **null**. Může být připojen k:

* **parametr** metody parametrizovaný test

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

* A **typu**

  ```csharp
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

Může být také připojen k sestavení testu, testovací přípravek nebo testovací metody; v tomto případě musíte uvést první argumenty, které pole nebo typ předpoklady platí. Atribut se vztahuje na typ, platí pro všechna pole s tímto typem formální.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Tento atribut označí třídu, která obsahuje *průzkumy*. Jedná se o ekvivalent MSTest **atribut TestClassAttribute** (nebo NUnit **TestFixtureAttribute**). Tento atribut je volitelný.

Třídy označené [PexClass](#pexclass) musí být *výchozí constructible*:

* veřejně exportovaného typu
* výchozí konstruktor
* není typu abstract

Pokud třída těchto požadavků nesplňuje, dojde k chybě a průzkum se nezdaří.

Je také důrazně doporučuje provádět tyto třídy **částečné** tak, aby IntelliTest může generovat nové testy, které jsou součástí třídy, ale v samostatném souboru. Tento přístup řeší mnohé problémy kvůli [viditelnost](input-generation.md#visibility) a je o typickou techniku v C#.

**Další sady a kategorie**:

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Určení typu v rámci testu**:

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

Třídy mohou obsahovat metody opatřen poznámkou [PexMethod](#pexmethod). IntelliTest také rozumí [nastavit a dovolí metody](test-generation.md#setup-teardown).

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Tento atribut obsahuje typ řazené kolekce členů pro vytvoření instance [obecný parametrizovaný test jednotek](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Tento atribut určí metodu jako [parametrizovaný test jednotek](test-generation.md#parameterized-unit-testing).
Metoda musí být umístěn v rámci třídy označené [PexClass](#pexclass) atribut.

IntelliTest bude generovat konstruktor bez parametrů, tradiční testů, které volání [parametrizovaný test části](test-generation.md#parameterized-unit-testing) s různými parametry.

Parametrizovaný test jednotek:

* musí být metoda instance.
* musí být [viditelné](input-generation.md#visibility) do testovací třídy, do které se umístí vygenerované testy podle [Vodopádové nastavení](settings-waterfall.md)
* může přijmout libovolný počet parametrů
* může být obecné

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

Tento atribut lze nastavit na úrovni sestavení přepsat výchozí hodnoty nastavení pro všechny průzkumy.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "Naked")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Tento atribut určuje sestavení, které je právě testováno podle aktuálního testovacího projektu. 

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Tento atribut slouží k určení sestavení instrumentace.

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

Tento atribut oznamuje IntelliTest, že určitý typ může použít k vytvoření instance základní typy (abstraktní) nebo rozhraní.

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

Pokud tento atribut je připojen k [PexMethod](#pexmethod) (nebo [PexClass](#pexclass), změní výchozí IntelliTest logiku, která označuje, když dojde k selhání testů. Test se nepovažuje jako neúspěšný i v případě, že ji vyvolá zadanou výjimkou.

**Příklad**

Následující testovací Určuje, že konstruktor třídy **zásobníku** může vyvolat **ArgumentOutOfRangeException**:

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

Tento filtr je připojen k testovacího přípravku následujícím způsobem (ji lze také definovat na úrovni sestavení nebo testovací):

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

## <a name="got-feedback"></a>Máte nějakou zpětnou vazbu?

Publikovat své nápady a funkce na požadavky [komunity vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
