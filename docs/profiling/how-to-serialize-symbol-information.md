---
title: Informace o serializaci symbolů | Microsoft Docs
description: Naučte se, jak můžete serializovat symboly, které musíte mít k analýze vaší aplikace, a způsob, jakým serializace symbolů přidává do souboru. vsp symboly.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b7cdfa6e64380c966b62d6691f73719a3034e2d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722084"
---
# <a name="how-to-serialize-symbol-information"></a>Postupy: serializace informací o symbolu
Můžete serializovat symboly, které musíte mít k analýze aplikace. Serializace symbolů přidá symboly do. soubor *VSP* . Přidáním informací o symbolech do. soubor *VSP* , ostatní mohou analyzovat sestavu o výkonu bez přístupu k původním symbolům. Pokud symboly nejsou serializovány, musíte mít původní instrumentaci. *exe* a. soubory *PDB* k analýze. soubor *VSP* .

### <a name="to-automatically-serialize-symbol-information"></a>Automatické serializace informací o symbolech

1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

     Zobrazí se dialogové okno **Možnosti** .

2. Klikněte na **Nástroje pro sledování výkonu**.

3. V části **Obecné nastavení** vyberte možnost **automaticky serializovat informace o symbolech**.

## <a name="see-also"></a>Viz také
- [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
- [Postupy: Odkazování na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [Postupy: ukládání analyzovaných souborů sestav](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
