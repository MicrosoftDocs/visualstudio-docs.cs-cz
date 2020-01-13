---
title: 'DA0011: nákladný objekt CompareTo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ed433612498a6b7d4b87291311d7fd6efcb0974
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918386"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Náročná metoda CompareTo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v tématu [DA0011: nákladných CompareTo](/visualstudio/profiling/da0011-expensive-compareto).  
  
|||  
|-|-|  
|Id pravidla|DA0011|  
|Kategorie|Využití .NET Framework|  
|Metody profilace|Vzorkování<br /><br /> Paměť .NET|  
|Zpráva|Funkce CompareTo by měly být levné a nesmí přidělit žádnou paměť. Pokud je to možné, snižte složitost funkce CompareTo.|  
|Typ pravidla|Upozornění|  
  
## <a name="cause"></a>příčina  
 Metoda CompareTo typu je nákladné nebo přiděluje paměť.  
  
## <a name="rule-description"></a>Popis pravidla  
 Metody CompareTo by měly být efektivní a neměly by přidělovat paměť.  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Snižte složitost metody CompareTo.
