---
title: 'CA2230: Použijte parametry pro proměnné argumenty | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ad0f43ac18c39d1dfdf6464e5cd260b669e1a0da
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892724"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Použijte parametry pro proměnné argumenty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Kategorie|Microsoft.Usage|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný typ obsahuje veřejná nebo chráněná metoda, která používá `VarArgs` konvence volání.

## <a name="rule-description"></a>Popis pravidla
 `VarArgs` Konvence volání se používá některé metody definicemi přijímajícími proměnný počet parametrů. Metoda použití `VarArgs` konvence volání není specifikace CLS (Common Language) předpisy a nemusí být přístupné napříč programovacími jazyky.

 V jazyce C# `VarArgs` konvence volání se používá při seznamu parametrů metod končí `__arglist` – klíčové slovo. Jazyk Visual Basic nepodporuje `VarArgs` volání konvence a Visual C++ umožňuje použití pouze v nespravovaném kódu, který používá tři tečky `...` zápis.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla v jazyce C#, použijte [params](http://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) – klíčové slovo místo `__arglist`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dva způsoby, ten, který porušuje pravidla a ten, který splňuje pravidlo.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [Jazyková nezávislost a jazykově nezávislé komponenty](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



