---
title: Sada pravidel pravidla globalizace pro spravovaný kód | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1630769b5150d9cef7b00e575ac9c555f5bc5be1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667608"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Sada pravidel Pravidla globalizace pro spravovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít pravidlo Microsoft globalizace pravidla, která se zaměřují na problémy, které by mohly zabránit tomu, aby se data v aplikaci zobrazovala správně v různých jazycích, národních prostředích a jazykových verzích. Tuto sadu pravidel byste měli zahrnout, pokud je vaše aplikace lokalizovaná, globální nebo obojí.

|Pravidlo|Popis|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Určete MessageBoxOptions|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Vyhněte se duplicitním akcelerátorům|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Nekódujte pevně řetězce závislé na národním prostředí|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Nepředávejte literály jako lokalizované parametry|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|Určete CultureInfo|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Určete IFormatProvider|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Nastavte národního prostředí pro datové typy|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Určete StringComparison|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizujte řetězce na velká písmena|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Použijte řadový StringComparison|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Určete zařazování pro argumenty řetězce volání nespravovaného kódu|
