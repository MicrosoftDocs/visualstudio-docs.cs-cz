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
ms.openlocfilehash: e0be715d8aea84fac53ea2a796e71850b961730c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667405"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Neuvolňujte objekty několikrát
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Implementace metody obsahuje cesty kódu, které by mohly způsobit více volání <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> nebo ekvivalent Dispose, jako je například metoda Close () u některých typů na stejném objektu.

## <a name="rule-description"></a>Popis pravidla
 Správně implementovaná <xref:System.IDisposable.Dispose%2A> metoda může být volána několikrát bez vyvolání výjimky. Nicméně to není zaručeno a vyhnout se generování <xref:System.ObjectDisposedException?displayProperty=fullName> byste neměli volat <xref:System.IDisposable.Dispose%2A> více než jednou pro objekt.

## <a name="related-rules"></a>Související pravidla
 [CA2000: Uvolňujte objekty před ztrátou oboru](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte implementaci tak, aby bez ohledu na cestu kódu byla <xref:System.IDisposable.Dispose%2A> pro objekt volána pouze jednou.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. I v případě, že je známo, že <xref:System.IDisposable.Dispose%2A> pro objekt je možné bezpečně volat, implementace se může v budoucnu změnit.

## <a name="example"></a>Příklad
 Vnořené příkazy `using` (`Using` v Visual Basic) mohou způsobit porušení upozornění CA2202. Pokud prostředek IDisposable vnořeného příkazu vnitřní `using` obsahuje prostředek vnějšího příkazu `using`, metoda `Dispose` vnořeného prostředku uvolní obsažený prostředek. Pokud k této situaci dojde, pokusí se metoda `Dispose` vnějšího příkazu `using` uvolnit svůj prostředek podruhé.

 V následujícím příkladu je objekt <xref:System.IO.Stream>, který je vytvořen v vnějším příkazu Using, vydán na konci vnitřního příkazu Using v metodě Dispose objektu <xref:System.IO.StreamWriter>, který obsahuje objekt `stream`. Na konci vnějšího příkazu `using` se objekt `stream` uvolní podruhé. Druhá verze je porušení CA2202.

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
 Chcete-li tento problém vyřešit, použijte místo vnějšího příkazu `using` `try` / `finally` blok. V bloku `finally` zajistěte, aby prostředek `stream` nebyl null.

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
 [vzor Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb) <xref:System.IDisposable?displayProperty=fullName>
