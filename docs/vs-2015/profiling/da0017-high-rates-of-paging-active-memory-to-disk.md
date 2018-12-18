---
title: 'DA0017: Vysoké míry stránkování aktivní paměti na disk | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.17
- vs.performance.rules.DA0017
- vs.performance.DA0017
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a7fbe924ee3d0f5dbd142d8e7f7020c6eed1ee5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766597"
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017: Vysoké míry stránkování aktivní paměti na disk
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id pravidla | DA0017 |  
| Kategorie | Paměti a stránkování |  
| Metoda profilace | Všechny |  
| Zpráva | Dochází k vysoké míry stránkování aktivní paměti na disk. Aplikace může být vázána na paměť. |  
| Typ pravidla | Informace |  
  
 Při profilování pomocí vzorkování, paměti .NET nebo metodám sporu prostředků, musíte shromáždit minimálně 10 vzorky k aktivaci tohoto pravidla.  
  
## <a name="cause"></a>příčina  
 Údaje o výkonu systému, která byla shromážděna během profilování označuje, že vysokým mírám stránkování aktivní paměti na a z disku došlo k chybě během spuštění profilování. Stránkování sazby na této úrovni obvykle ovlivní výkon aplikace a rychlost odezvy. Zvažte snížení přidělení paměti prostřednictvím revize algoritmy. Budete také muset zvážit požadavky na paměť vaší aplikace.  
  
## <a name="rule-description"></a>Popis pravidla  
  
> [!NOTE]
>  Tento informační pravidlo je vyvoláno, když dosáhnou významnou úrovně stránkování aktivní paměti. Pokud dojde k velmi vysoký stupeň stránkování, pravidlo upozornění [DA0014: velmi vysoké míry stránkování aktivní paměti na disk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md) aktivuje místo.  
  
 Nedostatek fyzické paměti může způsobovat nadměrné stránkování na disk. Pokud operace stránkování převládají na poli použití fyzického disku, ve které se nachází stránkovací soubor, může zpomalit další disk orientovaných na aplikace operace ke stejnému disku.  
  
 Stránky jsou často číst z disku nebo zapsaných na disk v hromadné operace stránkování. Počet stránek výstupu za sekundu je často mnohem větší než počet zápisů stránek/s, například. Vzhledem k tomu stránky výstupu za sekundu také zahrnuje změněná data stránek z mezipaměti systému souborů. Však není vždy jednoduché určit, který proces přímo zodpovídá za stránkování a proč.  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Dvakrát klikněte na zprávu v okně Seznam chyb, přejděte [značky](../profiling/marks-view.md) zobrazení. Najít **Paměť\Stránky/s** sloupce. Zjistěte, jestli konkrétní fázích provádění programu kde aktivity vstupně-výstupní operace stránkování je těžší než jiné.  
  
 Pokud se shromažďování dat profil pro aplikaci ASP.NET ve scénáři zátěžového testování, zkuste spustit zátěžový test znovu na počítače s nakonfigurovanou další fyzické paměti (nebo paměti RAM).  
  
 Zvažte snížení přidělení paměti tak, že revize algoritmy a jak se vyhnout vysokými nároky na paměť rozhraní API, jako je například String.Concat a String.Substring.



