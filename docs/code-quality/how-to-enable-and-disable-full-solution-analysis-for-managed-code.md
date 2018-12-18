---
title: 'Postupy: povolení a zákaz úplnou analýzu řešení pro spravovaný kód'
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: d227360be39455662d3d2ebe822810debd655dac
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922769"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Postupy: povolení a zákaz úplnou analýzu řešení pro spravovaný kód

*Úplné řešení analysis* je funkce sady Visual Studio, který vám umožní vidět problémy pouze v otevřených souborů Visual C# nebo Visual Basic v řešení pro analýzu kódu, nebo také v kódu soubory, které jsou uzavřeny. Ve výchozím nastavení, je úplnou analýzu řešení *povoleno* v jazyce Visual Basic a *zakázáno* pro Visual C#.

Může být užitečné, pokud chcete zobrazit všechny problémy v všechny soubory, ale může být také rušivě. Zpomaluje Visual Studio Pokud vaše řešení je velký nebo má mnoho souborů. Chcete-li omezit počet problémů zobrazí a zlepšit výkon v sadě Visual Studio, můžete zakázat úplnou analýzu řešení. V případě potřeby můžete snadno znovu povolit tuto funkci.

## <a name="to-toggle-full-solution-analysis"></a>K přepnutí úplnou analýzu řešení

1. Chcete-li otevřít **možnosti** dialogové okno, v řádku nabídek v sadě Visual Studio zvolte **nástroje** > **možnosti**.

1. V **možnosti** dialogovém okně vyberte **textového editoru** > **C#** nebo **základní**  >   **Rozšířené**.

1. Vyberte **povolit úplnou analýzu řešení** zaškrtněte políčko Povolit úplnou analýzu řešení, nebo zrušte zaškrtnutí políčka ji zakázat. Zvolte **OK** po dokončení.

    ![Povolte úplnou řešení analysis zaškrtávací políčko.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Výsledky povolování a zakazování úplnou analýzu řešení

Na následujícím snímku obrazovky uvidíte výsledky, pokud je povoleno úplnou analýzu řešení. Všechny chyby a problémy v analýzy kódu *všechny* souborů v řešení se zobrazí, bez ohledu na to, jestli jsou soubory otevřené nebo ne.

![Úplnou analýzu řešení povoleno.](../code-quality/media/fsa_enabled.png)

Následující snímek obrazovky ukazuje výsledky ze stejného řešení po zakázání úplnou analýzu řešení. V zobrazují pouze chyby a problémy analýzy kódu v souborech otevřete řešení **seznam chyb**.

![Úplnou analýzu řešení zakázána.](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>Automaticky zakázat úplnou analýzu řešení

Pokud Visual Studio rozpozná, že 200 MB nebo méně systémové paměti je dostupné, se automaticky zakáže úplnou analýzu řešení (a některé další funkce) Pokud je povoleno. Pokud k tomu dojde, zobrazí se výstraha oznamující, že Visual Studio zakázal některé funkce. Tlačítko umožňuje znovu povolit úplnou analýzu řešení, pokud chcete.

![Pozastavení úplnou analýzu řešení textu výstrahy](../code-quality/media/fsa_alert.png)