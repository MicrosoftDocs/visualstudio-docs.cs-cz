---
title: 'CA1301: Vyhněte se duplicitním akcelerátorům | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 647fef2968971cddb6a14cc19e53eed979b9c151
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661523"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Vyhněte se duplicitním akcelerátorům
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Kategorie|Microsoft. Globalization|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Typ rozšiřuje <xref:System.Windows.Forms.Control?displayProperty=fullName> a obsahuje dva nebo více ovládacích prvků nejvyšší úrovně, které mají stejné přístupové klíče, které jsou uloženy v souboru prostředků.

## <a name="rule-description"></a>Popis pravidla
 Přístupová klávesa neboli akcelerátor umožňuje klávesnici přístup k ovládacímu prvku pomocí klávesy ALT. Když má více ovládacích prvků duplicitní přístupové klávesy, není chování přístupové klávesy dobře definováno. Uživatel pravděpodobně nebude moci získat přístup k zamýšlenému ovládacímu prvku pomocí přístupového klíče a jiného ovládacího prvku, než který je určen, může být povolen.

 Aktuální implementace tohoto pravidla ignoruje položky nabídky. Nicméně položky nabídky ve stejné podnabídce by neměly mít stejné přístupové klíče.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, definujte jedinečné přístupové klíče pro všechny ovládací prvky.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje minimální formulář, který obsahuje dva ovládací prvky, které mají stejné přístupové klíče. Klíče jsou uloženy v souboru prostředků, který není zobrazen. jejich hodnoty se ale zobrazí v `checkBox.Text` řádky s komentářem. Chování duplicitních akcelerátorů se dá prozkoumat vyvoláním `checkBox.Text` řádků s jejich přidanými protějšky. V tomto případě se ale v tomto příkladu z pravidla negeneruje upozornění.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>Viz také
 [prostředky <xref:System.Resources.ResourceManager?displayProperty=fullName> v aplikacích klasické pracovní plochy](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
