---
title: Testování částí pro obecné metody
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
ms.openlocfilehash: 2158c889aefc85c908aa9ee42d45858fd11d557e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590810"
---
# <a name="unit-tests-for-generic-methods"></a>Testy jednotek pro obecné metody

Můžete generovat testy částí pro obecné metody přesně tak, jak to děláte pro jiné metody. V následujících částech jsou uvedeny informace a příklady vytváření testů částí pro obecné metody.

## <a name="type-arguments-and-type-constraints"></a>Zadejte argumenty a omezení typu

Když Visual Studio generuje testování částí pro obecné `MyList<T>`třídy, jako je například , generuje dvě metody: obecný pomocník a testovací metody. Pokud `MyList<T>` má jeden nebo více omezení typu, argument typu musí splňovat všechna omezení typu. Chcete-li se ujistit, že obecný kód v testu funguje podle očekávání pro všechny přípustné vstupy, testovací metoda volá obecnou pomocnou metodu se všemi omezeními, které chcete testovat.

## <a name="examples"></a>Příklady
Následující příklady ilustrují testy částí pro obecné typy:

- [Upravit generovaný testovací kód](#EditingGeneratedTestCode). Tento příklad má dvě části, Generovaný testovací kód a upravený testovací kód. Ukazuje, jak upravit nezpracovaný testovací kód, který je generován z obecné metody do užitečné testovací metody.

- [Použijte omezení typu](#TypeConstraintNotSatisfied). Tento příklad ukazuje testování částí pro obecnou metodu, která používá omezení typu. V tomto příkladu není splněno omezení typu.

### <a name="example-1-editing-generated-test-code"></a><a name="EditingGeneratedTestCode"></a>Příklad 1: Úpravy generovaného testovacího kódu
Testovací kód v této části testuje metodu `SizeOfLinkedList()`testu kódu s názvem . Tato metoda vrátí celé číslo, které určuje počet uzlů v propojeném seznamu.

První ukázka kódu v části Generovaný testovací kód zobrazuje neupravený testovací kód tak, jak byl vygenerován visual studio enterprise. Druhá ukázka v části Upravený testovací kód ukazuje, jak byste mohli provést testování fungování SizeOfLinkedList `int` metoda `char`pro dva různé datové typy a .

Tento kód ilustruje dvě metody:

- zkušební pomocnou metodu . `SizeOfLinkedListTestHelper<T>()` Ve výchozím nastavení má testovací pomocná metoda ve svém názvu "TestHelper".

- zkušební metoda `SizeOfLinkedListTest()`. Každá zkušební metoda je označena atributem TestMethod.

#### <a name="generated-test-code"></a>Generovaný testovací kód
Z `SizeOfLinkedList()` metody byl vygenerován následující testovací kód. Protože se jedná o neupravený generovaný test, musí být upraven tak, aby správně otestoval metodu SizeOfLinkedList.

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

V předchozím kódu je `GenericParameterHelper`parametr obecného typu . Vzhledem k tomu, můžete upravit a zadat konkrétní datové typy, jak je znázorněno v následujícím příkladu, můžete spustit test bez úprav tohoto příkazu.

#### <a name="edited-test-code"></a>Upravený testovací kód
V následujícím kódu byla upravena zkušební metoda a metoda pomocníka pro testování, aby byly `SizeOfLinkedList()`úspěšně otestovány metodu testu pod testem .

##### <a name="test-helper-method"></a>Testovací pomocná metoda
Pomocná metoda testu provede následující kroky, které odpovídají řádkům v kódu označeném krok 1 až krok 5.

1. Vytvořte obecný propojený seznam.

2. Připojte čtyři uzly k propojenému seznamu. Datový typ obsahu těchto uzlů není znám.

3. Přiřaďte proměnné `expected`očekávanou velikost propojeného seznamu .

4. Vypočítat skutečnou velikost propojeného seznamu a `actual`přiřadit jej proměnné .

5. Porovnejte `actual` s `expected` v příkazu Assert. Pokud skutečnost není rovna očekávané, test se nezdaří.

##### <a name="test-method"></a>Zkušební metoda
Testovací metoda je zkompilován do kódu, který je volán při spuštění testu s názvem SizeOfLinkedListTest. Provede následující kroky, které odpovídají řádkům v kódu označeném krokem 6 a krokem 7.

1. Určete `<int>` při volání testovací pomocné metody, chcete-li ověřit, zda test funguje pro `integer` proměnné.

2. Určete `<char>` při volání testovací pomocné metody, chcete-li ověřit, zda test funguje pro `char` proměnné.

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
> Pokaždé, když sizeOfLinkedListTest test spustí, jeho TestHelper metoda je volána dvakrát. Assert prohlášení musí vyhodnotit true pokaždé, když test předat. Pokud se test nezdaří, nemusí být jasné, zda volání, které zadal `<int>` nebo volání, které zadané `<char>` způsobil selhání. Chcete-li najít odpověď, můžete prozkoumat zásobník volání nebo můžete nastavit zarážky v testovací metodě a potom ladit při spuštění testu. Další informace naleznete v [tématu How to: Debug při spuštění testu v ASP.NET řešení](https://msdn.microsoft.com/Library/de4d7aa1-4a1e-467e-a19b-4a85ec245b8b).

### <a name="example-2-using-a-type-constraint"></a><a name="TypeConstraintNotSatisfied"></a>Příklad 2: Použití omezení typu
Tento příklad ukazuje testování částí pro obecnou metodu, která používá omezení typu, které není splněno. První část zobrazuje kód z projektu pod testem kódu. Omezení typu je zvýrazněno.

Druhá část zobrazuje kód z testovacího projektu.

#### <a name="code-under-test-project"></a>Projekt s kódem pod testem

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

#### <a name="test-project"></a>Testovací projekt

Stejně jako u všech nově generovaných testů částí je nutné do tohoto testování částí přidat neprůkazné příkazy Assert, aby byly vráceny užitečné výsledky. Nepřidáte je do metody označené atributem TestMethod, ale do metody "TestHelper", `DataTestHelper<T>()`která je pro tento test pojmenována .

V tomto příkladu má `T` parametr `where T : Employee`obecného typu omezení . Toto omezení není splněna ve zkušební metodě. `DataTest()` Proto metoda obsahuje Assert prohlášení, které vás upozorní na požadavek na `T`zadání omezení typu, který byl umístěn na . Zpráva tohoto assert prohlášení zní takto:`("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`

Jinými slovy při volání `DataTestHelper<T>()` metody z testovací `DataTest()`metody , musíte předat `Employee` parametr typu nebo `Employee`třídy odvozené z .

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
