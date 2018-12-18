---
title: 'DA0006: Přepište Equals() pro hodnoty | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ab011487f33438091eb963c9ea4a7e1d1c80ec4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856272"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Přepište Equals() pro hodnoty

|||  
|-|-|  
|Id pravidla|DA0006|  
|Kategorie|Použití rozhraní .NET framework|  
|Profiiling metody|Vzorkování|  
|Zpráva|Přepište Equals a operátory rovnosti na hodnotových typech.|  
|Typ Messge|Upozornění|  

## <a name="cause"></a>příčina  
 Volání metody Equals a operátory rovnosti veřejné hodnotového typu je podstatnou část dat profilování. Zvažte implementaci metodu efektivnější.  

## <a name="rule-description"></a>Popis pravidla  
 Pro hodnotové typy používá zděděná implementace metody Equals <xref:System.Reflection> knihovny a porovnává obsah všech polí v typu. Reflexe je výpočetně náročná a porovnání rovnosti všech polí může být zbytečné. Pokud očekáváte, že uživatelé budou porovnávat nebo třídit instance nebo používat jako klíče zatřiďovací tabulky, by měl typ hodnoty implementovat metodu Equals. Pokud svůj oblíbený programovací jazyk podporuje přetížení operátoru, měli byste také poskytnout implementaci pro operátory rovnosti a nerovnosti.  

 Další informace o tom, jak přepsat Equals a operátory rovnosti, naleznete v tématu [pokyny pro implementaci rovná se a operátor rovnosti (==)](http://go.microsoft.com/fwlink/?LinkId=177818).  

## <a name="how-to-investigate-a-warning"></a>Zkoumání upozornění  
 Příklad implementace Equals a operátory rovnosti, naleznete v tématu pravidel nástroje Analýza kódu [CA1815: přepište rovná se a operátor rovnosti na hodnotových typech](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)