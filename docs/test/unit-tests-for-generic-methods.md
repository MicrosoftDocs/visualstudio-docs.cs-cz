---
title: Testování částí pro obecné metody
description: Naučte se generovat testy částí pro obecné metody pomocí těchto informací o a příklady vytváření testů jednotek pro obecné metody.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 88ef5d64d2513bb97bdd5589e04669629dfdf6ae
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330040"
---
# <a name="unit-tests-for-generic-methods"></a>Testy jednotek pro obecné metody

Testování částí pro obecné metody můžete vytvořit přesně tak, jak je to nutné pro jiné metody. Následující části obsahují informace o a příklady vytváření testů jednotek pro obecné metody.

## <a name="type-arguments-and-type-constraints"></a>Argumenty typu a omezení typu

Když aplikace Visual Studio generuje test jednotky pro obecnou třídu, například `MyList<T>` , generuje dvě metody: obecnou pomoc a testovací metodu. Pokud `MyList<T>` má jeden nebo více omezení typu, argument typu musí splňovat všechna omezení typu. Aby se zajistilo, že obecný kód v rámci testu funguje podle očekávání pro všechny přípustné vstupy, metoda testu volá obecnou pomocnou metodu se všemi omezeními, která chcete testovat.

## <a name="examples"></a>Příklady
Následující příklady ilustrují testy částí pro obecné typy:

- [Úprava vygenerovaného testovacího kódu](#EditingGeneratedTestCode). Tento příklad obsahuje dva oddíly, generovaný testovací kód a upravený testovací kód. Ukazuje, jak upravit nezpracovaný testovací kód, který je vygenerován z obecné metody do užitečné testovací metody.

- [Použijte omezení typu](#TypeConstraintNotSatisfied). Tento příklad ukazuje test jednotky pro obecnou metodu, která používá omezení typu. V tomto příkladu není splněno omezení typu.

### <a name="example-1-editing-generated-test-code"></a><a name="EditingGeneratedTestCode"></a> Příklad 1: úpravy generovaného testovacího kódu
Testovací kód v této části testuje testovací metodu s názvem `SizeOfLinkedList()` . Tato metoda vrací celé číslo, které určuje počet uzlů v propojeném seznamu.

První ukázka kódu v oddílu, který vygeneroval testovací kód, zobrazuje neupravený testovací kód, který byl vygenerován Visual Studio Enterprise. Druhá ukázka v oddílu upravovaného kódu testu ukazuje, jak lze otestovat fungování SizeOfLinkedList metody pro dva různé typy dat, `int` a `char` .

Tento kód ilustruje dvě metody:

- Pomocná metoda testu, `SizeOfLinkedListTestHelper<T>()` . Ve výchozím nastavení má pomocná metoda testu "TestHelper" v názvu.

- testovací metoda, `SizeOfLinkedListTest()` . Každá testovací metoda je označena atributem TestMethod.

#### <a name="generated-test-code"></a>Kód generovaného testu
Následující kód testu byl vygenerován z `SizeOfLinkedList()` metody. Vzhledem k tomu, že se jedná o neupravený vygenerovaný test, musí být upraven, aby správně otestoval metodu SizeOfLinkedList.

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

V předchozím kódu je parametr obecného typu `GenericParameterHelper` . Vzhledem k tomu, že je lze upravit tak, aby poskytoval konkrétní datové typy, jak je znázorněno v následujícím příkladu, můžete spustit test bez úprav tohoto příkazu.

#### <a name="edited-test-code"></a>Upravený testovací kód
V následujícím kódu byla upravena testovací metoda a pomocná metoda testu, aby byly úspěšně testovány metodu testovaného kódu `SizeOfLinkedList()` .

##### <a name="test-helper-method"></a>Pomocná metoda testu
Pomocná metoda testu provádí následující kroky, které odpovídají řádkům v kódu s označením krok 1 až 5.

1. Vytvoří obecný propojený seznam.

2. Připojit čtyři uzly do odkazovaného seznamu. Datový typ obsahu těchto uzlů je neznámý.

3. Přiřaďte k proměnné očekávanou velikost propojeného seznamu `expected` .

4. Vypočítá skutečnou velikost propojeného seznamu a přiřadí ji k proměnné `actual` .

5. Porovnat `actual` s `expected` příkazem kontrolního výrazu. Pokud skutečnost není stejná jako očekávaná, test se nezdařil.

##### <a name="test-method"></a>Testovací metoda
Testovací metoda je zkompilována do kódu, který je volán při spuštění testu s názvem SizeOfLinkedListTest. Provede následující kroky, které odpovídají řádkům v kódu s označením krok 6 a krok 7.

1. Určete, kdy se má `<int>` volat pomocná metoda testu, aby bylo možné ověřit, zda test funguje pro `integer` proměnné.

2. Určete, kdy se má `<char>` volat pomocná metoda testu, aby bylo možné ověřit, zda test funguje pro `char` proměnné.

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
    SizeOfLinkedListTestHelper<int>();  // step 6
    SizeOfLinkedListTestHelper<char>(); // step 7
}
```

> [!NOTE]
> Pokaždé, když se spustí SizeOfLinkedListTest test, jeho metoda TestHelper se nazývá dvakrát. Příkaz Assert se musí vyhodnotit na hodnotu true pokaždé, když test projde. Pokud se test nezdaří, nemusí být jasné, zda volání určené `<int>` nebo volané volání `<char>` způsobilo selhání. Chcete-li najít odpověď, můžete zkontrolovat zásobník volání, nebo můžete nastavit zarážky v testovací metodě a poté ladit při spuštění testu. Další informace naleznete v tématu [How to: Debug while test in ASP.NET Solution](/previous-versions/ms243172(v=vs.140)).

### <a name="example-2-using-a-type-constraint"></a><a name="TypeConstraintNotSatisfied"></a> Příklad 2: použití omezení typu
Tento příklad ukazuje test jednotky pro obecnou metodu, která používá omezení typu, které není splněno. První oddíl zobrazuje kód z projektu s kódem v rámci testování. Omezení typu je zvýrazněno.

Druhá část zobrazuje kód z testovacího projektu.

#### <a name="code-under-test-project"></a>Projekt kódu pod testováním

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

Stejně jako u všech nově vygenerovaných testů jednotek musíte do testu jednotek přidat nevratné příkazy Assert, aby vracely užitečné výsledky. Nepřidáte je do metody označené atributem TestMethod, ale k metodě "TestHelper", která pro tento test je pojmenována `DataTestHelper<T>()` .

V tomto příkladu má parametr obecného typu `T` omezení `where T : Employee` . Toto omezení není v testovací metodě splněné. Proto `DataTest()` Metoda obsahuje příkaz kontrolního výrazu, který vás upozorní na požadavek na zadání omezení typu, které bylo umístěno `T` . Zpráva tohoto příkazu kontrolního výrazu načte následující: `("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`

Jinými slovy, při volání `DataTestHelper<T>()` metody z testovací metody `DataTest()` , je nutné předat parametr typu `Employee` nebo třídu odvozenou z `Employee` .

```csharp
using ClassLibrary2;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace TestProject1
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

## <a name="see-also"></a>Viz také

- [Testování částí kódu](../test/unit-test-your-code.md)