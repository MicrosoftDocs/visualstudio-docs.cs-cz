---
title: 'CA1064: výjimky by měly být veřejné | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5e704793aeef211ccabd4f2c9993834af205a14
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663628"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Výjimky by měly být veřejné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Kategorie|Microsoft. Design|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Výjimka, která není veřejná, je odvozena přímo z <xref:System.Exception>, <xref:System.SystemException> nebo <xref:System.ApplicationException>.

## <a name="rule-description"></a>Popis pravidla
 Vnitřní výjimka je viditelná pouze uvnitř vlastního vnitřního oboru. Jakmile výjimka přesáhne hranice vnitřního rozsahu, lze pro zachycení výjimky použít pouze základní výjimku. Pokud je interní výjimka děděna z <xref:System.Exception>, <xref:System.SystemException> nebo <xref:System.ApplicationException>, externí kód nebude mít dostatek informací, aby věděl, co s výjimkou dělat.

 Nicméně, pokud má kód veřejnou výjimku, která je později použita jako základ pro vnitřní výjimku, je vhodné předpokládat, že kód bude další, je možné něco inteligentního se základní výjimkou. Pro veřejnou výjimku bude k dispozici více informací, než jaké poskytuje T:System.Exception, T:System.SystemException nebo T:System.ApplicationException.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Udělejte výjimku jako veřejnou, nebo odvodit vnitřní výjimku z veřejné výjimky, která není <xref:System.Exception>, <xref:System.SystemException> nebo <xref:System.ApplicationException>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit zprávu z tohoto pravidla, pokud jste si jistí, že se soukromá výjimka zachytí v rámci vlastního vnitřního oboru.

## <a name="example"></a>Příklad
 Toto pravidlo je vyvoláno v prvním příkladu metody FirstCustomException, protože třída výjimky je odvozena přímo z výjimky a je interní. Pravidlo se neaktivuje u třídy SecondCustomException, protože i když třída je odvozená také přímo z výjimky, třída je deklarována jako veřejná. Třetí třída také neaktivuje pravidlo, protože neodvozuje přímo z <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName> nebo <xref:System.ApplicationException?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.design.exceptionsshouldbepublic.ca1064/cs/ca1064 - exceptionsshouldbepublic.cs#1)]
