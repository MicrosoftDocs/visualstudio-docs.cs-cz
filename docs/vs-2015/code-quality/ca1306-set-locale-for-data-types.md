---
title: 'CA1306: nastavení národního prostředí pro datové typy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: edd1d6a7623f96f03403883ee2585d245414bb3b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539019"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Nastavte národního prostředí pro datové typy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Kategorie|Microsoft. Globalization|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Metoda nebo konstruktor vytvořila jednu nebo více <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName> instancí nebo neexplicitně nastavila vlastnost locale ( <xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> nebo <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName> ).

## <a name="rule-description"></a>Popis pravidla
 Národní prostředí Určuje prvky prezentace specifické pro jazykovou verzi pro data, jako je například formátování používané pro číselné hodnoty, symboly měny a pořadí řazení. Při vytváření <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> by mělo být nastavení národního prostředí explicitně nastaveno. Ve výchozím nastavení je národní prostředí pro tyto typy aktuální jazyková verze. Pro data, která jsou uložena v databázi nebo souboru a jsou sdíleny globálně, by mělo být národní prostředí obvykle nastaveno na invariantní jazykovou verzi ( <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> ). Když jsou data sdílena napříč kulturami, použití výchozího národního prostředí může způsobit, že obsah <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> bude správně prezentován nebo interpretován.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, explicitně nastavte národní prostředí pro <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění, když je knihovna nebo aplikace určena pro omezené místní cílové skupiny, data nejsou sdílena nebo výchozí nastavení vydává požadované chování ve všech podporovaných scénářích.

## <a name="example"></a>Příklad
 Následující příklad vytvoří dvě <xref:System.Data.DataTable> instance.

 [!code-csharp[FxCop.Globalization.DataTable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DataTable/cs/FxCop.Globalization.DataTable.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
