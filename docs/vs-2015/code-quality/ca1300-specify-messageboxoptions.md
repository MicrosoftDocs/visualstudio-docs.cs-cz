---
title: 'CA1300: zadejte MessageBoxOptions | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3e21866fce69f768d927882d3ddd47ae3e431265
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663610"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Zadejte možnosti MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Kategorie|Microsoft. Globalization|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Metoda volá přetížení metody <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>, která nepřijímá <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argument.

## <a name="rule-description"></a>Popis pravidla
 Chcete-li zobrazit okno se zprávou pro jazykové verze, které používají pořadí čtení zprava doleva, musí být <xref:System.Windows.Forms.MessageBoxOptions> a <xref:System.Windows.Forms.MessageBoxOptions> členů výčtu <xref:System.Windows.Forms.MessageBoxOptions> předány metodě <xref:System.Windows.Forms.MessageBox.Show%2A>. Zkontrolujte vlastnost <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> obsahujícího ovládacího prvku, abyste zjistili, zda chcete použít směr čtení zprava doleva.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zavolejte přetížení metody <xref:System.Windows.Forms.MessageBox.Show%2A>, která přijímá argument <xref:System.Windows.Forms.MessageBoxOptions>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla, pokud knihovna kódu nebude lokalizována do jazykové verze, která používá pořadí čtení zprava doleva.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která zobrazí okno se zprávou s možnostmi, které jsou vhodné pro pořadí čtení jazykové verze. Soubor prostředků, který není zobrazen, je požadován k sestavení příkladu. Použijte komentáře v příkladu k sestavení příkladu bez souboru prostředků a k otestování funkce zprava doleva.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Viz také
 [prostředky <xref:System.Resources.ResourceManager?displayProperty=fullName> v aplikacích klasické pracovní plochy](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
