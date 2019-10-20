---
title: 'CA1303: nepředávejte literály jako lokalizované parametry | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ce85a3a933d9453c63ef118d5dfd9e0b17cbf130
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661450"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Nepředávejte literály jako lokalizované parametry
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategorie|Microsoft. Globalization|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Metoda předává řetězcový literál jako parametr konstruktoru nebo metodě v knihovně tříd [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] a tento řetězec by měl být Lokalizovatelný.

 Toto upozornění je vyvoláno, když je řetězcový literál předán jako hodnota parametru nebo vlastnosti a jeden nebo více z následujících případů je pravda:

- Atribut <xref:System.ComponentModel.LocalizableAttribute> parametru nebo vlastnosti je nastaven na hodnotu true.

- Název parametru nebo vlastnosti obsahuje text "text", "zpráva" nebo "titulek".

- Název řetězcového parametru, který je předán metodě Console. Write nebo Console. WriteLine, je buď hodnota, nebo formát.

## <a name="rule-description"></a>Popis pravidla
 Řetězcové literály, které jsou vloženy ve zdrojovém kódu, je obtížné lokalizovat.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nahraďte řetězcový literál řetězcem načteným pomocí instance třídy <xref:System.Resources.ResourceManager>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla, pokud knihovna kódu nebude lokalizována nebo pokud není řetězec vystaven koncovému uživateli nebo vývojáři pomocí knihovny kódu.

 Uživatelé mohou odstranit šum proti metodám, které by neměly být předány lokalizované řetězce buď přejmenováním parametru nebo vlastnosti s názvem nebo označením těchto položek jako podmíněné.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která vyvolá výjimku, pokud některý z jejích dvou argumentů je mimo rozsah. Pro první argument je konstruktoru výjimky předán literální řetězec, který porušuje toto pravidlo. Pro druhý argument je konstruktor správně předán řetězec načtený pomocí <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Viz také
 [Prostředky v desktopových aplikacích](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
