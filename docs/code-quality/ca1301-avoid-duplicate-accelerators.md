---
title: 'CA1301: Vyhněte se duplicitním akcelerátorům'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f50be12f4d601161ec20659bbb6b710e5a7cf24
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235168"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Vyhněte se duplicitním akcelerátorům

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Kategorie|Microsoft.Globalization|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Typ rozšiřuje <xref:System.Windows.Forms.Control?displayProperty=fullName> a obsahuje dva nebo více ovládacích prvků nejvyšší úrovně, které mají stejné přístupové klíče, které jsou uloženy v souboru prostředků.

## <a name="rule-description"></a>Popis pravidla

Přístupový klíč, označovaný také jako akcelerátor, umožňuje přístup k ovládacímu prvku přes klávesnici pomocí klávesy **ALT** . Pokud má více ovládacích prvků stejný přístupový klíč, chování přístupového klíče není správně definováno. Uživatel možná nebude mít přístup k zamýšlenému ovládacímu prvku pomocí přístupového klíče a jiný ovládací prvek, který je určený k dispozici, může být povolen.

Aktuální implementace tohoto pravidla ignoruje položky nabídky. Nicméně položky nabídky ve stejné podnabídce by neměly mít stejné přístupové klíče.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, definujte jedinečné přístupové klíče pro všechny ovládací prvky.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje minimální formulář, který obsahuje dva ovládací prvky, které mají stejné přístupové klíče. Klíče jsou uloženy v souboru prostředků, který není zobrazen. Jejich hodnoty se ale zobrazí v `checkBox.Text` řádcích s komentářem. Chování duplicitních akcelerátorů lze prozkoumat výměnou `checkBox.Text` řádků pomocí jejich přihlašování ke svým protějškům. V tomto případě se ale v tomto příkladu z pravidla negeneruje upozornění.

[!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>Viz také:

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Prostředky v desktopových aplikacích](/dotnet/framework/resources/index)