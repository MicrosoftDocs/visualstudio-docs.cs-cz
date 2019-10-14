---
title: 'DA0006: Přepište Equals () pro typy hodnot | Microsoft Docs'
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
ms.workload:
- multiple
ms.openlocfilehash: 9cb4ac65442d9dbcb384ee3765f6fa827e3fa5d8
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306156"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Přepis Equals() pro typy hodnot

|||
|-|-|
|Id pravidla|DA0006|
|Category|Využití .NET Framework|
|Metody Profiiling|Kontrol|
|Message|Přepište rovnost a operátor rovnosti na hodnotových typech.|
|Typ messge|Upozornění|

## <a name="cause"></a>Příčina
 Volání metody Equals nebo operátorů rovnosti typu veřejné hodnoty jsou významným podílem dat profilování. Zvažte implementaci efektivnější metody.

## <a name="rule-description"></a>Popis pravidla
 U hodnotových typů zděděná implementace Equals používá knihovnu <xref:System.Reflection> a porovnává obsah všech polí v typu. Reflexe je výpočetně náročná a porovnání rovnosti všech polí může být zbytečné. Pokud očekáváte, že uživatelé budou porovnávat nebo třídit instance nebo je používat jako klíče zatřiďovací tabulky, váš typ hodnoty by měl implementovat Equals. Pokud váš programovací jazyk podporuje přetížení operátoru, měli byste také poskytnout implementaci operátorů rovnosti a nerovnosti.

 Další informace o tom, jak přepsat rovnost a operátory rovnosti, naleznete v tématu [pokyny pro implementaci Equals a operátoru rovnosti (= =)](http://go.microsoft.com/fwlink/?LinkId=177818).

## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění
 Příklad implementace operátorů Equals a rovnost naleznete v tématu pravidlo analýzy kódu @no__t – 0CA1815: Přepište Equals a operátor Equals na hodnotových typech @ no__t-0