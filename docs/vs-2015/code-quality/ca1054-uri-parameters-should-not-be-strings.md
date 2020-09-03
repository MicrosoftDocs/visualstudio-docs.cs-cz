---
title: 'CA1054: parametry identifikátoru URI by neměly být řetězce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: babef652bbfa55d6549cf0e43ddae0920b3ff302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539487"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: Parametry identifikátoru URI by neměly být řetězce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Typ deklaruje metodu s parametrem řetězce, jehož název obsahuje "URI", "URI", "urn", "urn", "URL" nebo "URL" a typ nedeklaruje odpovídající přetížení, které přijímá <xref:System.Uri?displayProperty=fullName> parametr.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo rozdělí název parametru na tokeny založené na konvenci ve stylu CamelCase (velká a malá písmena) a zkontroluje, jestli každý token odpovídá "URI", "URI", "urn", "urn", "URL" nebo "URL". Pokud existuje shoda, pravidlo předpokládá, že parametr představuje identifikátor URI (Uniform Resource Identifier). Řetězcová reprezentace identifikátoru URI je náchylná k chybám analýzy a kódování a může vést k ohrožení bezpečnosti. Pokud metoda přebírá řetězcovou reprezentaci identifikátoru URI, měla by být poskytnuta odpovídající přetížení, které přebírá instanci <xref:System.Uri> třídy, která poskytuje tyto služby bezpečným a zabezpečeným způsobem.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte parametr na <xref:System.Uri> typ; jedná se o zásadní změnu. Případně zadejte přetížení metody, která přijímá <xref:System.Uri> parametr. Jedná se o nepřerušenou změnu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud parametr nepředstavuje identifikátor URI, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, `ErrorProne` , který porušuje toto pravidlo, a typ, `SaferWay` který splňuje pravidlo.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1056: Vlastnosti identifikátoru URI by neměly být řetězce](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055: Návratové hodnoty identifikátoru URI by neměly být řetězce](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Předejte objekty System.Uri namísto řetězců](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: Přetížení řetězce identifikátoru URI volají přetížení System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
