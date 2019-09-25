---
title: 'CA2202: Neuvolňujte objekty několikrát'
ms.date: 07/16/2019
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c7fa7756383426f990e18225995a768de9fefbd
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231741"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Neuvolňujte objekty několikrát

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Implementace metody obsahuje cesty kódu, které by mohly způsobit více volání <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> nebo ekvivalent Dispose, jako je například metoda Close () u některých typů na stejném objektu.

## <a name="rule-description"></a>Popis pravidla

Správně implementovaná <xref:System.IDisposable.Dispose%2A> metoda může být volána víckrát bez vyvolání výjimky. Nicméně to není zaručeno a vyhnout se generování <xref:System.ObjectDisposedException?displayProperty=fullName> , neměli byste volat <xref:System.IDisposable.Dispose%2A> pro objekt více než jednou.

## <a name="related-rules"></a>Související pravidla

- [CA2000 Uvolnit objekty před ztrátou oboru](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, změňte implementaci tak, aby nezávisle na cestě <xref:System.IDisposable.Dispose%2A> kódu byly pro objekt volány pouze jednou.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo. I v <xref:System.IDisposable.Dispose%2A> případě, že je známo, že se má u objektu bezpečně volat vícenásobně, implementace se může v budoucnu změnit.

## <a name="example"></a>Příklad

Vnořené `using` příkazy (`Using` v Visual Basic) mohou způsobit porušení upozornění CA2202. Pokud prostředek IDisposable vnořeného vnitřního `using` příkazu obsahuje prostředek vnějšího `using` příkazu, `Dispose` metoda vnořeného prostředku uvolní obsažený prostředek. Pokud dojde k této situaci, `Dispose` metoda vnějšího `using` příkazu se pokusí o odstranění svého prostředku podruhé.

V následujícím příkladu je <xref:System.IO.Stream> objekt, který je vytvořen v vnějším příkazu Using, vydán na konci vnitřního příkazu Using v metodě <xref:System.IO.StreamWriter> Dispose objektu, který obsahuje `stream` objekt. Na konci vnějšího `using` příkazu `stream` se objekt uvolní podruhé. Druhá verze je porušení CA2202.

```csharp
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Příklad

Chcete-li tento problém vyřešit, `try` použijte / `finally` místo vnějšího `using` příkazu blok. V bloku Ujistěte se, že `stream` prostředek není null. `finally`

```csharp
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    stream?.Dispose();
}
```

> [!TIP]
> Výše uvedená syntaxe je [operátor s hodnotou null-Conditional.](/dotnet/csharp/language-reference/operators/member-access-operators#null-conditional-operators--and-) `?.`

## <a name="see-also"></a>Viz také:

- <xref:System.IDisposable?displayProperty=fullName>
- [Vzor pro metodu Dispose](/dotnet/standard/design-guidelines/dispose-pattern)