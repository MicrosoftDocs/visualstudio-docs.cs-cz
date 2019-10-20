---
title: 'CA1053: statické typy držitelů by neměly mít konstruktory | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7de098d264dbdd6d7d9daea385de2e03d4e1ba35
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653827"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: Statický vlastník typů by neměl mít konstruktory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný nebo vnořený veřejný typ deklaruje pouze statické členy a má veřejný nebo chráněný výchozí konstruktor.

## <a name="rule-description"></a>Popis pravidla
 Konstruktor není nutný, protože volání statických členů nevyžaduje instanci typu. Vzhledem k tomu, že typ nemá nestatické členy, vytvoření instance neposkytuje přístup k žádnému z členů typu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte výchozí konstruktor nebo jej nastavte jako soukromý.

> [!NOTE]
> Některé kompilátory automaticky vytvoří veřejný výchozí konstruktor, pokud typ nedefinuje žádné konstruktory. Pokud se jedná o případ s vaším typem, přidejte privátní výchozí konstruktor, abyste vyloučili porušení.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Přítomnost konstruktoru naznačuje, že typ není statický typ.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který je v rozporu s tímto pravidlem. Všimněte si, že ve zdrojovém kódu není žádný výchozí konstruktor. Když je tento kód zkompilován do sestavení, C# kompilátor vloží výchozí konstruktor, který porušuje toto pravidlo. Chcete-li tento problém opravit, deklarujte privátní konstruktor.

 [!code-csharp[FxCop.Design.StaticTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes/cs/FxCop.Design.StaticTypes.cs#1)]
