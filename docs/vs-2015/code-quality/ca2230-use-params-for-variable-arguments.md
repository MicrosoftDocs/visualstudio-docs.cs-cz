---
title: 'CA2230: použijte parametry pro proměnné argumenty | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a690544a7ed03094587a2aaf1c44b7ed68e8f2a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662832"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Použijte parametry pro proměnné argumenty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Kategorie|Microsoft. Usage|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný typ obsahuje veřejnou nebo chráněnou metodu, která používá konvenci volání `VarArgs`.

## <a name="rule-description"></a>Popis pravidla
 Konvence volání `VarArgs` se používá s některými definicemi metod, které přebírají proměnný počet parametrů. Metoda používající konvenci volání `VarArgs` není kompatibilní se specifikací CLS (Common Language Specification) a nemusí být přístupná v různých programovacích jazycích.

 V C#je konvence volání `VarArgs` použita, když seznam parametrů metody končí klíčovým slovem `__arglist`. Visual Basic nepodporuje konvenci volání `VarArgs` a vizuál C++ umožňuje jeho použití pouze v nespravovaném kódu, který používá notaci elipsy `...`.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla v C#, použijte klíčové slovo [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) namísto `__arglist`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dvě metody, jeden, který porušuje pravidlo a jeden, který splňuje pravidlo.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Viz také
 nezávislá <xref:System.Reflection.CallingConventions?displayProperty=fullName> [jazyka a součásti nezávislé na jazyce](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
