---
title: 'CA2216: typy na jedno použití by měly deklarovat finalizační metodu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5268cb90544088742c6fda7c751bab943503cacc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534469"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: Uvolnitelné typy by měly deklarovat finalizační metodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Typ, který implementuje <xref:System.IDisposable?displayProperty=fullName> a obsahuje pole, která navrhují použití nespravovaných prostředků, neimplementuje finalizační metodu, jak je popsáno v <xref:System.Object.Finalize%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Popis pravidla
 Porušení tohoto pravidla je hlášeno, pokud typ mimo použití obsahuje pole následujících typů:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, implementujte finalizační metodu, která volá vaši <xref:System.IDisposable.Dispose%2A> metodu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla, pokud typ neimplementuje <xref:System.IDisposable> pro účely uvolnění nespravovaných prostředků.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který je v rozporu s tímto pravidlem.

 [!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DisposeNoFinalize/cs/FxCop.Usage.DisposeNoFinalize.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2115: Volejte GC.KeepAlive při použití nativních prostředků](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Volejte správně GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA1049: Typy, které vlastní nativní prostředky, by měly být uvolnitelné](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>Viz také
 <xref:System.IDisposable?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 [Vzor pro metodu Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
