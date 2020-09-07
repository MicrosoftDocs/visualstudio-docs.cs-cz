---
title: Sada pravidel Pravidla globalizace pro spravovaný kód
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2af6126c751d03968dc7ecd87693e3546376c12a
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509858"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Sada pravidel Pravidla globalizace pro spravovaný kód

Použijte pravidlo Microsoft globalizace pravidla, která se zaměřují na problémy, které by mohly zabránit tomu, aby se data v aplikaci zobrazovala správně v různých jazycích, národních prostředích a jazykových verzích. Tuto sadu pravidel byste měli zahrnout, pokud je vaše aplikace lokalizovaná, globální nebo obojí.

|Pravidlo|Popis|
|----------|-----------------|
|[CA1303](../code-quality/ca1303.md)|Nepředávejte literály jako lokalizované parametry|
|[CA1304](../code-quality/ca1304.md)|Určete CultureInfo|
|[CA1305](../code-quality/ca1305.md)|Určete IFormatProvider|
|[CA1307](../code-quality/ca1307.md)|Zadejte StringComparison pro přehlednost.|
|[CA1308](../code-quality/ca1308.md)|Normalizujte řetězce na velká písmena|
|[CA1309](../code-quality/ca1309.md)|Použijte řadový StringComparison|
|[CA1310](../code-quality/ca1310.md)|Zadejte StringComparison pro správnost.|
|[CA2101](../code-quality/ca2101.md)|Určete zařazování pro argumenty řetězce volání nespravovaného kódu|
