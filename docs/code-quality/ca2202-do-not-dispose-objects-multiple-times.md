---
title: 'CA2202: Neuvolňujte objekty několikrát'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4f666ba0cf620249e9308179d715ca38bf0f18b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822862"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Neuvolňujte objekty několikrát

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina

Implementace metody obsahuje cesty kódu, které by mohly způsobit více volání <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> nebo ekvivalentní metody pro uvolnění, například metoda Close() u některých typů na stejný objekt.

## <a name="rule-description"></a>Popis pravidla

A správně implementovaná <xref:System.IDisposable.Dispose%2A> metodu lze volat vícekrát bez vyvolání výjimky. Ale to není zaručeno a pro zabránění generování <xref:System.ObjectDisposedException?displayProperty=fullName> byste neměli volat <xref:System.IDisposable.Dispose%2A> více než jednou pro objekt.

## <a name="related-rules"></a>Související pravidla

- [CA2000: Uvolňujte objekty před ztrátou oboru](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, změňte implementaci, takže to bez ohledu na to cesty kódu, <xref:System.IDisposable.Dispose%2A> je volána pouze jednou pro objekt.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo. I když <xref:System.IDisposable.Dispose%2A> pro objekt se označuje jako bezpečně volat vícekrát, implementace může být v budoucnu změnit.

## <a name="example"></a>Příklad

Vnořené `using` příkazy (`Using` v jazyce Visual Basic) může způsobit narušení CA2202 upozornění. Pokud prostředek IDisposable vnořené vnitřního `using` příkaz obsahuje prostředek vnějšího `using` prohlášení, `Dispose` metoda vnořeného prostředku uvolní obsaženého zdroje. Pokud k této situaci dochází, `Dispose` metoda vnějšího `using` příkaz se pokusí uvolnit jeho prostředků pro podruhé.

V následujícím příkladu <xref:System.IO.Stream> objekt, který je vytvořen ve vnějším pomocí příkazu je vydané na konci vnitřní příkaz using v metodě Dispose <xref:System.IO.StreamWriter> objekt, který obsahuje `stream` objektu. Na konci vnější `using` příkazu `stream` uvolnění objektu podruhé. Druhá verze je porušení CA2202.

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

Chcete-li tento problém vyřešit, použijte `try` / `finally` místo vnějšího bloku `using` příkazu. V `finally` blokovat, ujistěte se, že `stream` prostředků nemá hodnotu null.

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
    if(stream != null)
        stream.Dispose();
}
```

## <a name="see-also"></a>Viz také:

- <xref:System.IDisposable?displayProperty=fullName>
- [Vzor pro metodu Dispose](/dotnet/standard/design-guidelines/dispose-pattern)