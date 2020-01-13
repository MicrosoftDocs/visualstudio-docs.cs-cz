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
ms.openlocfilehash: a0a2947f0bd6758de62a4a11d78390d38a503271
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919034"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Náročná metoda GetHashCode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v tématu [DA0010: nákladný GetHashCode](/visualstudio/profiling/da0010-expensive-gethashcode).  

|||  
|-|-|  
|Id pravidla|DA0010|  
|Kategorie|Využití .NET Framework|  
|Metody profilace|Vzorkování<br /><br /> Paměť .NET|  
|Zpráva|Funkce GetHashCode by měly být levné a nesmí přidělit žádnou paměť. Pokud je to možné, snižte složitost funkce kódu hash.|  
|Typ zprávy|Upozornění|  
  
## <a name="cause"></a>příčina  
 Volání metody GetHashCode typu jsou významným podílem dat profilování nebo metoda přiděluje paměť.  
  
## <a name="rule-description"></a>Popis pravidla  
 Hashing je technika, jak rychle vyhledat konkrétní položku ve velké kolekci. Vzhledem k tomu, že tabulky hash můžou být velmi velké a musí podporovat vysoké míry přístupu, měly by být zatřiďovací tabulky extrémně efektivní. Nemnožení tohoto požadavku je, že metody GetHashCode v .NET Framework by neměly přidělit paměť. Přidělování paměti zvyšuje zatížení systému uvolňování paměti a zpřístupňuje metodu potenciálním zpožděním, pokud bude nutné spustit uvolňování paměti v důsledku žádosti o přidělení.  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Snižte složitost metody.
