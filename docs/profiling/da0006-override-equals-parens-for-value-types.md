---
title: DA0006 – přepište Equals () pro typy hodnot | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e815c985653bc58271b643aabd53955ae3c83f9c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937651"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Přepis Equals() pro typy hodnot

|Položka|Hodnota|
|-|-|
|ID pravidla|DA0006|
|Kategorie|Využití .NET Framework|
|Metody Profiiling|Vzorkování|
|Zpráva|Přepište rovnost a operátor rovnosti na hodnotových typech.|
|Typ messge|Upozornění|

## <a name="cause"></a>Příčina
 Volání metody Equals nebo operátorů rovnosti typu veřejné hodnoty jsou významným podílem dat profilování. Zvažte implementaci efektivnější metody.

## <a name="rule-description"></a>Popis pravidla
 U hodnotových typů zděděná implementace EQUAL používá <xref:System.Reflection> knihovnu a porovnává obsah všech polí v typu. Reflexe je výpočetně náročná a porovnání rovnosti všech polí může být zbytečné. Pokud očekáváte, že uživatelé budou porovnávat nebo třídit instance nebo je používat jako klíče zatřiďovací tabulky, váš typ hodnoty by měl implementovat Equals. Pokud váš programovací jazyk podporuje přetížení operátoru, měli byste také poskytnout implementaci operátorů rovnosti a nerovnosti.

 Další informace o tom, jak přepsat rovnost a operátory rovnosti, naleznete v tématu [pokyny pro implementaci Equals a operátoru rovnosti (= =)](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění
 Příklad implementace operátorů Equals a rovnosti naleznete v tématu pravidlo analýzy kódu [CA1815: přepište Equals a operator Equals on Value Types](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)
