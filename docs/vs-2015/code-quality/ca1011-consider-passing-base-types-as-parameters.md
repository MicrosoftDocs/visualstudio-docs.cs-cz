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
ms.openlocfilehash: 3968d81e8ee18b4b0a56bed50f7aa1f121e1c074
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663243"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Zvažte předání základních typů jako parametrů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Deklarace metody obsahuje formální parametr, který je odvozeným typem, a metoda volá pouze členy základního typu parametru.

## <a name="rule-description"></a>Popis pravidla
 Je-li v deklaraci metody zadán jako parametr základní typ, lze jako příslušný argument k metodě předat kterýkoliv typ odvozený z tohoto základního typu. Pokud je argument použit uvnitř těla metody, konkrétní metoda, která je spuštěna, závisí na typu argumentu. Pokud nejsou vyžadovány další funkce, které jsou poskytovány odvozeným typem, použití základního typu umožňuje širší použití metody.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte typ parametru na jeho základní typ.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění.

- Pokud metoda vyžaduje konkrétní funkce, které jsou poskytovány odvozeným typem

   \- nebo-

- aby bylo možné vyhovět, že pouze odvozený typ nebo více odvozený typ, je předán metodě.

  V těchto případech bude kód robustnější z důvodu kontroly silného typu, který je poskytován kompilátorem a modulem runtime.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu `ManipulateFileStream`, která se dá použít jenom s objektem <xref:System.IO.FileStream>, který porušuje toto pravidlo. Druhá metoda, `ManipulateAnyStream`, splňuje pravidlo tím, že nahrazuje parametr <xref:System.IO.FileStream> pomocí <xref:System.IO.Stream>.

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1059: Členové by neměli zveřejňovat určité konkrétní typy](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
