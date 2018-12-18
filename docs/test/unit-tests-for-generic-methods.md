---
title: Testy jednotek pro obecné metody
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ced33798841a732773310a902c0d51568bc36fe7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067557"
---
# <a name="unit-tests-for-generic-methods"></a>Testy jednotek pro obecné metody

Přesně stejně jako u jiných metod můžete vygenerovat testů jednotek pro obecné metody. Následující části obsahují informace a příklady vytváření testů jednotek pro obecné metody.

## <a name="type-arguments-and-type-constraints"></a>Argumenty typu a omezení typu.

Když Visual Studio generuje testování částí pro obecné třídy, jako `MyList<T>`, generuje dvě metody: Obecné pomocné rutiny a testovací metodu. Pokud `MyList<T>` obsahuje jeden nebo více omezení typu, typ argumentu musí splňovat všechna omezení typu. Ujistěte se, že obecný kód v rámci testu funguje podle očekávání pro všechny přípustné vstupů, volání testovací metody obecný pomocnou metodu s všechna omezení, které chcete testovat.

## <a name="examples"></a>Příklady
 Následující příklady znázorňují testů jednotek pro obecné typy:

-   [Upravit vygenerované testovací kód](#EditingGeneratedTestCode). V tomto příkladu má dvě části, vygeneruje kód testu a upravit testovací kód. Ukazuje, jak upravit nezpracovaná testovací kód, který je generován z obecné metody do užitečné testovací metodu.

-   [Použití omezení typu](#TypeConstraintNotSatisfied). Tento příklad ukazuje testování částí pro obecné metody, která používá omezení typu. V tomto příkladu není splněná omezení typu.

###  <a name="EditingGeneratedTestCode"></a> Příklad 1: Úpravy generovaný kód testu
 Testuje testovací kód v této části kódu v rámci testovací metodu s názvem `SizeOfLinkedList()`. Tato metoda vrátí celé číslo určující počet uzlů v propojeném seznamu.

 První ukázce kódu, v části vygenerované testovací kód ukazuje neupravenou testovací kód jako byla generována pomocí sady Visual Studio Enterprise. Druhý příklad, v části upravovaný testovací kód ukazuje, jak vám může usnadnit otestovat fungování SizeOfLinkedList metodu pro dvě různé datové typy, `int` a `char`.

 Tento kód ukazuje dvě metody:

-   testovací metodu helper, `SizeOfLinkedListTestHelper<T>()`. Pomocná metoda testu má ve výchozím nastavení "TestHelper" v názvu.

-   testovací metoda `SizeOfLinkedListTest()`. Každý testovací metoda je označena atributem TestMethod.

#### <a name="generated-test-code"></a>Kód generovaný test
 Následující testovací kód byl generován ze `SizeOfLinkedList()` metody. Vzhledem k tomu, že toto je neupravenou generovaný test, musíte ho upravit tak, aby správně testovací metoda SizeOfLinkedList.

```csharp
public void SizeOfLinkedListTestHelper<T>()
{
    T val = default(T); // TODO: Initialize to an appropriate value
    MyLinkedList<T> target = new MyLinkedList<T>(val); // TODO: Initialize to an appropriate value
    int expected = 0; // TODO: Initialize to an appropriate value
    int actual;
    actual = target.SizeOfLinkedList();
    Assert.AreEqual(expected, actual);
    Assert.Inconclusive("Verify the correctness of this test method.");
}

[TestMethod()]
public void SizeOfLinkedListTest()
{
   SizeOfLinkedListTestHelper<GenericParameterHelper>();
}
```

 V předchozím kódu je parametr obecného typu `GenericParameterHelper`. Vzhledem k tomu, jak je znázorněno v následujícím příkladu můžete poskytnout konkrétní datové typy, upravit, můžete spustit test bez úprav tohoto prohlášení.

#### <a name="edited-test-code"></a>Upravený testovací kód
 V následujícím kódu testovací metody a pomocnou metodu testu se upravily tak, aby byly úspěšně testovaných kód testovací metody `SizeOfLinkedList()`.

##### <a name="test-helper-method"></a>Testovací metoda pomocné rutiny
 Pomocná metoda testu provede následující kroky, které odpovídají řádky v kódu s názvem kroky 1 až 5.

1.  Vytvořte obecný propojeného seznamu.

2.  Čtyři uzly připojí k propojeného seznamu. Datový typ obsahu z těchto uzlů neznámý.

3.  Přiřadit očekávané velikosti odkazovaného seznamu do proměnné `expected`.

4.  Vypočítat skutečnou velikost propojeného seznamu a přiřaďte ho k proměnné `actual`.

5.  Porovnání `actual` s `expected` v příkazu Assert. Pokud skutečnou není roven očekávané, test se nezdaří.

##### <a name="test-method"></a>Test – metoda
 Testovací metoda je zkompilován do kódu, která je volána při spuštění testu s názvem SizeOfLinkedListTest. Provede následující kroky, které odpovídají řádky v kódu s názvem kroky 6 a 7.

1.  Zadejte `<int>` při volání testovací pomocnou metodu, chcete-li ověřit, že test pracuje `integer` proměnné.

2.  Zadejte `<char>` při volání testovací pomocnou metodu, chcete-li ověřit, že test pracuje `char` proměnné.

```csharp
public void SizeOfLinkedListTestHelper<T>()
{
    T val = default(T);
    MyLinkedList<T> target = new MyLinkedList<T>(val); // step 1
    for (int i = 0; i < 4; i++) // step 2
    {
        MyLinkedList<T> newNode = new MyLinkedList<T>(val);
        target.Append(newNode);
    }
    int expected = 5; // step 3
    int actual;
    actual = target.SizeOfLinkedList(); // step 4
    Assert.AreEqual(expected, actual); // step 5
}

[TestMethod()]
public void SizeOfLinkedListTest()
{
    SizeOfLinkedListTestHelper<int>();  // step 6
    SizeOfLinkedListTestHelper<char>(); // step 7
}
```

> [!NOTE]
> Pokaždé, když SizeOfLinkedListTest testovací běhy, jeho TestHelper metoda je volána dvakrát. Příkaz kontrolní výraz se musí vyhodnotit na hodnotu true. pokaždé, když pro test proběhl úspěšně. Pokud se test nezdaří, nemusí být jasné, jestli volání, které zadané `<int>` nebo volání, které zadaná `<char>` způsobil, že k selhání. Odpovědi, může prozkoumat zásobník volání, nebo můžete nastavit zarážky v testovací metodě a ladění při spouštění testu. Další informace najdete v tématu [postupy: ladění během zpracování testu v řešení technologie ASP.NET](https://msdn.microsoft.com/Library/de4d7aa1-4a1e-467e-a19b-4a85ec245b8b).


###  <a name="TypeConstraintNotSatisfied"></a> Příklad 2: Použití omezení typu
 Tento příklad ukazuje testování částí pro obecné metody, která používá omezení typu, který není splněná. První část ukazuje kód z kódu v rámci testovacího projektu. Omezení typu je zvýrazněn.

 Druhá část zobrazuje kód z testovacího projektu.

#### <a name="code-under-test-project"></a>Kód v rámci testovacího projektu

```csharp
using System;
using System.Linq;
using System.Collections.Generic;
using System.Text;

namespace ClassLibrary2
{
    public class Employee
    {
        public Employee(string s, int i)
        {
        }
    }

    public class GenericList<T> where T : Employee
    {
        private class Node
        {
            private T data;
            public T Data
            {
                get { return data; }
                set { data = value; }
            }
        }
    }
}
```

#### <a name="test-project"></a>Projekt testů

Stejně jako u všech nově vygenerované testy jednotek, je nutné přidat-neprůkazné Assert – příkazy s tímto testem jednotek vrátíte užitečné výsledky. Nepřidáte je metodu označenou atributem TestMethod, ale metoda "TestHelper", který pro tento test se nazývá `DataTestHelper<T>()`.

 V tomto příkladu obecný parametr typu `T` má omezení `where T : Employee`. Toto omezení není splněná v testovací metodě. Proto `DataTest()` metoda obsahuje příkaz Assert, která vás upozorní na nutnost zadat omezení typu, který se nachází na `T`. Zprávu o tomto příkazu Assert čte následujícím způsobem: `("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`

 Jinými slovy, při volání `DataTestHelper<T>()` metodu z testovací metody `DataTest()`, musíte předat parametr typu `Employee` nebo třída odvozená z `Employee`.

 `using ClassLibrary2;`

 `using Microsoft.VisualStudio.TestTools.UnitTesting;`

 `namespace TestProject1`

```csharp
{
    [TestClass()]
    public class GenericList_NodeTest
    {

        public void DataTestHelper<T>()
            where T : Employee
        {
            GenericList_Shadow<T>.Node target = new GenericList_Shadow<T>.Node(); // TODO: Initialize to an appropriate value
            T expected = default(T); // TODO: Initialize to an appropriate value
            T actual;
            target.Data = expected;
            actual = target.Data;
            Assert.AreEqual(expected, actual);
            Assert.Inconclusive("Verify the correctness of this test method.");
        }

        [TestMethod()]
        public void DataTest()
        {
            Assert.Inconclusive("No appropriate type parameter is found to satisfies the type constraint(s) of T. " +
            "Please call DataTestHelper<T>() with appropriate type parameters.");
        }
    }
}
```

## <a name="see-also"></a>Viz také:

- [Testování částí kódu](../test/unit-test-your-code.md)
