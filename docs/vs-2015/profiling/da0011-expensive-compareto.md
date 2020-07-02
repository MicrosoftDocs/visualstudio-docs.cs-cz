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
ms.openlocfilehash: a66242554de28ab45cc797d523ea7b5a967e9e5d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542971"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Náročná funkce CompareTo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v tématu [DA0011: nákladných CompareTo](/visualstudio/profiling/da0011-expensive-compareto).  
  
|Položka|Hodnota|  
|-|-|  
|ID pravidla|DA0011|  
|Kategorie|Využití .NET Framework|  
|Metody profilace|Vzorkování<br /><br /> Paměť .NET|  
|Zpráva|Funkce CompareTo by měly být levné a nesmí přidělit žádnou paměť. Pokud je to možné, snižte složitost funkce CompareTo.|  
|Typ pravidla|Upozornění|  
  
## <a name="cause"></a>Příčina  
 Metoda CompareTo typu je nákladné nebo přiděluje paměť.  
  
## <a name="rule-description"></a>Popis pravidla  
 Metody CompareTo by měly být efektivní a neměly by přidělovat paměť.  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Snižte složitost metody CompareTo.
