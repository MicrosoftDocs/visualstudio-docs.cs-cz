---
title: 'CA1026: výchozí parametry by neměly být použity | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a63d6e788dd1722d0c593469b225a4f1aeb4738d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548438"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Neměly by být použity výchozí parametry
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Externě viditelný typ obsahuje externě viditelnou metodu, která používá výchozí parametr.

## <a name="rule-description"></a>Popis pravidla
 Metody používající výchozí parametry jsou povoleny v rámci specifikace CLS (Common Language Specification); specifikace CLS však umožňuje kompilátorům ignorovat hodnoty, které jsou přiřazeny těmto parametrům. Kód, který je napsán pro kompilátory, které ignorují výchozí hodnoty parametrů, musí explicitně zadat argumenty pro každý výchozí parametr. Chcete-li zachovat chování, které chcete v programovacích jazycích, metody, které používají výchozí parametry, by měly být nahrazeny přetíženími metod, které poskytují výchozí parametry.

 Kompilátor při přístupu ke spravovanému kódu ignoruje hodnoty výchozích parametrů pro spravované rozšíření pro C++. Kompilátor Visual Basic podporuje metody, které mají výchozí parametry, které používají klíčové slovo [Optional](https://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) .

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nahraďte metodu, která používá výchozí parametry, pomocí přetížení metod, které poskytují výchozí parametry.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která používá výchozí parametry a přetížené metody, které poskytují ekvivalentní funkce.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1025: Nahraďte opakované argumenty polem parametrů](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Viz také
 [Jazyková nezávislost a jazykově nezávislé komponenty](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
