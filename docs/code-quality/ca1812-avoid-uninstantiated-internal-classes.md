---
title: 'CA1812: Vyhněte se nevytvořeným instancím interních tříd'
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f924e9530a7ee43ec2222366141c3af6be2efc29
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233601"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Vyhněte se nevytvořeným instancím interních tříd

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategorie|Microsoft. Performance|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Interní typ (na úrovni sestavení) nikdy nevytváří instanci.

## <a name="rule-description"></a>Popis pravidla

Toto pravidlo se pokusí najít volání jednoho z konstruktorů typu a oznámí porušení, pokud není nalezeno žádné volání.

Toto pravidlo nezkoumá následující typy:

- Typy hodnot

- Abstraktní typy

- Výčty

- Delegáty

- Typy polí generovaných kompilátorem

- Typy, jejichž instance se nedají vytvořit a které [`static`](/dotnet/csharp/language-reference/keywords/static) definují jenom metody ([ `Shared` v Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)).

Použijete <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> -li pro sestavení, které je analyzováno, toto pravidlo nebude označovat typy, které jsou označeny jako [`internal`](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` v Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)), protože pole může být použito v sestavení typu Friend.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, odeberte typ nebo přidejte kód, který ho používá. Pokud typ obsahuje pouze `static` metody, přidejte jeden z následujících typů k typu, čímž zabráníte kompilátoru v generování výchozího veřejného konstruktoru instance:

- Modifikátor pro typy C# , které cílí na .NET Framework 2,0 nebo novější. `static`

- Privátní konstruktor pro typy, které cílí na .NET Framework verze 1,0 a 1,1.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Z tohoto pravidla je bezpečné potlačit upozornění. Toto upozornění doporučujeme potlačit v následujících situacích:

- Třída je vytvořena pomocí metod reflexe s pozdní vazbou <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>, jako je.

- Třída je vytvořena automaticky modulem runtime nebo ASP.NET. Některé příklady automaticky vytvořených tříd jsou ty, které <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> implementují <xref:System.Web.IHttpHandler?displayProperty=fullName>nebo.

- Třída je předána jako parametr typu, který má [ `new` omezení](/dotnet/csharp/language-reference/keywords/new-constraint). Následující příklad bude označen příznakem CA1812 pravidla:

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }

    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

## <a name="related-rules"></a>Související pravidla

- [CA1811: Vyhněte se nevolanému privátnímu kódu](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801: Zkontrolovat nepoužité parametry](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804: Odebrat nepoužívané místní hodnoty](../code-quality/ca1804-remove-unused-locals.md)