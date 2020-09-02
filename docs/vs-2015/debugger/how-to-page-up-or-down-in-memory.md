---
title: 'Postupy: stránka nahoru nebo dolů v paměti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: cc05772e6376dbe151d5ca71b9ee221e61a7be88
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157860"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Postupy: O stránku nahoru nebo dolů v paměti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když zobrazíte obsah paměti v okně **paměti** nebo v okně **zpětný překlad** , můžete pomocí svislého posuvníku přesunout nahoru nebo dolů v paměťovém prostoru.  
  
### <a name="to-page-up-or-down-in-memory"></a>Pro stránku nahoru nebo dolů v paměti  
  
1. Chcete-li posunout stránku dolů (přesunout na vyšší adresu paměti), klikněte na svislý posuvník pod posuvníkem.  
  
2. Chcete-li stránku nahoru (přesunout na nižší adresu paměti), klikněte na svislý posuvník nad jezdcem.  
  
   Všimněte si také, že svislý posuvník funguje nestandardním způsobem. Adresní prostor moderního počítače je velmi velký a je snadné ho ztratit tím, že se podíváme na miniaturu ScrollBar a přetáhnete ji do náhodného umístění. Z tohoto důvodu je palec "springloaded" a vždy zůstává ve středu posuvníku. V aplikacích s nativním kódem můžete stránku nahoru nebo dolů, ale nemůžete se pohybovat volně.  
  
   Ve spravovaných aplikacích je zpětný překlad omezen na jednu funkci a můžete se posouvat normálně.  
  
   Všimněte si, že v dolní části okna se zobrazí vyšší adresy. Chcete-li zobrazit vyšší adresu, je nutné přesunout dolů, ne.  
  
#### <a name="to-move-up-or-down-one-instruction"></a>Přesun nahoru nebo dolů o jednu instrukci  
  
- Klikněte na šipku v horní nebo dolní části svislého posuvníku.  
  
## <a name="see-also"></a>Viz také  
 [Okna paměti](../debugger/memory-windows.md)   
 [Postupy: použití okna zpětného překladu](../debugger/how-to-use-the-disassembly-window.md)   
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
