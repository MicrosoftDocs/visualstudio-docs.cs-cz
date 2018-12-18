---
title: 'Postupy: povolení a zákaz úplné analýzy řešení pro spravovaný kód | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: af0aae4020182f6414d44a2004f98a6fc0df23ca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221868"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Postupy: povolení a zákaz úplné analýzy řešení pro spravovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

POZNÁMKA:]
>  Toto téma se vztahuje pouze k Visual Studio 2015 Update 3 RC a novějším.  
  
 *Úplné analýzy řešení* je funkce sady Visual Studio, který vám umožní vybrat, zda se zobrazí problémy s analýzou kódu pouze v otevřených Visual C# nebo Visual Basic souborů ve vašem řešení, nebo otevřené a uzavřené Visual C# nebo Visual Basic souborů ve vašem řešení.  
  
 Dokáže zjistit všechny problémy ve všech souborech je užitečné, ho může být rušivé a dokonce i zpomalení aplikace Visual Studio, pokud vaše řešení je moc velká, nebo obsahuje velké množství souborů.  Pokud chcete omezit počet problémů zobrazí a zlepšení výkonu sady Visual Studio, můžete zakázat úplné analýzy řešení. Pokud chcete, můžete snadno znovu povolit tuto funkci.  
  
#### <a name="to-toggle-full-solution-analysis"></a>Chcete-li přepnout úplné analýzy řešení  
  
1.  V hlavní nabídce v sadě Visual Studio, zvolte **nástroje** &#124; **možnosti** zobrazíte **možnosti** dialogové okno.  
  
2.  V **možnosti** dialogového okna zvolte **textový Editor** &#124; **jazyka C#** nebo **základní** &#124; **Upřesnit**.  
  
3.  Vyberte **povolení úplné analýzy řešení** zaškrtávací políčko pro povolení úplné analýzy řešení, nebo zrušte zaškrtnutí políčka pro jeho zakázání. Zvolte **OK** tlačítko až budete hotovi.  
  
     ![Povolte úplné řešení analýzy zaškrtávací políčko. ](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Výsledky povolení a zakázání úplné analýzy řešení  
 Na následujícím snímku obrazovky vidíte výsledky při úplné analýzy řešení je povolené. Všechny chyby a problémy s analýzou kódu v *všechny* souborů v řešení se zobrazí, bez ohledu na to, zda jsou dané soubory otevřeny nebo ne.  
  
 ![Úplná analýza řešení povolené. ](../code-quality/media/fsa-enabled.png "FSA_Enabled")  
  
 Následující snímek obrazovky ukazuje výsledky ze stejného řešení po zakázání úplné analýzy řešení. Pouze chyby a problémy s analýzou kódu v otevřete řešení, které soubory se zobrazí v seznamu chyb.  
  
 ![Úplné analýzy řešení zakázáno. ](../code-quality/media/fsa-disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>Automaticky zakázání úplné analýzy řešení  
 Pokud aplikace Visual Studio zjistí, že 200MB nebo méně paměti systému, je k dispozici, se automaticky zakáže úplné analýzy řešení (stejně jako některé jiné funkce) Pokud je povolené. Pokud k tomu dojde, zobrazí se výstraha informuje vás o to. Tlačítko umožňuje opětovné povolení úplné analýzy řešení, pokud chcete udělat.  
  
 ![Pozastavení úplné analýzy řešení textu výstrahy](../code-quality/media/fsa-alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>Další podrobnosti  
 Ve výchozím nastavení je úplné analýzy řešení povolené v jazyce Visual Basic a zakázán pro jazyk Visual C#.  
  
 Visual Studio Update 3 RC zahrnuje modul diagnostické v2 analyzátor kódu, který výrazně snižuje využití paměti a sníží doba využití procesoru při nečinnosti, i když je povolená úplné analýzy řešení.



