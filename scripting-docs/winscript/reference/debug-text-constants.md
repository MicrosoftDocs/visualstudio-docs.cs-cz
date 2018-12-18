---
title: Debug_text – konstanty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5126a9efefaab611cd27d2104c40918f8dc7c7e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791829"
---
# <a name="debugtext-constants"></a>DEBUG_TEXT – konstanty
Použít během [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Konstanty  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Označuje, že je text výrazu oproti příkaz. Tento příznak může mít vliv na způsob, ve kterém je analyzována text v některých jazycích.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Pokud je k dispozici návratovou hodnotu, použije se volajícího.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Nepovolit vedlejší účinky. Pokud je nastavený tento příznak, vyhodnocování výrazu by měl změnit žádné stav modulu runtime.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Povolit zarážky během vyhodnocení textu. Pokud není nastavený tento příznak, budou zarážky ignorovat během vyhodnocení textu.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Povolit zprávy o chybách během vyhodnocení textu. Pokud není nastavený tento příznak, pak chyby, nebudou ohlášena na hostiteli během vyhodnocování.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Označuje, že je výraz k vyhodnocení na kontext kódu než systémem samotného výrazu.|  
  
## <a name="see-also"></a>Viz také  
 [Konstanty ladicího programu aktivních skriptů, výčty a struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)