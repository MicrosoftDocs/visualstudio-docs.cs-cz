---
title: 'CA1304: Určete CultureInfo'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2539cef9e6b2fe20513943f686aeaa1ff7a79013
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235104"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Určete CultureInfo

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Kategorie|Microsoft.Globalization|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Metoda nebo konstruktor volá člen, který má přetížení, které přijímá <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> parametr, a metoda nebo konstruktor nevolá přetížení, které <xref:System.Globalization.CultureInfo> přijímá parametr. Toto pravidlo ignoruje volání následujících metod:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Popis pravidla

V případě, <xref:System.IFormatProvider?displayProperty=nameWithType> že objekt nebonenízadán,nemusímítvýchozíhodnota,kterájeposkytnutapřetíženýmčlenem,efekt,kterýchcetevevšechnárodníchprostředích.<xref:System.Globalization.CultureInfo> Kromě toho členové rozhraní .NET zvolí výchozí jazykovou verzi a formátování na základě předpokladů, které nemusí být pro váš kód správné. Chcete-li zajistit, aby kód pro vaše scénáře fungoval podle očekávání, měli byste doručovat informace specifické pro jazykovou verzi podle následujících pokynů:

- Pokud se hodnota zobrazí uživateli, použijte aktuální jazykovou verzi. Viz <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Pokud bude hodnota uložena a bude mít k dispozici software, který je trvale uložený v souboru nebo databázi, použijte invariantní jazykovou verzi. Viz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Pokud neznáte cíl hodnoty, je nutné, aby příjemce dat nebo poskytovatel tuto jazykovou verzi určil.

I v případě, že je výchozí chování přetíženého členu vhodné pro vaše potřeby, je lepší explicitně volat přetížení specifické pro jazykovou verzi, aby váš kód byl vlastní dokument a snadněji se udržoval.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>slouží pouze k načtení lokalizovaných prostředků pomocí instance <xref:System.Resources.ResourceManager?displayProperty=nameWithType> třídy.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, použijte přetížení, které přijímá <xref:System.Globalization.CultureInfo> argument.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Je bezpečné potlačit upozornění z tohoto pravidla, pokud je jisté, že výchozí jazyková verze je správná volba a kde udržovatelnost kódu není důležitou prioritou pro vývoj.

## <a name="example-showing-how-to-fix-violations"></a>Příklad ukazující, jak opravit porušení

V následujícím příkladu `BadMethod` způsobí dvě porušení tohoto pravidla. `GoodMethod`opraví první porušení předáním invariantní jazykové verze k <xref:System.String.Compare%2A?displayProperty=nameWithType>a opraví druhé porušení předáním aktuální jazykové verze do <xref:System.String.ToLower%2A?displayProperty=nameWithType> , protože `string3` se zobrazí uživateli.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Příklad znázorňující formátovaný výstup

Následující příklad ukazuje účinek aktuální jazykové verze ve výchozím nastavení <xref:System.IFormatProvider> , které je vybráno <xref:System.DateTime> typem.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

Tento příklad vytvoří následující výstup:

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>Související pravidla

- [CA1305: Zadat IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Viz také:

- [Použití třídy CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)