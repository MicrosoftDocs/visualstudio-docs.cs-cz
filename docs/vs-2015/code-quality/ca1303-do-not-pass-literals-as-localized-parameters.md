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
ms.openlocfilehash: f3ad1f56215d002c03d346b38ce6155e8df7412b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539110"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Nepředávejte literály jako lokalizované parametry
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategorie|Microsoft. Globalization|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Metoda předává řetězcový literál jako parametr konstruktoru nebo metodě v [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] knihovně tříd a tento řetězec by měl být Lokalizovatelný.

 Toto upozornění je vyvoláno, když je řetězcový literál předán jako hodnota parametru nebo vlastnosti a jeden nebo více z následujících případů je pravda:

- <xref:System.ComponentModel.LocalizableAttribute>Atribut parametru nebo vlastnosti je nastaven na hodnotu true.

- Název parametru nebo vlastnosti obsahuje text "text", "zpráva" nebo "titulek".

- Název řetězcového parametru, který je předán metodě Console. Write nebo Console. WriteLine, je buď hodnota, nebo formát.

## <a name="rule-description"></a>Popis pravidla
 Řetězcové literály, které jsou vloženy ve zdrojovém kódu, je obtížné lokalizovat.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nahraďte řetězcový literál řetězcem načteným prostřednictvím instance <xref:System.Resources.ResourceManager> třídy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla, pokud knihovna kódu nebude lokalizována nebo pokud není řetězec vystaven koncovému uživateli nebo vývojáři pomocí knihovny kódu.

 Uživatelé mohou odstranit šum proti metodám, které by neměly být předány lokalizované řetězce buď přejmenováním parametru nebo vlastnosti s názvem nebo označením těchto položek jako podmíněné.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která vyvolá výjimku, pokud některý z jejích dvou argumentů je mimo rozsah. Pro první argument je konstruktoru výjimky předán literální řetězec, který porušuje toto pravidlo. Pro druhý argument je konstruktor správně předán pomocí řetězce načteného prostřednictvím <xref:System.Resources.ResourceManager> .

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Viz také
 [Prostředky v aplikacích klasické pracovní plochy](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
