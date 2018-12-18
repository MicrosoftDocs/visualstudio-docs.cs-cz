---
title: 'Postupy: porovnávání datových souborů výkonu | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eeb9f26091deaf995ef1221d39aa7264553f5c70
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815376"
---
# <a name="how-to-compare-performance-data-files"></a>Postupy: porovnání výkonu datových souborů
Můžete porovnat výsledky dva různé profileru datových souborů (. *Vsp* nebo. *vsps*) tak, že vytvoříte porovnání ("rozdílové") sestavy nebo zobrazení. Porovnání se zobrazuje rozdíly, výkon regresí a vylepšení, které došlo k jedné relace profilování na druhý.  
  
 Sestava rozdílové uvede zobrazení tabulky dat. V tabulce uvede rozdílů, nebo změňte ze směrného plánu. Tato hodnota je vypočtena určením rozdílu mezi původní hodnoty, hodnota směrného plánu a výslednou hodnotu z nové analýzy.  
  
 Porovnání profileru dat může být založen na funkce v kódu, modulů v aplikaci, řádky, ukazatele na instrukce (IP) a typy.  
  
 Prahovou hodnotu lze nastavit pro snížení šumu a filtrovat všechna data v tabulce zobrazení řádků, které nebyly změněny o určenou hodnotu.  
  
### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Vytvoření zobrazení porovnání souborů pro projekt v Průzkumníku výkonu  
  
1.  V **prohlížeč výkonu**v části **sestavy**, vyberte. *Vsp* nebo. *vsps* soubor sestavy, který chcete použít jako hodnoty standardních hodnot pro porovnání.  
  
2.  Vyberte. *vsp* nebo. *vsps* sestavy soubory, které chcete porovnat.  
  
3.  Klikněte pravým tlačítkem na vybrané soubory a potom klikněte na **porovnat sestavy**.  
  
### <a name="to-compare-values"></a>Pro porovnání hodnot  
  
1.  Vyberte **sestavy porovnání** kartě v okně zobrazení sestavy.  
  
2.  V **tabulky** rozevíracího seznamu vyberte funkce nebo moduly k porovnání.  
  
3.  V **sloupec** rozevíracího seznamu vyberte hodnotu, která chcete porovnat.  
  
4.  (volitelné) Zadejte hodnotu pro **prahová hodnota**.  
  
5.  Klikněte na tlačítko **použít**.  
  
### <a name="to-compare-report-files"></a>Pro porovnání souborů sestav  
  
1.  Na **analyzovat** nabídce vyberte možnost **porovnat sestavy pro zvýšení výkonu**.  
  
2.  V **vyberte analysis soubory pro porovnání** , procházet a vyberte **směrného plánu souboru** soubor analýzy (. *Vsp* nebo. *vsps*) a **porovnání souborů** (. *Vsp* nebo. *vsps*).  
  
3.  Click **OK**.