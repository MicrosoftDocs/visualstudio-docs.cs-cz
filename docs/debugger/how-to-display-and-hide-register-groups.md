---
title: Zobrazení a skrytí skupin registru | Microsoft Docs
description: Okno Registry, které je k dispozici, pokud je povoleno ladění na úrovni adres, uspořádá Registry do skupin. Přečtěte si, jak nastavit, které skupiny se zobrazí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.registergroups
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, displaying and hiding register groups
- register groups, displaying and hiding
ms.assetid: 6be5dfb4-4cfe-4daf-b538-60405640857d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dee270bc4c4f9417bdf412974a12d687635e312f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899274"
---
# <a name="how-to-display-and-hide-register-groups-c-c-visual-basic-f"></a>Postupy: zobrazení a skrytí skupin registrů (C#, C++, Visual Basic, F #)

Okno **Registry** je dostupné pouze v případě, že je povoleno ladění na úrovni adres v dialogovém okně **Možnosti** , uzel **ladění** , **Obecné** kategorie.

Chcete-li snížit přehlednost, okno **Registry** uspořádá Registry do skupin. Pokud kliknete pravým tlačítkem myši na okno **Registry** , zobrazí se místní nabídka obsahující tyto skupiny, které můžete zobrazit nebo skrýt, jak vidíte podle následujícího postupu.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

## <a name="display-or-hide-register-groups"></a>Zobrazení nebo skrytí skupin registrací

1. Klikněte pravým tlačítkem na okno **Registry** .

2. V místní nabídce vyberte skupiny registrů, které chcete zobrazit nebo skrýt.

     Skupiny registrů, které nejsou podporované hardwarem, na kterém ladíte, jsou v místní nabídce zakázané, takže je nejde vybrat.

## <a name="see-also"></a>Viz také

- [Postupy: Použití okna Registry](../debugger/how-to-use-the-registers-window.md)