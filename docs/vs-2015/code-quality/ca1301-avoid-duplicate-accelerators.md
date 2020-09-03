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
ms.openlocfilehash: 772c9bee3f43c42701bfa460c622f4a225ec59cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539175"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Vyhněte se duplicitním akcelerátorům
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Kategorie|Microsoft. Globalization|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Typ rozšiřuje <xref:System.Windows.Forms.Control?displayProperty=fullName> a obsahuje dva nebo více ovládacích prvků nejvyšší úrovně, které mají stejné přístupové klíče, které jsou uloženy v souboru prostředků.

## <a name="rule-description"></a>Popis pravidla
 Přístupová klávesa neboli akcelerátor umožňuje klávesnici přístup k ovládacímu prvku pomocí klávesy ALT. Když má více ovládacích prvků duplicitní přístupové klávesy, není chování přístupové klávesy dobře definováno. Uživatel pravděpodobně nebude moci získat přístup k zamýšlenému ovládacímu prvku pomocí přístupového klíče a jiného ovládacího prvku, než který je určen, může být povolen.

 Aktuální implementace tohoto pravidla ignoruje položky nabídky. Nicméně položky nabídky ve stejné podnabídce by neměly mít stejné přístupové klíče.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, definujte jedinečné přístupové klíče pro všechny ovládací prvky.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje minimální formulář, který obsahuje dva ovládací prvky, které mají stejné přístupové klíče. Klíče jsou uloženy v souboru prostředků, který není zobrazen. jejich hodnoty se ale zobrazí v řádcích s komentářem `checkBox.Text` . Chování duplicitních akcelerátorů lze prozkoumat výměnou `checkBox.Text` řádků pomocí jejich přihlašování ke svým protějškům. V tomto případě se ale v tomto příkladu z pravidla negeneruje upozornění.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.Resources.ResourceManager?displayProperty=fullName>[Prostředky v aplikacích klasické pracovní plochy](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
