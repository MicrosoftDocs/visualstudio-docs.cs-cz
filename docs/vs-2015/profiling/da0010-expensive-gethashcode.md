---
title: 'DA0010: nákladný GetHashCode | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af234cd130d06c2a76c5ddbc958a67eb064d9128
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547573"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Náročná funkce GetHashCode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v tématu [DA0010: nákladný GetHashCode](/visualstudio/profiling/da0010-expensive-gethashcode).  

|Položka|Hodnota|  
|-|-|  
|ID pravidla|DA0010|  
|Kategorie|Využití .NET Framework|  
|Metody profilace|Vzorkování<br /><br /> Paměť .NET|  
|Zpráva|Funkce GetHashCode by měly být levné a nesmí přidělit žádnou paměť. Pokud je to možné, snižte složitost funkce kódu hash.|  
|Typ zprávy|Upozornění|  
  
## <a name="cause"></a>Příčina  
 Volání metody GetHashCode typu jsou významným podílem dat profilování nebo metoda přiděluje paměť.  
  
## <a name="rule-description"></a>Popis pravidla  
 Hashing je technika, jak rychle vyhledat konkrétní položku ve velké kolekci. Vzhledem k tomu, že tabulky hash můžou být velmi velké a musí podporovat vysoké míry přístupu, měly by být zatřiďovací tabulky extrémně efektivní. Nemnožení tohoto požadavku je, že metody GetHashCode v .NET Framework by neměly přidělit paměť. Přidělování paměti zvyšuje zatížení systému uvolňování paměti a zpřístupňuje metodu potenciálním zpožděním, pokud bude nutné spustit uvolňování paměti v důsledku žádosti o přidělení.  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Snižte složitost metody.
