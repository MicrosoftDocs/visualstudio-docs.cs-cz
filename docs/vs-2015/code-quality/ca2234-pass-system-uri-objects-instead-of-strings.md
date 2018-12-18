---
title: 'CA2234: Předejte objekty System.Uri namísto řetězců | Dokumentace Microsoftu'
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
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 83490f93368da777f35544ba09e40bdb5a929f99
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813970"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Předejte objekty System.Uri namísto řetězců
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Je provedeno volání metody, která má řetězcový parametr, jehož název obsahuje "uri", "Uri", "urn", "Urn", "url" nebo "Url"; a deklarující typ metody obsahuje odpovídající přetížení metody, která má <xref:System.Uri?displayProperty=fullName> parametru.

## <a name="rule-description"></a>Popis pravidla
 Název parametru je rozděleno na tokeny, které podle konvence camelCase a potom každý token se zkontroluje, jestli se rovná "uri", "Uri", "urn", "Urn", "url" nebo "Url". Pokud se zjistí shoda, parametr se předpokládá, že představují identifikátor URI (URI). Řetězcová reprezentace identifikátoru URI je náchylná k chybám analýzy a kódování a může vést k ohrožení bezpečnosti. <xref:System.Uri> Třída poskytuje tyto služby bezpečným a zabezpečeným způsobem. Pokud je možnost volby mezi dvě přetížení, které se liší pouze o reprezentaci identifikátoru URI, uživatel by měl vybrat přetížení přijímající <xref:System.Uri> argument.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zavolejte přetížení přijímající <xref:System.Uri> argument.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, je-li parametr řetězec nepředstavuje identifikátor URI.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, `ErrorProne`, který porušuje pravidla a metodu, `SaferWay`, která správně volá <xref:System.Uri> přetížení.

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1057: Řetězcové přetížení identifikátoru URI volá přetížení System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: Vlastnosti identifikátoru URI by neměly být řetězce](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Parametry identifikátoru URI by neměly být řetězce](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Návratové hodnoty identifikátoru URI by neměly být řetězce](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)



