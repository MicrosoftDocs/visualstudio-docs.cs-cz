---
title: 'DA0006: přepište Equals () pro typy hodnot | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eaba2f099f2a4d04574acd5bcdd2ba8f8f44b4ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852366"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Přepis Equals() pro typy hodnot
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID pravidla | DA0006 |  
| Kategorie |. Použití rozhraní .NET Framework |  
| Metody Profiiling | Vzorkování |  
| Zpráva | Přepište rovnost a operátor rovnosti na hodnotových typech. |  
| Typ messge | Upozornění |  
  
## <a name="cause"></a>Příčina  
 Volání metody Equals nebo operátorů rovnosti typu veřejné hodnoty jsou významným podílem dat profilování. Zvažte implementaci efektivnější metody.  
  
## <a name="rule-description"></a>Popis pravidla  
 U hodnotových typů zděděná implementace EQUAL používá <xref:System.Reflection> knihovnu a porovnává obsah všech polí v typu. Reflexe je výpočetně náročná a porovnání rovnosti všech polí může být zbytečné. Pokud očekáváte, že uživatelé budou porovnávat nebo třídit instance nebo je používat jako klíče zatřiďovací tabulky, váš typ hodnoty by měl implementovat Equals. Pokud váš programovací jazyk podporuje přetížení operátoru, měli byste také poskytnout implementaci operátorů rovnosti a nerovnosti.  
  
 Další informace o tom, jak přepsat rovnost a operátory rovnosti, naleznete v tématu [pokyny pro implementaci Equals a operátoru rovnosti (= =)](https://msdn.microsoft.com/library/7h9bszxx.aspx).  
  
## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění  
 Příklad implementace operátorů Equals a rovnosti naleznete v tématu pravidlo analýzy kódu [CA1815: přepište Equals a operator Equals on Value Types](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)
