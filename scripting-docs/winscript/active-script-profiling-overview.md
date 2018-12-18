---
title: Přehled profilace aktivních skriptů | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9413e8b6e6db0c81eb1853c24506d20c8d06f3e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791922"
---
# <a name="active-script-profiling-overview"></a>Přehled profilace aktivních skriptů
[Rozhraní profileru aktivních skriptů](../winscript/reference/active-script-profiler-interfaces.md) povolit profilace skriptovací stroje. Profilace aktivních skriptů se skládá z následujících částí:  
  
-   Modul jazyka  
  
-   Hostitel  
  
-   profiler  
  
## <a name="language-engine"></a>Modul jazyka  
 Modul jazyka spustí skript. Poskytuje metody, které umožní profilace kód skriptu, jako je proveden. Při vytváření profilu je povolená, modul jazyka vezme identifikátor třídy (CLSID) z profileru objektu COM jako argument. Vytvoří instanci objektu COM profileru a pak zavolá do profileru, když dojde k různé události.  
  
 Implementuje modul jazyka [iactivescriptprofilercontrol – rozhraní](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] Běhový kontroluje proměnné prostředí JS_PROFILER na vytvoření k určení, zda má být povolen profilace. Pokud tato proměnná je nastavená na CLSID profileru, modul runtime jazyka vytvoří instanci objektu COM profileru, pomocí hodnoty proměnné, chcete-li určit, které profileru k vytvoření.  
  
## <a name="host"></a>Hostitel  
 Hostitele vytvoří modul jazyka a poskytuje modul jazyka spouštět skripty. Inteligentního hostitele také poskytuje kontext dokumentu, které je možné zajistit lepší informace při ladění a profilování ladicí program nebo profileru.  
  
## <a name="profiler"></a>profiler  
 Pokud dojde k různé události profileru obdrží volání z modulu jazyka. Profileru musí být registrován jako objekt COM a musí implementovat [iactivescriptprofilercallback – rozhraní](../winscript/reference/iactivescriptprofilercallback-interface.md) rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní profileru aktivních skriptů](../winscript/reference/active-script-profiler-interfaces.md)