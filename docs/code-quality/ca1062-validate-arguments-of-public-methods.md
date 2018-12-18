---
title: 'CA1062: Ověřte argumenty veřejných metod'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c5894eaf321204ace98a55a3d08411d61207ff7c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857559"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Ověřte argumenty veřejných metod

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategorie|Microsoft.Design|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina

Externě viditelná metoda přístupů přes ukazatel, jeden z jeho argumenty odkazu bez ověření, zda je tento argument `null` (`Nothing` v jazyce Visual Basic).

## <a name="rule-description"></a>Popis pravidla

Všechny argumenty odkazu předané externě viditelným metodám by měly být porovnány `null`. V případě potřeby, vyvolejte <xref:System.ArgumentNullException> když má argument hodnotu `null`.

Pokud metodu lze volat z neznámého sestavení, protože je deklarována jako veřejná nebo chráněná, měli byste ověřit všechny parametry metody. Pokud metoda je navržen pro být volány pouze známé sestavení, by měl provést metodu interní a použít <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut sestavení, který obsahuje metodu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, ověřit každý argument odkazu proti `null`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Toto pravidlo upozornění můžete potlačit, pokud jste si jistí, že parametr přes ukazatel byl ověřen voláním jiného volání metody ve funkci.

## <a name="example"></a>Příklad

Následující příklad ukazuje metodu, která porušuje pravidlo a metodu, která splňuje pravidlo.

 ```csharp
 using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException("input");
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Příklad

Kopírovací konstruktory, které pole nebo vlastnosti, které jsou objekty referenční naplnění také CA1062 pravidla porušit. Porušení dojde, protože může být zkopírovaný objektu, který je předán konstruktoru kopie `null` (`Nothing` v jazyce Visual Basic). Chcete-li vyřešit porušení zásad, můžete metodu statické (sdílené v jazyce Visual Basic) zkontrolujte, zda zkopírovaný objektu není null.

V následujícím `Person` příklad třídy, `other` objekt, který je předán `Person` může být kopírovací konstuktor `null`.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>Příklad

Následující revize `Person` například `other` objekt, který je předán konstruktoru kopie se nejdříve kontroluje u hodnoty null v `PassThroughNonNull` metody.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException("person");
        return person;
    }
}
```