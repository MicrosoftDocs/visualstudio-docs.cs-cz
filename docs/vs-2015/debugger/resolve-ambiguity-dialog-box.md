---
title: Vyřešit nejednoznačnosti – dialogové okno | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.Disambig
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b35d305bbd011adc02692cd7c9c687ac0bfc7d45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148792"
---
# <a name="resolve-ambiguity-dialog-box"></a>Dialogové okno Vyřešit nejednoznačnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Resolve Ambiguity`Dialogové okno se zobrazí, pokud ladicí program nemůže zvolit umístění, které se má zobrazit. Například pokud používáte šablony jazyka C++, můžete vytvořit více funkcí z jedné šablony funkce. Pokud se ladicí program zastaví na zdrojovém umístění v šabloně a Vy zvolíte `Go To Disassembly` , má ladicí program více možností. Každá funkce vytvořená v šabloně má svůj vlastní kód zpětného překladu a ladicí program neví, který kód chcete zobrazit. `Resolve Ambiguity`Dialogové okno umožňuje vybrat umístění, které chcete, ze seznamu všech odpovídajících umístění.  
  
 `Choose the specific location`  
 Zobrazí seznam všech umístění odpovídajících vašemu příkazu.  
  
 `Address`  
 Zobrazuje adresy paměti pro každou funkci.  
  
 `Function`  
 Zobrazuje název každé funkce.  
  
 `Module`  
 Zobrazuje modul (EXE nebo DLL) obsahující kód objektu pro funkci.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy v ladicím programu](../debugger/expressions-in-the-debugger.md)
