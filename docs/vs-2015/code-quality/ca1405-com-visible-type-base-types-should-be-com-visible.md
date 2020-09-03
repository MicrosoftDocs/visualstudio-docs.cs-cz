---
title: 'CA1405: základní typy viditelného typu modelu COM by měly být viditelné modelu COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 779d3ec1ed520d5d48043f90e7cb6272553012a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535041"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Základní typy viditelného typu modelu COM by měly být viditelné modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|DependsOnFix|

## <a name="cause"></a>Příčina
 Viditelný typ objektu součásti modelu COM je odvozen z typu, který není viditelný v modelu COM.

## <a name="rule-description"></a>Popis pravidla
 Pokud viditelný typ modelu COM přidá členy v nové verzi, musí dodržovat přísné pokyny, aby nedošlo k narušení klientů modelu COM, které se váže k aktuální verzi. Typ, který není viditelný v modelu COM, se předpokládá, že při přidávání nových členů není nutné dodržovat pravidla správy verzí modelu COM. Pokud je však viditelný typ modelu COM odvozen z neviditelného typu modelu COM a zpřístupňuje rozhraní třídy <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> nebo <xref:System.Runtime.InteropServices.ClassInterfaceType> (výchozí), všechny veřejné členy základního typu (pokud nejsou výslovně označeny jako model COM neviditelný, který by byl redundantní) zpřístupněny modelu COM. Pokud základní typ přidá nové členy v následné verzi, může dojít k přerušení všech klientů modelu COM, které jsou vázány na rozhraní třídy odvozeného typu. Viditelné typy modelu COM by měly odvozovat pouze z viditelných typů modelu COM, aby se snížila pravděpodobnost poškození klientů modelu COM.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zajistěte, aby základní typy modelu COM byly viditelné nebo aby byl odvozený typ COM neviditelný.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který je v rozporu s pravidlem.

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>Viz také
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>[Představujeme rozhraní třídy, které](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [spolupracuje s nespravovaným kódem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
