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
ms.openlocfilehash: ce66e04272618b9df2ab1957af305bb9bf40ee9c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540358"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Použijte parametry pro proměnné argumenty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Kategorie|Microsoft. Usage|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Veřejný nebo chráněný typ obsahuje veřejnou nebo chráněnou metodu, která používá `VarArgs` konvenci volání.

## <a name="rule-description"></a>Popis pravidla
 `VarArgs`Konvence volání se používá s určitými definicemi metod, které přebírají proměnný počet parametrů. Metoda používající `VarArgs` konvenci volání není kompatibilní se specifikací CLS (Common Language Specification) a nemusí být přístupná v různých programovacích jazycích.

 V jazyce C# se `VarArgs` konvence volání používá v případě, že seznam parametrů metody končí `__arglist` klíčovým slovem. Visual Basic nepodporuje `VarArgs` konvenci volání a Visual C++ umožňuje její použití pouze v nespravovaném kódu, který používá tři `...` tečky.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla v jazyce C#, použijte [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) místo parametru klíčové slovo params `__arglist` .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dvě metody, jeden, který porušuje pravidlo a jeden, který splňuje pravidlo.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>[Jazyková nezávislost a jazykově nezávislé komponenty](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
