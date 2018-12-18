---
title: 'DA0504: Maximum pracovní sady v bajtech pro profilovaný proces | Dokumentace Microsoftu'
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
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a39171c8786f3b2149a50bd3c4a6915575f050ae
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800195"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: Maximum Pracovní sady v bajtech pro profilovaný Proces
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id pravidla | DA0504 |  
| Kategorie | Správa prostředků |  
| Metoda profilace | Všechny |  
| Zpráva | Tato informace byla shromážděna pouze pro informaci. Čítač pracovní sady procesu měří využití fyzické paměti procesem, který profilujete. Hlášená hodnota je maximum pozorované přes všechny intervaly měření. |  
| Typ pravidla | Informace |  
  
 Při profilování pomocí vzorkování, paměti .NET nebo metodám sporu prostředků, musíte shromáždit minimálně 10 vzorky k aktivaci tohoto pravidla.  
  
## <a name="rule-description"></a>Popis pravidla  
 Tato zpráva znamená maximální velikost fyzické paměti, v bajtech, kterou aktuálně používá proces. Pracovní sada procesu představuje stránek z adresního prostoru procesu, která jsou aktuálně umístěny ve fyzické paměti. Toto pravidlo sestavy maximální hodnota pracovní sady procesu během profilace byl aktivní.  
  
 Hodnotu hlášenou zahrnuje rezidenční stránky ze segmentu sdílené paměti, které odkazoval na proces. Odkazy procesu obsažené v příslušných segmentech sdílené paměti, které jsou započteny sdílené knihovny DLL. Hodnota procesu pracovní sada může být vyšší než velikost virtuální paměti, která byla přidělena procesu a z důvodu sdílené paměti segmenty.  
  
 Velikost pracovní sady procesu odráží kolik virtuální paměti aktivně je využívána procesem. Je také vliv na množství fyzické paměti (nebo paměti RAM) k dispozici ke spuštění aplikace a množství kolizí pro tuto fyzickou paměť z jiných spuštěné procesy. Další informace o pracovní sady procesu najdete v tématu [pracovní sady](http://go.microsoft.com/fwlink/?LinkId=177830) v dokumentaci k Windows Správa paměti MSDN.  
  
## <a name="how-to-use-rule-data"></a>Jak používat Data pravidla  
 Toto pravidlo shromažďuje ze zařízení sledování výkonu Windows tato data měření a ohlásí ji pouze pro informaci. Použije k porovnání výkonu různých verzí nebo sestavení tohoto programu nebo porozumět výkonu aplikace v rámci různých testovacích scénářů.  
  
 Dvakrát klikněte na zprávu v okně Seznam chyb, přejděte [zobrazení značky](../profiling/marks-view.md) dat profilování. Najít **Process\Working nastavit** a **Paměť\Stránky/s** čítač sloupce. Potom vrátí maximální hodnotu **Process\Working nastavit** a porovnat **Paměť\Stránky/s** hodnotu. Pracovní sady maximální je často přidružený interval, ve kterém je snížení vstupně-výstupní operace stránkování, zejména v případě, že tento počítač je omezenou pamětí.



