---
title: 'DA0013: vysoké použití String. Split nebo String. substring | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6ff05e7e8cc74eacb00b5ec8ff42bd48faaa12c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159190"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Vysoký výskyt použití String.Split nebo String.Substring
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID pravidla | DA0013 |  
| Kategorie |. Pokyny k používání rozhraní .NET Framework |  
| Metody profilování | Vzorkování |  
| Zpráva | Zvažte snížení využití funkcí String. Split a String. substring. |  
| Typ pravidla | Upozornění |  
  
## <a name="cause"></a>Příčina  
 Volání metod System. String. Split nebo System. String. substring představují významnou část dat profilace. Zvažte použití System. String. IndexOf nebo System. String. IndexOfAny, pokud testujete existenci podřetězce v řetězci.  
  
## <a name="rule-description"></a>Popis pravidla  
 Metoda Split pracuje na objektu String a vrací nové pole řetězců, které obsahuje podřetězce originálu. Funkce přiděluje paměť pro vrácený objekt Array a přidělí objekt New String pro každý prvek pole, který najde. Podobně metoda substr funguje na objektu String a vrátí nový řetězec, který je ekvivalentní podřetězec, který byl vyžádán.  
  
 Pokud je Správa přidělení paměti ve vaší aplikaci kritická, zvažte použití alternativ pro metody String. Split a String. substr. Například můžete použít buď metodu IndexOf nebo IndexOfAny, k vyhledání konkrétního podřetězce v řetězci znaků bez vytvoření nové instance třídy String.  
  
## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění  
 Dvakrát klikněte na zprávu v okně Seznam chyb, abyste přešli na [zobrazení podrobností o funkcích](../profiling/function-details-view.md) profilu vzorkování. Zkontrolujte volání funkcí a vyhledejte části programu, které usnadňují použití metod System. String. Split nebo System. String. substr. Pokud je to možné, použijte buď metodu IndexOf nebo IndexOfAny, k vyhledání konkrétního podřetězce v rámci řetězce znaků bez vytvoření nové instance třídy String.
