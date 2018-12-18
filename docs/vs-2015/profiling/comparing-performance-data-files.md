---
title: Porovnání datových souborů výkonu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3aa37462915b3155a21248a968325a24b8da05bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741585"
---
# <a name="comparing-performance-data-files"></a>Porovnání datových souborů výkonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilace funkci porovnání souborů dat nástroje vám umožní vybrat dva soubory sestav (. VSP nebo. VSPS) soubory a generovat sestavy, která ukazuje rozdíly, regrese výkonu a vylepšení, ke kterým došlo v jedné relaci profilace na druhý.  
  
 Sestava porovnání datových souborů z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů pro profilaci sady porovnává výsledky analýzy v jeden soubor dat profilování pro výsledky analýzy standardních hodnot v jiném datovém souboru služby. Oba soubory dat musí být vygenerováno stejným způsobem, profilace. Zprávy analyzované porovnání je uložen jako soubor .vsps.  
  
 Zobrazení sestav porovnání představuje zobrazení tabulky změněná data. V tabulce představuje rozdílů nebo změnit ze standardních hodnot. Delta se počítá tak, že určíte rozdíl mezi původní hodnoty, základní hodnota a hodnota výsledku z nové analýzy.  
  
 Porovnání dat profiler může být založen na funkce v kódu, moduly v aplikaci, řádky, ukazatele na instrukce (IP) a typy.  
  
 Data profilace, která je k dispozici pro porovnání obsahuje informace, které se zobrazí ve sloupci. Definice tyto názvy sloupců, naleznete v tématu [zobrazení sestav výkonu](../profiling/performance-report-views.md).  
  
 Prahovou hodnotu můžete nastavit ke snížení šumu a vyfiltrovat všechna data v zobrazení tabulky porovnání řádků, které nebyly změněny o určenou hodnotu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Porovnání souborů s údaji o výkonu](../profiling/how-to-compare-performance-data-files.md)



