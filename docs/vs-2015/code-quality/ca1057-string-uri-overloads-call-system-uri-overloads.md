---
title: 'CA1057: řetězcové přetížení identifikátoru URI volá přetížení System. URI | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba7e7de4f3ef6336ed3d82dc1e1da03ec0bf2575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603081"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Řetězcové přetížení identifikátoru URI volá přetížení System.Uri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Typ deklaruje přetížení metod, které se liší pouze nahrazením řetězcového parametru parametrem <xref:System.Uri?displayProperty=fullName> a přetížení, které přijímá řetězcový parametr, nevolá přetížení, které přijímá parametr <xref:System.Uri>.

## <a name="rule-description"></a>Popis pravidla
 Vzhledem k tomu, že přetížení se liší pouze parametrem String/<xref:System.Uri>, předpokládá se, že řetězec představuje identifikátor URI (Uniform Resource Identifier). Řetězcová reprezentace identifikátoru URI je náchylná k chybám analýzy a kódování a může vést k ohrožení bezpečnosti. Třída <xref:System.Uri> poskytuje tyto služby bezpečným a bezpečným způsobem. Chcete-li těžit výhody třídy <xref:System.Uri>, přetížení řetězce by mělo volat přetížení <xref:System.Uri> pomocí řetězcového argumentu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Znovu Implementujte metodu, která používá řetězcovou reprezentaci identifikátoru URI, aby vytvořila instanci <xref:System.Uri> třídy pomocí řetězcového argumentu a poté předá objekt <xref:System.Uri> přetížení, které má parametr <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud parametr řetězce nepředstavuje identifikátor URI, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
 Následující příklad ukazuje správně implementované přetížení řetězce.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2234: Předejte objekty System.Uri namísto řetězců](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: Vlastnosti identifikátoru URI by neměly být řetězce](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Parametry identifikátoru URI by neměly být řetězce](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Návratové hodnoty identifikátoru URI by neměly být řetězce](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
