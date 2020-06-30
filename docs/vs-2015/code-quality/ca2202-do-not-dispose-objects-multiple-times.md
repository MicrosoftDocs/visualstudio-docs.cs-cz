---
title: 'CA2202: Neodstraňujte objekty několikrát | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 31bf7fe33aa59c3a713d2da81ddbd11ed6899723
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546286"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Neuvolňujte objekty několikrát
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Implementace metody obsahuje cesty kódu, které by mohly způsobit více volání <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> nebo ekvivalent Dispose, jako je například metoda Close () u některých typů na stejném objektu.

## <a name="rule-description"></a>Popis pravidla
 Správně implementovaná <xref:System.IDisposable.Dispose%2A> metoda může být volána víckrát bez vyvolání výjimky. Nicméně to není zaručeno a vyhnout se generování <xref:System.ObjectDisposedException?displayProperty=fullName> , neměli byste volat pro <xref:System.IDisposable.Dispose%2A> objekt více než jednou.

## <a name="related-rules"></a>Související pravidla
 [CA2000: Uvolňujte objekty před ztrátou oboru](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte implementaci tak, aby nezávisle na cestě kódu byly <xref:System.IDisposable.Dispose%2A> pro objekt volány pouze jednou.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. I v případě, že je známo, že se má <xref:System.IDisposable.Dispose%2A> u objektu bezpečně volat vícenásobně, implementace se může v budoucnu změnit.

## <a name="example"></a>Příklad
 Vnořené `using` příkazy ( `Using` v Visual Basic) mohou způsobit porušení upozornění CA2202. Pokud prostředek IDisposable vnořeného vnitřního `using` příkazu obsahuje prostředek vnějšího `using` příkazu, `Dispose` Metoda vnořeného prostředku uvolní obsažený prostředek. Pokud dojde k této situaci, `Dispose` Metoda vnějšího `using` příkazu se pokusí o odstranění svého prostředku podruhé.

 V následujícím příkladu <xref:System.IO.Stream> je objekt, který je vytvořen v vnějším příkazu Using, vydán na konci vnitřního příkazu Using v metodě Dispose <xref:System.IO.StreamWriter> objektu, který obsahuje `stream` objekt. Na konci vnějšího příkazu se `using` `stream` objekt uvolní podruhé. Druhá verze je porušení CA2202.

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Příklad
 Chcete-li tento problém vyřešit, použijte `try` / `finally` místo vnějšího `using` příkazu blok. V bloku Ujistěte se `finally` , že `stream` prostředek není null.

```
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

## <a name="see-also"></a>Viz také
 <xref:System.IDisposable?displayProperty=fullName>[Vzor Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
