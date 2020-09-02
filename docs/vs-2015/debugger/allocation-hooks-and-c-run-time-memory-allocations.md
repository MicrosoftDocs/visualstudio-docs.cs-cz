---
title: Háky přidělení a přidělení běhové paměti jazyka C | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 8487972c237b9c2ba6bf2594ffc1df43fa0c63cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702427"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Háky přidělení a přidělení běhové paměti jazyka C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Velmi důležité omezení funkcí zavěšení přidělení je, že musí explicitně ignorovat `_CRT_BLOCK` bloky (přidělení paměti, které interně provádí funkce běhové knihovny jazyka c), pokud provedou volání funkcí běhové knihovny jazyka c, která přidělují interní paměť. `_CRT_BLOCK`Bloky lze ignorovat zahrnutím kódu, jako je například následující na začátku funkce Hooku přidělení:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Pokud váš Hook přidělení Neignoruje `_CRT_BLOCK` bloky, pak jakákoli funkce knihovny run-time jazyka C, která je volána ve vašem zavěšení, může zachytit program v nekonečné smyčce. Například `printf` provede interní přidělení. Pokud váš kód zavěšení volá `printf` , výsledná alokace pak způsobí, že se váš Hook znovu volá, čímž se znovu zavolá **printf** a tak dále, dokud se zásobník nepřetéká. Pokud potřebujete nahlásit `_CRT_BLOCK` operace přidělení, jedním ze způsobů obcházení tohoto omezení je použití funkcí rozhraní API systému Windows namísto běhových funkcí pro formátování a výstup. Vzhledem k tomu, že rozhraní API systému Windows nepoužívají haldu běhové knihovny jazyka C, nebudou v nekonečné smyčce zachycena vaše zavěšení připojení.  
  
 Pokud prohlížíte zdrojové soubory knihovny run-time, uvidíte, že výchozí funkce Hooku přidělení, **CrtDefaultAllocHook** (která jednoduše vrátí **hodnotu true**), je umístěna v samostatném souboru vlastní DBGHOOK. C. Chcete-li, aby byl zavěšení připojení volán i pro přidělení spouštěcího kódu modulu runtime, který je proveden před funkcí **Main** vaší aplikace, můžete tuto výchozí funkci nahradit jednou z vlastních funkcí namísto použití [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d).  
  
## <a name="see-also"></a>Viz také  
 [Zápis funkce zavěšení ladění](../debugger/debug-hook-function-writing.md)   
 [Ukázka crt_dbg2](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
