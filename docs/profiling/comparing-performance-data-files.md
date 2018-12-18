---
title: Porovnávání souborů Data výkonu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 20324a3026f5c32fcc1525f1c5afcd20b1b62332
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34690728"
---
# <a name="compare-performance-data-files"></a>Porovnání datových souborů výkonu
Profilace funkce porovnání souborů nástrojů data vám umožní vybrat dvě souborů sestav (. *Vsp* /nebo. *vsps*) soubory a vygenerovat sestavu, která zobrazuje rozdíly, výkon regresí a vylepšení, které došlo k jedné relace profilování na druhý.  
  
 Sestavy porovnání datových souborů z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástrojích pro profilaci porovná výsledky analýzu v jednom souboru profilování data na výsledky analýzy standardních hodnot v jiném datovém souboru. Oba soubory dat musí byl vytvořen pomocí stejné metody profilování. Sestava analyzovaných porovnání se uloží jako. *vsps* souboru.  
  
 Zobrazení sestavy porovnání uvede tabulky zobrazení změněná data. V tabulce uvede rozdílů, nebo změňte ze směrného plánu. Rozdíl je vypočtena určením rozdíl mezi původní hodnoty, hodnotu směrného plánu a výslednou hodnotu z nové analýzy.  
  
 Porovnání profileru dat může být založen na funkce v kódu, modulů v aplikaci, řádky, ukazatele na instrukce (IP) a typy.  
  
 Profilace data, která je k dispozici pro porovnání obsahuje informace, které se zobrazí ve sloupcích. Definice názvů těchto sloupců naleznete v tématu [zobrazení sestav výkonu](../profiling/performance-report-views.md).  
  
 Prahovou hodnotu lze nastavit pro snížení šumu a filtrovat všechna data v tabulce zobrazení porovnání řádků, které nebyly změněny o určenou hodnotu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Porovnání datových souborů výkonu](../profiling/how-to-compare-performance-data-files.md)