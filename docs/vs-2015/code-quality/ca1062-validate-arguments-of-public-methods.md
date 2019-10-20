---
title: 'CA1062: Ověřte argumenty veřejných metod | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 50044b51a3e576ff7d1c11b19b2f498f99b63019
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663646"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Ověřte argumenty veřejných metod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategorie|Microsoft. Design|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Externě viditelná metoda odkazuje na jeden z jejích odkazů, aniž by bylo nutné ověřit, zda je tento argument `null` (`Nothing` v Visual Basic).

## <a name="rule-description"></a>Popis pravidla
 Všechny argumenty odkazů, které jsou předány externě viditelným metodám, by měly být zkontrolovány proti `null`. V případě potřeby vyvolejte <xref:System.ArgumentNullException>, pokud je argument `null`.

 Pokud metoda může být volána z neznámého sestavení, protože je deklarována jako veřejná nebo chráněná, měli byste ověřit všechny parametry metody. Pokud je metoda navržena tak, aby byla volána pouze pomocí známých sestavení, měli byste provést interní metodu a použít atribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> na sestavení, které obsahuje metodu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, ověřte každý argument odkazu na `null`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Můžete potlačit upozornění z tohoto pravidla, pokud jste si jistí, že parametr s odkazem byl ověřen jiným voláním metody ve funkci.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která porušuje pravidlo a metodu, která splňuje pravidlo.

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Příklad
 V [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] toto pravidlo nezjistí, že parametry jsou předávány jiné metodě, která provádí ověření.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Příklad
 Kopírovací konstruktory, které naplní pole nebo vlastnosti odkazující na objekty, mohou také porušovat pravidlo CA1062. K porušení dojde, protože zkopírovaný objekt, který je předán konstruktoru kopírování, může být `null` (`Nothing` v Visual Basic). Chcete-li vyřešit porušení, použijte metodu static (Shared in Visual Basic) pro kontrolu, zda kopírovaný objekt není null.

 V následujícím příkladu třídy `Person` může být objekt `other` předaný konstruktoru kopírování `Person` `null`.

```

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
 V následujícím opraveném příkladu `Person` je objekt `other`, který je předán konstruktoru Copy, nejprve zkontrolován na hodnotu null v metodě `PassThroughNonNull`.

```
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
