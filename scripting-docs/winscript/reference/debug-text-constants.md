---
title: Konstanty DEBUG_TEXT | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: facbdc1258b3fca72a239d9d5cc41772cf577f13
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577373"
---
# <a name="debug_text-constants"></a>DEBUG_TEXT – konstanty
Používá se během [idebugexpressioncontext –::P arselanguagetext](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Konstanty  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Označuje, že text je výraz na rozdíl od příkazu. Tento příznak může mít vliv na způsob, jakým je text analyzován některými jazyky.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Pokud je vrácená hodnota k dispozici, bude ji volající používat.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Nepovoluje vedlejší účinky. Pokud je tento příznak nastaven, vyhodnocení výrazu by neměl změnit žádný běhový stav.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Při vyhodnocování textu povolte zarážky. Není-li tento příznak nastaven, budou zarážky při vyhodnocování textu ignorovány.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Povolí zprávy o chybách během vyhodnocování textu. Není-li tento příznak nastaven, nebudou během vyhodnocení chyby hlášeny hostiteli.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Označuje, že výraz má být vyhodnocen jako kontext kódu namísto spuštění výrazu samotného.|  
  
## <a name="see-also"></a>Viz také:  
 [Konstanty, výčty a struktury ladicího programu aktivních skriptů](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)