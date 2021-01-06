---
title: Just-in-time, ladění, dialogové okno možností | Microsoft Docs
description: Ladění za běhu umožňuje ladit programy, které se spouštějí mimo aplikaci Visual Studio. Naučte se povolit ladění za běhu pro různé typy programů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b346cfdae8671f8f647d41065d5793184fefd3fb
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903867"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Za běhu, ladění, dialogové okno Možnosti
Chcete-li získat přístup **ke stránce za běhu,** přejděte do nabídky **nástroje** a klikněte na **Možnosti**. V dialogovém okně **Možnosti** rozbalte uzel **ladění** a vyberte možnost **za běhu**. Tato stránka umožňuje povolit ladění za běhu pro spravovaný kód, nativní kód a skript. Další informace naleznete v tématu [ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md).

 Můžete povolit ladění za běhu pro tyto typy programů:

- Spravované

- Nativní

- Skript

  Ladění za běhu je technika pro ladění programu, který je spuštěný mimo aplikaci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Můžete spustit program, který jste vytvořili [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mimo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prostředí. Pokud jste povolili ladění za běhu, zobrazí se při chybě dialogové okno s dotazem, jestli chcete ladit.

## <a name="associated-warnings"></a>Přidružená upozornění
 Když navštívíte tuto stránku dialogového okna **Možnosti** , může se zobrazit zpráva s upozorněním, například:

 **Jiný ladicí program se zaregistroval jako ladicí program za běhu. Chcete-li provést opravu, povolte ladění za běhu nebo spusťte opravu sady Visual Studio.**

 Tato zpráva se zobrazí, pokud máte jiný ladicí program, případně starší verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ladicího programu, nastavenou jako ladicí program za běhu.

 Další zpráva, kterou by se mohla zobrazit, je následující:

 **Byly zjištěny chyby registrace ladění za běhu. Chcete-li provést opravu, povolte ladění za běhu nebo spusťte opravu sady Visual Studio.**

 Pokud se zobrazí některá z těchto upozornění, ladění za běhu [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] vyžaduje oprávnění správce, dokud problém neopravíte. Pokud se v těchto podmínkách pokusíte povolit oprávnění pouze jako správce, zobrazí se tato chybová zpráva:

 **Přístup byl odepřen. Nechte správce povolit ladění za běhu nebo opravte instalaci sady Visual Studio.**

## <a name="see-also"></a>Viz také
- [Ladění, dialogové okno Možnosti](../debugger/debugging-options-dialog-box.md)
- [Postupy: Určení nastavení ladicího programu](../debugger/how-to-specify-debugger-settings.md)