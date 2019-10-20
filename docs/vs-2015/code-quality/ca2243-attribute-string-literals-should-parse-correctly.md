---
title: 'CA2243: řetězcové literály atributu by se měly správně analyzovat | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 62a2adc6f01e5cb26a6af26d71a124f8b81e07fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671967"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Literály řetězce atributu by se měly správně analyzovat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Parametr řetězcového literálu atributu se neanalyzuje správně pro adresu URL, identifikátor GUID nebo verzi.

## <a name="rule-description"></a>Popis pravidla
 Vzhledem k tomu, že atributy jsou odvozeny z <xref:System.Attribute?displayProperty=fullName> a atributy jsou použity v době kompilace, lze do jejich konstruktorů předat pouze konstantní hodnoty. Parametry atributů, které musí představovat adresy URL, identifikátory GUID a verze, nelze zadat jako <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName> a <xref:System.Version?displayProperty=fullName>, protože tyto typy nemohou být reprezentovány jako konstanty. Místo toho musí být reprezentovány pomocí řetězců.

 Vzhledem k tomu, že parametr je zadán jako řetězec, je možné předat nesprávně naformátovaný parametr v době kompilace.

 Toto pravidlo používá heuristickou pojmenování k nalezení parametrů, které reprezentují identifikátor URI (Uniform Resource Identifier), globálně jedinečného identifikátoru (GUID) nebo verzi a ověřuje, že je předaná hodnota správná.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Změňte řetězec parametru na správně vytvořenou adresu URL, identifikátor GUID nebo verzi.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud parametr nepředstavuje adresu URL, identifikátor GUID ani verzi, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
 Následující příklad ukazuje kód pro AssemblyFileVersionAttribute, který porušuje toto pravidlo.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 Toto pravidlo se aktivuje následujícím způsobem:

- Parametry obsahující ' Version ' a nelze je analyzovat na System. Version.

- Parametry obsahující identifikátor GUID a nelze je analyzovat na System. GUID.

- Parametry obsahující ' URI ', ' urn ' nebo ' URL ' a nelze je analyzovat na System. URI.

## <a name="see-also"></a>Viz také
 [CA1054: Parametry identifikátoru URI by neměly být řetězce](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
