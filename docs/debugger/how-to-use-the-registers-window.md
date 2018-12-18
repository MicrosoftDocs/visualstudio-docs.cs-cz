---
title: Zobrazení hodnoty registru v ladicím programu | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31d9b9a9243bdf5bd39ebddf90ffa0ea32b23072
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058438"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Zobrazení hodnoty registru v okně registr (C#, C++, Visual Basic, F#)

**Zaregistruje** okně se zobrazí obsah registru během ladění sady Visual Studio. Podrobný úvod ke koncepci registry a **zaregistruje** okna, naleznete v tématu [základní informace o ladění: okno registrů](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Informace registru není k dispozici pro skript nebo SQL.

Během ladění, zaregistrujte změnu hodnoty jako kód spustí ve vaší aplikaci. Hodnoty, které se změnily nedávno zobrazí červeně **zaregistruje** okna.

K odebrání nepotřebných prvků, **zaregistruje** okno uspořádá registry do skupiny, které se liší podle platformy a procesor typu. Můžete zobrazit nebo skrytí nabídky registrovat skupiny. Další informace najdete v tématu [postupy: zobrazení a skrytí nabídky registrovat skupiny](../debugger/how-to-display-and-hide-register-groups.md).

Můžete upravit hodnot registru. Další informace najdete v tématu [postupy: Úprava hodnoty registru](../debugger/how-to-edit-a-register-value.md).

**Chcete-li otevřít okno registrů**

1. Povolit ladění na úrovni adres, tak, že vyberete **povolit ladění na úrovni adres** v **nástroje** (nebo **ladění**) > **možnosti**  >  **Ladění**.

1. Při ladění je spuštěná nebo na zarážce, vyberte **ladění** > **Windows** > **zaregistruje**, nebo stiskněte klávesu **Alt** + **5**.

>[!NOTE]
>Dialogová okna a příkazy nabídek se mohou lišit v závislosti na edici Visual Studio nebo nastavení. Chcete-li změnit nastavení, vyberte **nastavení importu a exportu** v sadě Visual Studio **nástroje** nabídky. Další informace najdete v tématu [Resetovat nastavení](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Viz také:

- [Základní informace o ladění: okno registrů](../debugger/debugging-basics-registers-window.md)
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
