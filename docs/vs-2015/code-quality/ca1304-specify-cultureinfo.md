---
title: 'CA1304: zadejte CultureInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 202f3759026bbedd5e99e94bba76e956b83357b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661460"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Zadejte možnosti CultureInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Kategorie|Microsoft. Globalization|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Metoda nebo konstruktor volá člen, který má přetížení, které přijímá parametr <xref:System.Globalization.CultureInfo?displayProperty=fullName> a metoda nebo konstruktor nevolá přetížení, které přijímá parametr <xref:System.Globalization.CultureInfo>. Toto pravidlo ignoruje volání následujících metod:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Popis pravidla
 Pokud není zadán objekt <xref:System.Globalization.CultureInfo> nebo <xref:System.IFormatProvider?displayProperty=fullName>, výchozí hodnota, která je poskytnuta přetíženým členem, nemusí mít ve všech národních prostředích požadovaný efekt. @No__t_0 členy také zvolí výchozí jazykovou verzi a formátování na základě předpokladů, které nemusí být pro váš kód správné. Chcete-li zajistit, aby kód pro vaše scénáře fungoval podle očekávání, měli byste doručovat informace specifické pro jazykovou verzi podle následujících pokynů:

- Pokud se hodnota zobrazí uživateli, použijte aktuální jazykovou verzi. Viz <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Pokud bude hodnota uložena a bude mít k dispozici software, který je trvale uložený v souboru nebo databázi, použijte invariantní jazykovou verzi. Viz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Pokud neznáte cíl hodnoty, je nutné, aby příjemce dat nebo poskytovatel tuto jazykovou verzi určil.

  Všimněte si, že <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> slouží pouze k načtení lokalizovaných prostředků pomocí instance <xref:System.Resources.ResourceManager?displayProperty=fullName> třídy.

  I v případě, že je výchozí chování přetíženého členu vhodné pro vaše potřeby, je lepší explicitně volat přetížení specifické pro jazykovou verzi, aby váš kód byl vlastní dokument a snadněji se udržoval.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, použijte přetížení, které přebírá <xref:System.Globalization.CultureInfo> nebo <xref:System.IFormatProvider> a zadejte argument podle pokynů uvedených výše.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění, když je jisté, že výchozí poskytovatel jazykové verze nebo formátu je správným výběrem a kde udržovatelnost kódu není důležitou prioritou pro vývoj.

## <a name="example"></a>Příklad
 V následujícím příkladu `BadMethod` způsobí dvě porušení tohoto pravidla. `GoodMethod` opravuje první porušení předáním invariantní jazykové verze do System. String. Compare a opravuje druhé porušení předáním aktuální jazykové verze do <xref:System.String.ToLower%2A>, protože se uživateli zobrazí `string3`.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Příklad
 Následující příklad ukazuje účinek aktuální jazykové verze na výchozí <xref:System.IFormatProvider>, který je vybrán typem <xref:System.DateTime>.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Tento příklad vytvoří následující výstup.

 **6/4/1900 12:15:12 PM** 
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Související pravidla
 [CA1305: Zadejte možnosti IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Viz také
 [NIB: použití třídy CultureInfo](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
