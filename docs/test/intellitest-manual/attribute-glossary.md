---
title: Glosář atributů | Testovací nástroj pro vývojáře IntelliTest společnosti Microsoft
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 00d8b24d26237a3c7b4130eba4614b5ea7b7eccd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302628"
---
# <a name="attribute-glossary"></a>Glosář atributů

## <a name="attributes-by-namespace"></a>Atributy podle oboru názvů

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
    * [PexExplorationAttributeBase](#pexexplorationattributebase)

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)

* **Microsoft.Pex.Framework.Instrumentace**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Tento atribut tvrdí, že řízená hodnota nemůže být **null**. Může být připojen k:

* **parametr** parametrizované zkušební metody

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

Může být také připojen ke zkušební sestavě, zkušebnímu přípravku nebo zkušební metodě; v tomto případě musí první argumenty uvádět, na které pole nebo typ se předpoklady vztahují. Pokud se atribut vztahuje na typ, platí pro všechna pole s tímto formálním typem.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Tento atribut označuje třídu, která obsahuje *průzkumy*. Jedná se o ekvivalent atributu MSTest **TestClassAttribute** (nebo Atribut **Utajení NUnit TestFixtureAttribute).** Tento atribut je volitelný.

Třídy označené [třídou PexClass](#pexclass) musí být *výchozí k ono :*

* veřejně exportovaný typ
* výchozí konstruktor
* není abstraktní

Pokud třída nesplňuje tyto požadavky, je hlášena chyba a průzkum se nezdaří.

Důrazně doporučujeme, aby tyto třídy **částečné** tak, aby IntelliTest můžete generovat nové testy, které jsou součástí třídy, ale v samostatném souboru. Tento přístup řeší mnoho problémů z důvodu [viditelnosti](input-generation.md#visibility) a je typická technika v C#.

**Další sada a kategorie**:

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Určení zkoušeného typu**:

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

Třída může obsahovat metody s poznámkou [PexMethod](#pexmethod). IntelliTest také chápe [metody nastavení a bourání](test-generation.md#setup-teardown).

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Tento atribut poskytuje typ řazené kolekce členů pro vytváření instancí [obecné parametrizované testování částí](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Tento atribut označí metodu jako [parametrizovaný test částí](test-generation.md#parameterized-unit-testing).
Metoda musí být umístěna v rámci třídy označené atributem [PexClass.](#pexclass)

IntelliTest bude generovat tradiční, parametrické testy, které volají [parametrizovaný test částí](test-generation.md#parameterized-unit-testing) s různými parametry.

Parametrizovaný test částí:

* musí být metoda instance
* musí být [viditelné](input-generation.md#visibility) pro zkušební třídu, do které jsou generované zkoušky umístěny podle [vodopádu Nastavení](settings-waterfall.md)
* může mít libovolný počet parametrů
* mohou být generické

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

[Více informací](xref:Microsoft.Pex.Framework.PexExplorationAttributeBase)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

Tento atribut lze nastavit na úrovni sestavy přepsat výchozí hodnoty nastavení pro všechny průzkumy.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "MSTestv2")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Tento atribut určuje sestavení, které je testováno aktuálním testovacím projektem.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Tento atribut se používá k určení sestavy, která má být instrumentována.

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

Tento atribut říká IntelliTest, že můžete použít určitý typ k vytvoření instance (abstraktní) základní typy nebo rozhraní.

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

Pokud je tento atribut připojen k [pexmethod](#pexmethod) (nebo [pexclass](#pexclass), změní výchozí logiku IntelliTest, která označuje, když se testy nezdaří. Test nebude považován za neúspěšný, i v případě, že vyvolá zadanou výjimku.

**Příklad**

Následující test určuje, že konstruktor **Stack** může vyvolat **ArgumentOutOfRangeException**:

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

Filtr je připojen k upínací mutovi (lze jej také definovat na úrovni sestavy nebo zkoušky):

```csharp
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[Více informací](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromAssemblyAttribute)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[Více informací](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeAttribute)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[Více informací](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeUnderTestAttribute)

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Své nápady a žádosti o funkce můžete zadávat na webu [Developer Community](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
