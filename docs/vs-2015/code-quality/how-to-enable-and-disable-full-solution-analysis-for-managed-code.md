---
title: 'Postupy: povolení a zákaz úplné analýzy řešení pro spravovaný kód | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 72b27bf9dcc1f0ee8a222ac701f2ffae4fc68614
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646282"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Postupy: povolení a zákaz úplné analýzy řešení pro spravovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ZNAČTE
> Toto téma se vztahuje pouze na Visual Studio 2015 Update 3 RC a novější.

 *Úplná analýza řešení* je funkce sady Visual Studio, která umožňuje zvolit, zda se v řešení zobrazují problémy s analýzou kódu C# pouze v otevřených nebo Visual Basicch souborech nebo v otevřených i uzavřených vizuálních C# nebo Visual Basicch souborech řešení.

 I když se může zobrazit všechny problémy ve všech souborech, může být rušivý a i pomalý, pokud je vaše řešení velmi velké nebo má hodně souborů.  Pokud chcete omezit počet zobrazených problémů a zvýšit výkon sady Visual Studio, můžete zakázat kompletní analýzu řešení. Pokud chcete, můžete tuto funkci snadno znovu povolit.

#### <a name="to-toggle-full-solution-analysis"></a>Přepnutí úplné analýzy řešení

1. V hlavní nabídce v aplikaci Visual Studio klikněte na možnost **Možnosti** **nástrojů** &#124; . zobrazí se dialogové okno **Možnosti** .

2. V dialogovém okně **Možnosti** vyberte možnost **textový editor** &#124; **C#** nebo **základní** &#124; **Upřesnit**.

3. Zaškrtnutím políčka **Povolit úplnou analýzu řešení** povolíte úplnou analýzu řešení, nebo zaškrtnutím políčka zakážete. Až budete hotovi, klikněte na tlačítko **OK** .

     ![Zaškrtněte políčko úplná analýza řešení.](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Výsledky povolování a zakazování kompletních analýz řešení
 Na následujícím snímku obrazovky vidíte výsledky, pokud je povolená úplná analýza řešení. Všechny chyby a problémy analýzy kódu se zobrazí ve *všech* souborech v řešení, bez ohledu na to, zda jsou soubory otevřeny nebo nikoli.

 ![Úplná analýza řešení je povolena.](../code-quality/media/fsa-enabled.png "FSA_Enabled")

 Následující snímek obrazovky ukazuje výsledky ze stejného řešení po zakázání úplné analýzy řešení. V Seznam chyb se zobrazí pouze chyby a problémy analýzy kódu v otevřených souborech řešení.

 ![Úplná analýza řešení je zakázaná.](../code-quality/media/fsa-disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>Automatické zakázání úplné analýzy řešení
 Pokud aplikace Visual Studio zjistí, že je k dispozici 200 MB nebo méně systémové paměti, automaticky zakáže úplnou analýzu řešení (a také jiné funkce), pokud je povolená. Pokud k tomu dojde, zobrazí se výstraha s upozorněním. Tlačítko umožňuje znovu povolit úplnou analýzu řešení, pokud to chcete udělat.

 ![Text výstrahy, která pozastavuje úplnou analýzu řešení](../code-quality/media/fsa-alert.png "FSA_Alert")

## <a name="additional-details"></a>Další podrobnosti
 Ve výchozím nastavení je úplná analýza řešení povolená pro Visual Basic a zakázaná C#pro Visual.

 Visual Studio Update 3 RC obsahuje modul vylepšeného diagnostiky analyzátoru kódu v2, který významně snižuje využití paměti a snižuje čas procesoru na nečinnost, a to i v případě, že je povolená úplná analýza řešení.
