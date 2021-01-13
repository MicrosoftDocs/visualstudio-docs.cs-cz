---
title: Zobrazení hodnot registru v ladicím programu | Microsoft Docs
description: Zobrazit hodnoty registru v okně Registry v aplikaci Visual Studio. Během ladění zaregistruje změny hodnot, jako se ve vaší aplikaci spustí kód.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/19/2018
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8422738b5c46b5482ac65cd24ccc903acdb4506e
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148036"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Zobrazení hodnot registru v okně Registry (C#, C++, Visual Basic, F #)

Okno **Registry** zobrazuje obsah registru během ladění sady Visual Studio. Úvod do konceptů za registry a v okně **Registry** najdete v části [základy ladění: Registry Window](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Informace o registraci nejsou k dispozici pro skripty nebo aplikace SQL.

Během ladění zaregistruje změny hodnot, jako se ve vaší aplikaci spustí kód. Hodnoty, které se v poslední době změnily, se v okně **Registry** zobrazí červeně.

Chcete-li snížit přehlednost, okno **Registry** uspořádá Registry do skupin, které se liší podle typu platformy a procesoru. Můžete zobrazit nebo skrýt skupiny registrů. Další informace najdete v tématu [Postup: zobrazení a skrytí skupin registrů](../debugger/how-to-display-and-hide-register-groups.md).

Informace o příznacích, které vidíte v okně **Registry** , naleznete v části [o okně Registry](../debugger/debugging-basics-registers-window.md) .

Hodnoty registru můžete upravovat. Další informace najdete v tématu [Postupy: Úprava hodnoty registru](../debugger/how-to-edit-a-register-value.md).

**Otevření okna Registry**

1. Povolte ladění na úrovni adres výběrem možnosti **Povolit ladění na úrovni adresy** v **nástrojích** (nebo **ladění**) >   >  **ladění** možností.

1. Když je ladění spuštěno nebo na zarážce, vyberte **ladit**  >  **Registry systému Windows**  >  nebo stiskněte **ALT** + **5**.

>[!NOTE]
>Dialogová okna a příkazy nabídek se mohou lišit v závislosti na vaší edici nebo nastavení sady Visual Studio. Chcete-li změnit nastavení, zvolte **Nastavení importu a exportu** v nabídce **nástroje** sady Visual Studio. Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Viz také

- [Základy ladění: okno Registry](../debugger/debugging-basics-registers-window.md)
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
