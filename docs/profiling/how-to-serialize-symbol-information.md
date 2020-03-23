---
title: 'Postup: Serializace informací o symbolech | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 202c30b1786e7e3ddb27583ddaeda9180d680b53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774884"
---
# <a name="how-to-serialize-symbol-information"></a>Postup: Serializace informací o symbolech
Můžete serializovat symboly, které je nutné analyzovat aplikace. Serializace symbolů přidává symboly do . *vsp.* Přidáním informací o symbolu do . *vsp,* ostatní mohou analyzovat zprávu o výkonu bez přístupu k původním symbolům. Pokud symboly nejsou serializovány, musíte mít originální instrumentované . *exe* a . *pdb* soubory pro analýzu . *vsp.*

### <a name="to-automatically-serialize-symbol-information"></a>Automatické serializace informací o symbolu

1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

     Zobrazí se dialogové okno **Možnosti.**

2. Klepněte **na položku Nástroje pro sledování výkonu**.

3. V části **Obecné nastavení**vyberte **Automaticky serializovat informace o symbolu**.

## <a name="see-also"></a>Viz také
- [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
- [Postupy: Odkazování na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [Postup: Uložení analyzovaných souborů sestav](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
