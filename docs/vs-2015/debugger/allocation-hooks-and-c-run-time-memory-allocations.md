---
title: Háky přidělení a přidělení běhové paměti jazyka C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e123e74597ced9ef08860c5369f75ddda2f6e25
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780682"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Háky přidělení a přidělení běhové paměti jazyka C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Je velmi důležité omezení funkce háku přidělení, že se musí explicitně Ignorovat `_CRT_BLOCK` bloky (přidělení paměti provedené interně pomocí funkce knihovny run-time jazyka C) je-li využívají všechna volání do funkce knihovny run-time jazyka C, které přidělují interní paměť. `_CRT_BLOCK` Bloky můžete ignorovat zahrnutím kódu, jako je následující na začátku přidělení funkci připojení:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Pokud vaše háku přidělení neignoruje `_CRT_BLOCK` blokuje, pak všechny funkce knihovny run-time jazyka C v váš hook můžete zachytávat program v nekonečné smyčce. Například `printf` díky interní přidělení. Pokud váš kód hook volá `printf`, poté způsobí, že výsledný přidělení hook volat akci, která bude volat **printf** znovu, a tak dále až do přetečení zásobníku. Pokud potřebujete sestavy `_CRT_BLOCK` operace přiřazení jednu cestu pro obejití toto omezení je použít funkce rozhraní Windows API, nikoli funkcí jazyka C za běhu, pro formátování a výstup. Vzhledem k tomu, že rozhraní API Windows nepoužívejte haldy knihovny run-time jazyka C, se nebude zachytávat vaše háku přidělení v nekonečné smyčce.  
  
 Když si zblízka zdrojové soubory knihovny run-time, uvidíte, že funkci, výchozí přidělení připojení **CrtDefaultAllocHook** (které jednoduše vrátí **TRUE**), se nachází v samostatném souboru své vlastní, DBGHOOK. C. Pokud chcete, aby vaše háku přidělení volat i pro přidělení provedených za běhu spouštěcí kód, který se spouští před vaší aplikace **hlavní** funkce, můžete nahradit výchozí funkci svůj vlastní místo pomocí [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d).  
  
## <a name="see-also"></a>Viz také  
 [Zápis funkce háku ladění](../debugger/debug-hook-function-writing.md)   
 [Ukázka crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



