---
title: 'CA1303: Nepředávejte literály jako lokalizované parametry | Dokumentace Microsoftu'
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
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d900abe23dab4d950b5790798916fe728a44af4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886559"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Nepředávejte literály jako lokalizované parametry
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategorie|Microsoft.Globalization|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Metoda předává řetězcový literál jako parametr do konstruktoru nebo metody v [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] třídy knihovny a řetězec by měl být lokalizovatelný.

 Toto upozornění je vyvoláno, když řetězcový literál je předán jako hodnotu parametru nebo vlastnost a nejméně jednu z následujících případech má hodnotu true:

-   <xref:System.ComponentModel.LocalizableAttribute> Atribut parametru nebo vlastnosti je nastaven na hodnotu true.

-   Název parametru nebo vlastnosti obsahuje "Text", "Zpráva" nebo "Popisu".

-   Název parametru řetězce, který se předá metodě Console.Write nebo Console.WriteLine je "value" nebo "format".

## <a name="rule-description"></a>Popis pravidla
 Řetězcové literály, které jsou vloženy do zdrojového kódu se obtížně lokalizují.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nahraďte řetězcový literál řetězce načíst prostřednictvím instance <xref:System.Resources.ResourceManager> třídy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, pokud knihovny kódu nesmí být lokalizována, nebo pokud řetězec není vystavený koncovému uživateli nebo vývojáři pomocí knihovny kódu.

 Uživatelům můžete eliminovat šumu proti metody, které by neměly být předány lokalizované řetězce přejmenování parametru nebo vlastnost s názvem nebo označením tyto položky jako podmíněný.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která vyvolá výjimku, pokud některý z jeho dva argumenty jsou mimo rozsah. Pro první argument je předán konstruktoru výjimka řetězcový literál, který porušuje tato pravidla. Pro druhý argument je předán konstruktoru správně načtené pomocí řetězce <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Viz také
 [Prostředky v desktopových aplikacích](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



