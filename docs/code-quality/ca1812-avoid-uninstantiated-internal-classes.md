---
title: 'CA1812: Vyhněte se nevytvořeným instancím vnitřních tříd'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45ff6e07abb77623fe1007ef5e13556e26852224
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827456"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Vyhněte se nevytvořeným instancím vnitřních tříd

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategorie|Microsoft.Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina

Instance typu na úrovni sestavení není vytvořena kódem v sestavení.

## <a name="rule-description"></a>Popis pravidla

Toto pravidlo pokusí vyhledat volání jednoho z konstruktorů typu a oznámí porušení, pokud se nenajde žádný volání.

Následující typy nejsou prozkoumat toto pravidlo:

- Typy hodnot

- Abstraktní typy

- Výčty

- Delegáty

- Typy generované kompilátoru pole

- Typy, které se nedá vytvořit instance, které definují `static` (`Shared` v jazyce Visual Basic) metody pouze.

Pokud použijete <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> na sestavení, které se právě analyzuje, toto pravidlo nedojde na žádné konstruktory, které jsou označeny jako `internal` protože nemůže určit, zda pole se používá jiným `friend` sestavení.

I když toto omezení v analýzy kódu sady Visual Studio nelze vyřešit, externí samostatné FxCop dojde u interní konstruktory, pokud každý `friend` sestavení je k dispozici v analýze.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, typ odeberte nebo přidejte kód, který ji používá. Pokud typ obsahuje pouze statické metody, přidejte jeden z následujících na typ pro zabránění kompilátoru generování výchozí veřejný konstruktor instance:

- Soukromý konstruktor pro typy, které jsou cíleny na rozhraní .NET Framework verze 1.0 a 1.1.

- `static` (`Shared` v jazyce Visual Basic) modifikátor pro typy, které se zaměřují [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Je bezpečné potlačit upozornění tohoto pravidla. Doporučujeme vám, že je potlačení tohoto upozornění v těchto situacích:

- Třída je vytvořená prostřednictvím reflexe pozdní vazby metod, jako <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- Modul runtime se automaticky vytvoří třídu nebo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Například třídy, které implementují <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> nebo <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- Třídy je předán jako parametr obecného typu, který má nové omezení. Například následující příklad vyvolá toto pravidlo.

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
    // [...]
    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

  V takových situacích doporučujeme že potlačení tohoto upozornění.

## <a name="related-rules"></a>Související pravidla

[CA1811: Vyhněte se nevolanému místnímu kódu](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1801: Revize nepoužitých parametrů](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Odeberte nepoužívané místní hodnoty](../code-quality/ca1804-remove-unused-locals.md)