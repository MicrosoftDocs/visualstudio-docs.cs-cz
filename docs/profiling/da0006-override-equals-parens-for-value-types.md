---
title: 'DA0006: Přepsat rovná se() pro typy hodnot | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9e097d6d8c9a7b82fac53fd37951644eb7eb5e59
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779529"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Přepište Equals() pro hodnoty

|||
|-|-|
|Id pravidla|DA0006 řekl:|
|Kategorie|Použití rozhraní .NET Framework|
|Profiilingmetody|Vzorkování|
|Zpráva|Přepsat operátor Rovná se a rovnost i na typech hodnot.|
|Messge typ|Upozornění|

## <a name="cause"></a>Příčina
 Volání metody Equals nebo operátory rovnosti typu veřejné hodnoty jsou významnou částí dat profilování. Zvažte implementaci efektivnější metody.

## <a name="rule-description"></a>Popis pravidla
 Pro typy hodnot zděděná implementace <xref:System.Reflection> Equals používá knihovnu a porovnává obsah všech polí v typu. Reflexe je výpočetně náročná a porovnání rovnosti všech polí může být zbytečné. Pokud očekáváte, že uživatelé porovnat nebo seřadit instance nebo je použít jako klíče tabulky hash, typ hodnoty by měl implementovat Rovná se. Pokud váš programovací jazyk podporuje přetížení operátoru, měli byste také poskytnout implementaci operátorů rovnosti a nerovnosti.

 Další informace o tom, jak přepsat Equals a operátory rovnosti, naleznete [v tématu Pokyny pro implementaci rovná se a operátor rovnosti (==)](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to-investigate-a-warning"></a>Jak prošetřit varování
 Příklad implementace operátorů Rovná se a rovnosti naleznete v tématu pravidlo analýzy kódu [CA1815: Přepsat rovná se a operátor se rovná na typy hodnot](../code-quality/ca1815.md)
