---
title: Sada pravidel Pravidla globalizace pro spravovaný kód
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 905f3323f4ede33ba8a7e1547bed7a81c43be96d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449033"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Sada pravidel Pravidla globalizace pro spravovaný kód

Použijte pravidlo Microsoft globalizace pravidla, která se zaměřují na problémy, které by mohly zabránit tomu, aby se data v aplikaci zobrazovala správně v různých jazycích, národních prostředích a jazykových verzích. Tuto sadu pravidel byste měli zahrnout, pokud je vaše aplikace lokalizovaná, globální nebo obojí.

|Pravidlo|Popis|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Určete MessageBoxOptions|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Vyhněte se duplicitním akcelerátorům|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Nenekódujte pevně řetězce specifické pro národní prostředí|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Nepředávejte literály jako lokalizované parametry|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|Určete CultureInfo|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Určete IFormatProvider|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Nastavte národního prostředí pro datové typy|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Určete StringComparison|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizujte řetězce na velká písmena|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Použijte řadový StringComparison|
|[CA2101](../code-quality/ca2101.md)|Určete zařazování pro argumenty řetězce volání nespravovaného kódu|
