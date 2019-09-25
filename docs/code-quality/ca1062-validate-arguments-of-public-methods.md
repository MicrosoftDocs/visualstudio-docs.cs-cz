---
title: 'CA1062: Ověřte argumenty veřejných metod'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8106a4c0244cbd79e88a2bdc50e04ea74627dab4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235339"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Ověřte argumenty veřejných metod

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategorie|Microsoft.Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Externě viditelná metoda odkazuje na jeden z jeho referenčních argumentů bez ověření, zda je `null` tento argument (`Nothing` v Visual Basic).

## <a name="rule-description"></a>Popis pravidla

Všechny argumenty odkazů, které jsou předány externě viditelným metodám, by `null`měly být zkontrolovány proti. V případě potřeby vyvolejte <xref:System.ArgumentNullException> a, pokud je `null`argumentem.

Pokud metoda může být volána z neznámého sestavení, protože je deklarována jako veřejná nebo chráněná, měli byste ověřit všechny parametry metody. Pokud je metoda navržena tak, aby byla volána pouze pomocí známých sestavení, měli byste provést interní metodu a použít <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut na sestavení, které obsahuje metodu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, ověřte každý argument odkazu proti `null`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Můžete potlačit upozornění z tohoto pravidla, pokud jste si jistí, že parametr s odkazem byl ověřen jiným voláním metody ve funkci.

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

Kopírovací konstruktory, které naplní pole nebo vlastnosti odkazující na objekty, mohou také porušovat pravidlo CA1062. K porušení dojde, protože zkopírovaný objekt, který je předán konstruktoru kopírování, může být `null` (`Nothing` v Visual Basic). Chcete-li vyřešit porušení, použijte metodu static (Shared in Visual Basic) pro kontrolu, zda kopírovaný objekt není null.

V následujícím `Person` příkladu `other` třídy může `Person` být`null`objekt předaný konstruktoru kopírování.

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

V následujícím změněném `Person` příkladu je `other` objekt, který je předán kopírovacímu konstruktoru, nejprve `PassThroughNonNull` zkontrolován na hodnotu null v metodě.

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