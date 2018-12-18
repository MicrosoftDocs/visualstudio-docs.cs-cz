---
title: 'CA1304: Zadejte možnosti CultureInfo'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe02dd66b523e6ee82c5e1a2051f3a68839957d4
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546185"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Zadejte možnosti CultureInfo

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Kategorie|Microsoft.Globalization|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina

Metoda nebo konstruktor volá člen, který má přetížení přijímající <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> parametr a tato metoda nebo konstruktor nevolá přetížení přebírající <xref:System.Globalization.CultureInfo> parametru. Toto pravidlo ignoruje volání těchto metod:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Popis pravidla

Když <xref:System.Globalization.CultureInfo> nebo <xref:System.IFormatProvider?displayProperty=nameWithType> objektu není zadán, výchozí hodnota zadaná pomocí přetíženého členu nemusí mít ve všech národních prostředích požadovaný efekt. Kromě toho členy rozhraní .NET Framework zvolte výchozí jazykovou verzi a formátování podle předpokladů, které nemusí být správná pro váš kód. K zajištění, že kód funguje podle očekávání pro vaše scénáře, by měla poskytnout informace specifické jazykové verze podle následujících pokynů:

- Pokud uživateli se zobrazí hodnotu, použijte aktuální jazykové verze. Zobrazit <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Pokud hodnota bude uložen a přístupný softwarem, to znamená, trvale uložena do souboru nebo databáze, pomocí neutrální jazykové verze. Zobrazit <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Pokud si nejste jisti cílové hodnoty, mají příjemce dat nebo zprostředkovatele zadejte jazykovou verzi.

I v případě, že výchozí chování přetíženého členu je vhodné pro vaše potřeby, je lepší explicitně volat přetížení specifické pro jazykovou verzi tak, aby váš kód je držitelem dokumentů a snadněji zachována.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> slouží jenom k načítání lokalizovaných prostředků pomocí instance <xref:System.Resources.ResourceManager?displayProperty=nameWithType> třídy.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, použijte přetížení přijímající <xref:System.Globalization.CultureInfo> argument.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Je bezpečné potlačit upozornění tohoto pravidla, když je jisté, že výchozí jazykovou verzi je správnou volbou a udržovatelnosti kódu není důležité vývojové prioritou.

## <a name="example-showing-how-to-fix-violations"></a>Příklad ukazuje, jak vyřešit porušení

V následujícím příkladu `BadMethod` způsobí, že dvě porušení tohoto pravidla. `GoodMethod` opravuje první porušení předáním invariantní jazyková verze <xref:System.String.Compare%2A?displayProperty=nameWithType>a předáním aktuální jazyková verze opravuje druhý porušení <xref:System.String.ToLower%2A?displayProperty=nameWithType> protože `string3` se zobrazí uživateli.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Příklad zobrazující formátovaný výstup

Následující příklad ukazuje účinek aktuální jazykovou verzi na výchozí <xref:System.IFormatProvider> , která se zvolila <xref:System.DateTime> typu.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

Tento příklad vytvoří následující výstup:

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>Související pravidla

- [CA1305: Zadejte možnosti IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Viz také:

- [Pomocí třídy CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)