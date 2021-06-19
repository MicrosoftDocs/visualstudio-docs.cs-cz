---
title: Zobrazení hodnot registru v ladicím | Microsoft Docs
description: Hodnoty registru si můžete zobrazit v okně Registry v Visual Studio. Během ladění se hodnoty registru mění při provádění kódu ve vaší aplikaci.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2648f74453f51cd8d655ccb0c2344eb1030c1ed
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385393"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Zobrazení hodnot registru v okně Registry (C#, C++, Visual Basic, F#)

V **okně Registry** se během ladění registru Visual Studio registru. Základní informace o konceptech registrů a okně **Registry** najdete v tématu Základy [ladění: Okno Registry.](../debugger/debugging-basics-registers-window.md)

> [!NOTE]
> Informace o registraci nejsou k dispozici pro skripty nebo aplikace SQL.

Během ladění se hodnoty registru mění při provádění kódu ve vaší aplikaci. Hodnoty, které se nedávno změnily, se v okně **Registry** zobrazí červeně.

Aby se snížily  nepotřbné položky, okno Registry uspořádá registry do skupin, které se liší podle typu platformy a procesoru. Registrační skupiny můžete zobrazit nebo skrýt. Další informace najdete v tématu [Postupy: Zobrazení a skrytí skupin registrů.](../debugger/how-to-display-and-hide-register-groups.md)

Informace o příznakech, které vidíte v okně **Registry,** najdete v tématu [Informace o okně Registry.](../debugger/debugging-basics-registers-window.md)

Hodnoty registru můžete upravit. Další informace najdete v tématu [Postupy: Úprava hodnoty registru](../debugger/how-to-edit-a-register-value.md).

**Otevření okna Registry**

1. Povolte ladění na úrovni adres výběrem **možnosti Povolit ladění na** úrovni adres v části Nástroje (nebo Ladit) > **Možnosti**    >  **ladění.**

1. Při spuštěném ladění nebo na zarážce vyberte **Ladit** registry  >  **Windows**  >  nebo stiskněte **Alt** + **5.**

>[!NOTE]
>Dialogová okna a příkazy nabídky se můžou lišit v závislosti na Visual Studio edici nebo nastavení. Pokud chcete nastavení změnit, vyberte **v nabídce Nástroje** Visual Studio **Import** a export. Další informace najdete v tématu [Resetování nastavení.](../ide/environment-settings.md#reset-settings)

### <a name="see-also"></a>Viz také

- [Základy ladění: Okno Registry](../debugger/debugging-basics-registers-window.md)
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
