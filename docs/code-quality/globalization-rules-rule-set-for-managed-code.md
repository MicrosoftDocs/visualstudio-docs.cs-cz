---
title: Sada pravidel Pravidla globalizace pro spravovaný kód
ms.date: 11/04/2016
description: Seznamte se s pravidlem pravidel globalizace v sadě Visual Studio, které se zaměřuje na problémy související s jazyky, místními prostředími a kulturami. Podívejte se na téma popisy pravidel.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: fdf816b978aac5d22b1750eeabe3737f1eb64085
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867929"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Sada pravidel Pravidla globalizace pro spravovaný kód

Použijte pravidlo Microsoft globalizace pravidla, která se zaměřují na problémy, které by mohly zabránit tomu, aby se data v aplikaci zobrazovala správně v různých jazycích, národních prostředích a jazykových verzích. Tuto sadu pravidel byste měli zahrnout, pokud je vaše aplikace lokalizovaná, globální nebo obojí.

|Pravidlo|Description|
|----------|-----------------|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Nepředávejte literály jako lokalizované parametry|
|[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304)|Určete CultureInfo|
|[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305)|Určete IFormatProvider|
|[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307)|Zadejte StringComparison pro přehlednost.|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Normalizujte řetězce na velká písmena|
|[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309)|Použijte řadový StringComparison|
|[CA1310](/dotnet/fundamentals/code-analysis/quality-rules/ca1310)|Zadejte StringComparison pro správnost.|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Určete zařazování pro argumenty řetězce volání nespravovaného kódu|
