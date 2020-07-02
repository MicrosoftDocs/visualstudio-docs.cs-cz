---
title: 'CA1011: Zvažte předání základních typů jako parametrů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f689dfd6c1d39bbd03d522a33ed8c5639a3da9f8
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545480"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Zvažte předání základních typů jako parametrů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Deklarace metody obsahuje formální parametr, který je odvozeným typem, a metoda volá pouze členy základního typu parametru.

## <a name="rule-description"></a>Popis pravidla
 Je-li v deklaraci metody zadán jako parametr základní typ, lze jako příslušný argument k metodě předat kterýkoliv typ odvozený z tohoto základního typu. Pokud je argument použit uvnitř těla metody, konkrétní metoda, která je spuštěna, závisí na typu argumentu. Pokud nejsou vyžadovány další funkce, které jsou poskytovány odvozeným typem, použití základního typu umožňuje širší použití metody.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte typ parametru na jeho základní typ.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění.

- Pokud metoda vyžaduje konkrétní funkce, které jsou poskytovány odvozeným typem

   \-ani

- aby bylo možné vyhovět, že pouze odvozený typ nebo více odvozený typ, je předán metodě.

  V těchto případech bude kód robustnější z důvodu kontroly silného typu, který je poskytován kompilátorem a modulem runtime.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, `ManipulateFileStream` , která se dá použít jenom s <xref:System.IO.FileStream> objektem, který porušuje toto pravidlo. Druhá metoda, `ManipulateAnyStream` splňuje pravidlo tím, že nahradí <xref:System.IO.FileStream> parametr pomocí <xref:System.IO.Stream> .

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1059: Členy by neměly zveřejňovat určité konkrétní typy](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
