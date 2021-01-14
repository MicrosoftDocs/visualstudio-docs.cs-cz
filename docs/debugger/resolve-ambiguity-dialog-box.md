---
title: Vyřešit nejednoznačnosti – dialogové okno | Microsoft Docs
description: Zkontrolujte dialogové okno vyřešit nejednoznačnosti sady Visual Studio, které se zobrazí, když ladicí program nemůže zvolit umístění, které se má zobrazit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6f7156a43bc8c5c60415680b4380600e9e695cc
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205603"
---
# <a name="resolve-ambiguity-dialog-box"></a>Dialogové okno Vyřešit nejednoznačnosti
`Resolve Ambiguity`Dialogové okno se zobrazí, pokud ladicí program nemůže zvolit umístění, které se má zobrazit. Například pokud používáte šablony jazyka C++, můžete vytvořit více funkcí z jedné šablony funkce. Pokud se ladicí program zastaví na zdrojovém umístění v šabloně a Vy zvolíte `Go To Disassembly` , má ladicí program více možností. Každá funkce vytvořená v šabloně má svůj vlastní kód zpětného překladu a ladicí program neví, který kód chcete zobrazit. `Resolve Ambiguity`Dialogové okno umožňuje vybrat umístění, které chcete, ze seznamu všech odpovídajících umístění.

 `Choose the specific location` Zobrazí seznam všech umístění odpovídajících vašemu příkazu.

 `Address` Zobrazuje adresy paměti pro každou funkci.

 `Function` Zobrazuje název každé funkce.

 `Module` Zobrazuje modul (EXE nebo DLL) obsahující kód objektu pro funkci.

## <a name="see-also"></a>Viz také
- [Výrazy v ladicím programu](../debugger/expressions-in-the-debugger.md)