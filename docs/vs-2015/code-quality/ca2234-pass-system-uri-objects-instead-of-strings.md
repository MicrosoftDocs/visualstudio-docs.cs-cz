---
title: 'CA2234: předejte objekty System. URI místo řetězců | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ce5c076260886def089118a4d7211d75e0185c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545207"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Předejte objekty System.Uri namísto řetězců
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Bylo provedeno volání metody, která má parametr řetězce, jehož název obsahuje "URI", "URI", "urn", "urn", "URL" nebo "URL"; a deklarující typ metody obsahuje odpovídající přetížení metody, která má <xref:System.Uri?displayProperty=fullName> parametr.

## <a name="rule-description"></a>Popis pravidla
 Název parametru je rozdělen na tokeny založené na konvenci ve stylu CamelCase (velká a malá písmena) a pak je zkontrolován každý token, aby bylo možné zjistit, zda se rovná "URI", "URI", "urn", "urn", "URL" nebo "URL". Pokud existuje shoda, předpokládá se, že parametr představuje identifikátor URI (Uniform Resource Identifier). Řetězcová reprezentace identifikátoru URI je náchylná k chybám analýzy a kódování a může vést k ohrožení bezpečnosti. <xref:System.Uri>Třída poskytuje tyto služby bezpečným a bezpečným způsobem. Pokud existuje volba mezi dvěma přetíženími, které se liší pouze v případě reprezentace identifikátoru URI, uživatel by měl zvolit přetížení, které přijímá <xref:System.Uri> argument.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zavolejte přetížení, které přijímá <xref:System.Uri> argument.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud parametr řetězce nepředstavuje identifikátor URI, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, `ErrorProne` , která porušuje pravidlo a metodu, `SaferWay` ,, která správně volá <xref:System.Uri> přetížení.

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1057: Přetížení řetězce identifikátoru URI volají přetížení System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: Vlastnosti identifikátoru URI by neměly být řetězce](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Parametry identifikátoru URI by neměly být řetězce](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Návratové hodnoty identifikátoru URI by neměly být řetězce](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
