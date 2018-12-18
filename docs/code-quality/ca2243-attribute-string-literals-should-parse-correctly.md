---
title: 'CA2243: Literály řetězce atributu by se měly správně analyzovat'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c6808520f3b28a2da8421394619550166d88d52d
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551935"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Literály řetězce atributu by se měly správně analyzovat

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Parametr literál řetězce atributu nesprávně analyzuje adresu URL, identifikátor GUID nebo verzi.

## <a name="rule-description"></a>Popis pravidla
 Protože atributy jsou odvozeny z <xref:System.Attribute?displayProperty=fullName>a atributy se používají v době kompilace, jejich konstruktory mohou být předány pouze konstantní hodnoty. Parametry atributu, které musí představovat adresy URL, identifikátory GUID a verze nemůže být typu <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, a <xref:System.Version?displayProperty=fullName>, protože tyto typy nemůže být reprezentovaná jako konstanty. Místo toho se musí být reprezentována řetězce.

 Protože parametr je zadán jako řetězec, je možné, že parametr nesprávně naformátovanou může předávat v době kompilace.

 Toto pravidlo používá pojmenování heuristiku k nalezení parametry, které představují identifikátor URI (URI), verze nebo globálně jedinečný identifikátor (GUID) a ověří, zda předaná hodnota je správný.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Změňte parametr řetězec správně vytvořená adresa URL, identifikátor GUID nebo verzi.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, je-li parametr nepředstavuje adresu URL, identifikátor GUID nebo verzi.

## <a name="example"></a>Příklad
 Následující příklad ukazuje kód pro AssemblyFileVersionAttribute, který porušuje tato pravidla.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

 Toto pravidlo aktivuje následující parametry:

- Parametry, které obsahují 'version' a nejde ho parsovat na System.Version.

- Parametry, které obsahují 'guid' a nejde ho parsovat na System.Guid.

- Parametry, které obsahuje "uri", "urn" nebo "url" a nelze jej analyzovat na System.Uri.

## <a name="see-also"></a>Viz také:

- [CA1054: Parametry identifikátoru URI by neměly být řetězce](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)