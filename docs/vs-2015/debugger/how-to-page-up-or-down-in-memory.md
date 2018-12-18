---
title: 'Postupy: stránku nahoru nebo dolů v paměti | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d20c22e366736711f16fc17f56b2e81eea558948
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769149"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Postupy: O stránku nahoru nebo dolů v paměti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při prohlížení obsah paměti **paměti** okno nebo **zpětný překlad** můžete použít svislý posuvník přesunout nahoru nebo dolů v paměti prostoru.  
  
### <a name="to-page-up-or-down-in-memory"></a>Na stránce nahoru nebo dolů v paměti  
  
1. Na stránce dolů (Přejít na vyšší adresy paměti), klikněte na svislý posuvník posuvníku.  
  
2. Na stránce nahoru (Přejít na nižší adresa paměti), klikněte na svislý posuvník nad jezdce.  
  
   Můžete si všimnout, že svislý posuvník funguje v nestandardním způsobem. Adresní prostor moderní počítače je velmi velké a je snadné získat ztráty uchopíte jeho thumb posuvník a jeho přetažením do náhodných umístění. Z tohoto důvodu jezdce je "springloaded" a vždy zůstane v centru posuvník. V nativním kódu aplikace můžete stránku nahoru nebo dolů ale nejde o volně přejděte.  
  
   Ve spravovaných aplikacích zpětného překladu je omezená na jednu funkci a můžete posouvat normálně.  
  
   Můžete si všimnout, že vyšší adresy se zobrazí v dolní části okna. Chcete-li zobrazit adresu vyšší musí přesunout dolů, nikoli nahoru.  
  
#### <a name="to-move-up-or-down-one-instruction"></a>Chcete-li přesunout nahoru nebo dolů jedna instrukce  
  
-   Klikněte na šipku v horní nebo dolní svislý posuvník.  
  
## <a name="see-also"></a>Viz také  
 [Paměť Windows](../debugger/memory-windows.md)   
 [Postupy: použití okna zpětného překladu](../debugger/how-to-use-the-disassembly-window.md)   
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)





