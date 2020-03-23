---
title: Povolení & zakázat úplnou analýzu řešení pro spravovaný kód
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d699dd74315cfc36820c1cdb4120543e0290b1a1
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79428269"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Postup: Povolení a zakázání úplné analýzy řešení spravovaného kódu

*Úplná analýza řešení* znamená, že analýza kódu zkoumá všechny soubory jazyka C# nebo Visual Basic v řešení, bez ohledu na to, zda jsou otevřeny v editoru nebo ne. Ve výchozím nastavení je pro jazyk Visual Basic *povolena* úplná analýza řešení a pro jazyk C# *je zakázána.*

Může být užitečné zobrazit všechny problémy ve všech souborech, ale může být také rušivé. Zpomaluje Visual Studio dolů, pokud vaše řešení je velmi velké nebo má mnoho souborů. Chcete-li omezit počet zobrazených problémů a zlepšit výkon sady Visual Studio, můžete zakázat úplnou analýzu řešení. V případě potřeby můžete tuto funkci snadno znovu povolit.

Na následujícím obrázku je povolena úplná analýza řešení. Problémy s analýzou kompilátoru a kódu ve všech souborech v řešení jsou zobrazeny, i když nejsou otevřené.

![Úplná analýza řešení povolena.](../code-quality/media/fsa_enabled.png)

Následující obrázek znázorňuje výsledky ze stejného řešení po zakázání úplné analýzy řešení. V seznamu chyb se zobrazí pouze chyby kompilátoru a problémy s analýzou kódu v otevřených souborech řešení.

![Úplná analýza řešení zakázána.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Přepnout úplnou analýzu řešení

1. Chcete-li otevřít dialogové okno **Možnosti,** zvolte na řádku nabídek v sadě Visual Studio **možnostI** > **nástroje**.

1. V dialogovém okně **Možnosti** zvolte **Textový editor** > **C#** nebo **Základní** > **upřesnit**.

1. Zaškrtnutím políčka **Povolit úplnou analýzu řešení** povolíte úplnou analýzu řešení nebo zrušte zaškrtnutí políčka a zakážete ji. Až budete hotovi, zvolte **OK.**

   ![Povolit úplné zaškrtávací políčko analýzy řešení.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Automatické zakázání úplné analýzy řešení

Pokud Visual Studio zjistí, že 200 MB nebo méně systémové paměti je k dispozici, automaticky zakáže úplnou analýzu řešení (a některé další funkce), pokud je povolena. Pokud k tomu dojde, zobrazí se výstraha informující o tom, že sada Visual Studio zakázala některé funkce. Tlačítko umožňuje znovu povolit úplnou analýzu řešení, pokud chcete.

![Výstražný text pozastavující úplnou analýzu řešení](../code-quality/media/fsa_alert.png)
