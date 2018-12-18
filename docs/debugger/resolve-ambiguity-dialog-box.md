---
title: Vyřešit nejednoznačnosti – dialogové okno | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.Disambig
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 130f580c997cb5bc0e522d0fef57969788481273
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475477"
---
# <a name="resolve-ambiguity-dialog-box"></a>Dialogové okno Vyřešit nejednoznačnosti
`Resolve Ambiguity` Dialogové okno se zobrazí, když ladicí program nemůže vyberte umístění, k zobrazení. Například pokud používáte šablonami C++, můžete vytvořit víc funkcí z jedné funkce šablony. Pokud ladicí program zastaví v umístění zdroje v šabloně, a vy zvolíte `Go To Disassembly`, má více možností ladicího programu. Jednotlivé funkce z šablony má svou vlastní zpětný překlad kódu a ladicí program nebude vědět, který kód, který chcete zobrazit. `Resolve Ambiguity` Dialogové okno umožňuje vybrat umístění, bude ze seznamu všech odpovídajících umístění.  
  
 `Choose the specific location`  
 Zobrazuje seznam všech umístění odpovídající do příkazu.  
  
 `Address`  
 Zobrazuje adresy paměti pro každou funkci.  
  
 `Function`  
 Zobrazuje název jednotlivé funkce.  
  
 `Module`  
 Zobrazí modul, (EXE nebo DLL) obsahující kód objektu pro tuto funkci.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy v ladicím programu](../debugger/expressions-in-the-debugger.md)