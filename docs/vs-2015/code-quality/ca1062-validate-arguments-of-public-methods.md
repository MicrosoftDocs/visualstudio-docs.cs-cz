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
ms.openlocfilehash: 377906675d70a712f8ca72b0b6e4d8a6864c1fbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533234"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Ověřte argumenty veřejných metod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategorie|Microsoft. Design|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Externě viditelná metoda odkazuje na jeden z jeho referenčních argumentů bez ověření, zda je tento argument `null` ( `Nothing` v Visual Basic).

## <a name="rule-description"></a>Popis pravidla
 Všechny argumenty odkazů, které jsou předány externě viditelným metodám, by měly být zkontrolovány proti `null` . V případě potřeby vyvolejte a, pokud <xref:System.ArgumentNullException> je argumentem `null` .

 Pokud metoda může být volána z neznámého sestavení, protože je deklarována jako veřejná nebo chráněná, měli byste ověřit všechny parametry metody. Pokud je metoda navržena tak, aby byla volána pouze pomocí známých sestavení, měli byste provést interní metodu a použít <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut na sestavení, které obsahuje metodu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, ověřte každý argument odkazu proti `null` .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Můžete potlačit upozornění z tohoto pravidla, pokud jste si jistí, že parametr s odkazem byl ověřen jiným voláním metody ve funkci.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která porušuje pravidlo a metodu, která splňuje pravidlo.

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Příklad
 V nástroji [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] Toto pravidlo nezjistí, že parametry jsou předávány jiné metodě, která provádí ověření.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Příklad
 Kopírovací konstruktory, které naplní pole nebo vlastnosti odkazující na objekty, mohou také porušovat pravidlo CA1062. K porušení dojde, protože zkopírovaný objekt, který je předán konstruktoru kopírování, může být `null` ( `Nothing` v Visual Basic). Chcete-li vyřešit porušení, použijte metodu static (Shared in Visual Basic) pro kontrolu, zda kopírovaný objekt není null.

 V následujícím `Person` příkladu třídy `other` může být objekt předaný `Person` konstruktoru kopírování `null` .

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
 V následujícím změněném `Person` příkladu `other` je objekt, který je předán kopírovacímu konstruktoru, nejprve zkontrolován na hodnotu null v `PassThroughNonNull` metodě.

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
