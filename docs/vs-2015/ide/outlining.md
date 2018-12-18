---
title: Sbalování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
ms.assetid: d1476758-9d35-4d74-b63c-310661932ecd
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: af7f854f6e097471cdd744537a4be4cbd1646400
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282513"
---
# <a name="outlining"></a>Sbalování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete skrýt nějaký kód ze zobrazení sbalením oblasti kódu tak, aby se objevila pod znaménko plus (+). Rozbalte sbalený oblast kliknutím na symbol plus. (Nebo stiskněte klávesu CTRL + M + M sbalit oblast a potom CTRL + M + M a rozbalte ho znovu.) Sbalování oblastí můžete také sbalit dvojitým kliknutím na kterýkoli řádek v oblasti na okraji osnovy, které se zobrazí vlevo kód. Když najedete myší sbaleného regionu, můžete zobrazit obsah sbaleného regionu jako popisek.  
  
 Když najedete myší na okraji pomocí myši, jsou také zvýrazněna oblastí na okraji osnovy. Výchozí barva zvýraznění se může zdát slabé místo v některých konfiguracích barvu. Můžete změnit v **Nástroje/možnosti/prostředí/písma a barvy/Collapsible oblasti**.  
  
 Pokud pracujete v osnovy kódu, můžete rozbalit oddíly, které chcete pracovat, je sbalení při dokončení a poté přesuňte do další sekce. Pokud nechcete, aby sbalování zobrazí, můžete použít **ukončit sbalování** příkazu odeberte informace osnovy bez narušení základní kód.  
  
 **Zpět** a **znovu** příkazy na **upravit** nabídky, ovlivňují tyto akce. **Kopírování**, **Vyjmout**, **vložit**, a operace přetažení myší zachovat popisující informací, ale stav sbalitelná oblast. Například při kopírování oblast, která je sbalena, **vložte** operace se vložit zkopírovaný text jako rozbalená oblast.  
  
> [!CAUTION]
>  Při změně ohraničené oblasti osnovu mohou být ztraceny. Například odstranění nebo operace hledání a nahrazení můžou vymazat konec oblasti.  
  
 Následující příkazy můžete najít na **úpravy/Osnova** podnabídka.  
  
|||  
|-|-|  
|Skrýt výběr|(CTRL + M, CTRL + H) - sbalí vybraný blok kódu, který obvykle nebude k dispozici pro sbalení, třeba `if` bloku. Chcete-li odebrat vlastní oblasti, použijte **Zastavit skrývání aktuálního** (nebo CTRL + M, CTRL + U). Není k dispozici v jazyce Visual Basic.|  
|Přepne sbalování osnovy|– Vrátí aktuální stav skrytý nebo rozšířené nejvnitřnější sbalení části, pokud kurzor spočívá ve vnořených sbalenou část.|  
|Přepnout všechny osnovy|(CTRL + M, CTRL + L) – nastaví všechny oblasti stejné rozbalit nebo sbalit stavu. Pokud jsou rozbaleny v některých oblastech a některé sbalena, pak sbalených oblasti jsou rozbaleny.|  
|Ukončit sbalování|(CTRL + M, CTRL + P) – odebere všechny osnovy informace pro celý dokument.|  
|Zastavit skrývání aktuálního|(CTRL + M, CTRL + U) – odebere sbalování informace pro aktuálně vybrané oblasti definované uživatelem. Není k dispozici v jazyce Visual Basic.|  
|Sbalit do definic|(CTRL + M, CTRL + O) - sbalí všechny typy jako objekty její členové.|  
|Sbalit blok:\<logické hraniční >|(Visual C++) Sbalí oblast ve funkci obsahující kurzor. Například pokud se kurzor nachází uvnitř smyčky, smyčky je skrytá.|  
|Sbalit vše do: \<logické struktury >|(Visual C++) Sbalí všechny struktury uvnitř funkce.|  
  
 Visual Studio SDK můžete použít také k definování oblastí textu, které chcete rozbalit nebo sbalit. Zobrazit [návod: sbalení](../extensibility/walkthrough-outlining.md).



