---
title: Povolit & zakázání úplné analýzy řešení pro spravovaný kód
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 26cd267f80f8c7c220771a5c2220d22b66929051
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448923"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Postupy: povolení a zákaz úplné analýzy řešení pro spravovaný kód

*Úplná analýza řešení* znamená, že analýza kódu prověřuje všechny C# soubory nebo Visual Basic v řešení, bez ohledu na to, zda jsou otevřeny v editoru nebo nikoli. Ve výchozím nastavení je úplná analýza řešení *povolena* pro Visual Basic a *zakázáno* pro C#.

Může být užitečné zobrazit všechny problémy ve všech souborech, ale může to být také rušivé. Zpomaluje aplikaci Visual Studio, pokud je vaše řešení velmi velké nebo má mnoho souborů. Pokud chcete omezit počet zobrazených problémů a zvýšit výkon sady Visual Studio, můžete zakázat kompletní analýzu řešení. V případě potřeby můžete tuto funkci snadno znovu povolit.

Na následujícím obrázku je povolena kompletní analýza řešení. Zobrazí se problémy s kompilátorem a analýzou kódu ve všech souborech v řešení, a to i v případě, že nejsou otevřeny.

![Úplná analýza řešení je povolena.](../code-quality/media/fsa_enabled.png)

Následující obrázek znázorňuje výsledky ze stejného řešení po zakázání úplné analýzy řešení. V Seznam chyb se zobrazují jenom chyby kompilátoru a problémy analýzy kódu v otevřených souborech řešení.

![Úplná analýza řešení je zakázaná.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Přepnout úplnou analýzu řešení

1. Chcete-li otevřít dialogové okno **Možnosti** , na panelu nabídek v aplikaci Visual Studio vyberte možnost **nástroje** > **Možnosti**.

1. V dialogovém okně **Možnosti** vyberte možnost **textový editor** > **C#** nebo **Basic** > **Advanced**.

1. Zaškrtnutím políčka **Povolit úplnou analýzu řešení** povolíte úplnou analýzu řešení, nebo zaškrtnutím políčka zakážete. Až skončíte, klikněte na **OK** .

   ![Zaškrtněte políčko úplná analýza řešení.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Automaticky zakázat kompletní analýzu řešení

Pokud aplikace Visual Studio zjistí, že je k dispozici 200 MB nebo méně systémové paměti, automaticky zakáže úplnou analýzu řešení (a další funkce), pokud je povolená. V takovém případě se zobrazí výstraha informující o tom, že aplikace Visual Studio zakázala některé funkce. Tlačítko umožňuje znovu povolit úplnou analýzu řešení, pokud chcete.

![Text výstrahy, která pozastavuje úplnou analýzu řešení](../code-quality/media/fsa_alert.png)
