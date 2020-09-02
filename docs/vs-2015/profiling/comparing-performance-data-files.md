---
title: Porovnávání datových souborů výkonu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 132a3cb5f7d4257aa0728960cb5bfd50c5ee3066
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62419992"
---
# <a name="comparing-performance-data-files"></a>Porovnání souborů s údaji o výkonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkce porovnání datových souborů Nástroje pro profilaci umožňují vybrat dva soubory sestav (. VSP/or. VSPS) a vygenerujte sestavu, která zobrazuje rozdíly, regrese výkonu a vylepšení, k nimž došlo z jedné relace profilování na druhou.  
  
 Porovnávací sestava datových souborů z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroje pro profilaci porovnává výsledky analýzy v jednom souboru dat profilování s výsledky analýzy standardních hodnot v jiném datovém souboru. Oba datové soubory musí být vygenerovány pomocí stejné metody profilace. Sestava analyzovaných porovnání je uložena jako soubor. vsps.  
  
 Zobrazení sestavy porovnání prezentuje tabulková zobrazení změněných dat. V tabulce se zobrazí rozdílová hodnota nebo se změní ze směrného plánu. Rozdíl se vypočítá pomocí určení rozdílu mezi starou hodnotou, základní hodnotou a výslednou hodnotou z nové analýzy.  
  
 Porovnání dat profileru může být založeno na funkcích v kódu, modulech aplikace, řádcích, ukazateli instrukcí (IP) a typech.  
  
 Data profilace, která jsou k dispozici pro porovnání, zahrnují informace, které se zobrazí ve sloupcích. Definice těchto názvů sloupců najdete v tématu [zobrazení sestav výkonu](../profiling/performance-report-views.md).  
  
 Prahovou hodnotu lze nastavit tak, aby snižovala šum a vyfiltroval všechna data v zobrazení srovnávací tabulky řádků, které se nezměnily zadanou hodnotou.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: porovnání datových souborů výkonu](../profiling/how-to-compare-performance-data-files.md)
