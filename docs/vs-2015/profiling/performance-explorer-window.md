---
title: Prohlížeč výkonu okno | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
ms.assetid: cb6a6efc-93a5-49a2-8d03-6969b5f3b6d7
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a370ae802408ecc821de4cd15824f9d1fca42b75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195529"
---
# <a name="performance-explorer-window"></a>Okno Prohlížeč výkonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **prohlížeč výkonu** v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaném vývojovém prostředí (IDE) umožňuje konfigurovat a spouštět relace výkonu pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroje pro profilaci.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="performance-explorer-toolbar"></a>Panel nástrojů Prohlížeč výkonu  
 Na panelu nástrojů **prohlížeč výkonu** jsou k dispozici následující možnosti:  
  
- **Spustit Průvodce výkonem** – zobrazí Průvodce výkonem, který přidá novou relaci výkonu do okna Prohlížeč výkonu.  
  
- **Nová výkonnostní relace** – přidá do okna Prohlížeč výkonu prázdnou relaci výkonu.  
  
- **Spustit** – seznam **spouštěcích** tlačítek umožňuje spustit cílovou aplikaci, která má okamžitě povolené profilování (**Spustit s profilací**), nebo s pozastaveným profilací (**Spustit s pozastaveným profilací**).  
  
- **Metoda** – určuje, jestli je metoda profilování relace vzorkování nebo instrumentace.  
  
- **Zastavit** – okamžitě ukončí cílovou aplikaci a Profiler.  
  
- **Připojit nebo odpojit** – zobrazí dialogové okno **Připojit profiler k procesu** pro výběr běžícího procesu, ke kterému se má připojit Profiler.  
  
## <a name="performance-explorer-window"></a>Okno Prohlížeč výkonu  
 Okno **prohlížeč výkonu** obsahuje ovládací prvek stromové struktury, který zobrazuje binární soubory a soubory sestav s daty jedné nebo více relací výkonu.  
  
- **Název relace** – kořen ovládacího prvku stromu obsahuje název relace. Klikněte pravým tlačítkem myši na název relace a nastavte vlastnosti relace nebo spusťte cílovou aplikaci a Profiler.  
  
- **Cíle** – zobrazí názvy binárních souborů, které se mají profilovat v relaci. Kliknutím pravým tlačítkem myši na možnost **cíle** můžete přidat nebo odebrat binární, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekt nebo Web. Klikněte pravým tlačítkem myši na název cíle a nastavte vlastnosti pro jednotlivé binární soubory.  
  
- **Sestavy** – zobrazí názvy datových souborů profileru, které jsou generovány pro relaci. Kliknutím pravým tlačítkem myši na **sestavy** můžete přidat existující sestavu nebo porovnat dva datové soubory profileru. Kliknutím pravým tlačítkem myši na název sestavy otevřete, odeberete nebo vyexportujete datový soubor profileru.  
  
## <a name="see-also"></a>Viz také  
 [Přehledy](../profiling/overviews-performance-tools.md)   
 [Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md)   
 [Řízení shromažďování dat](../profiling/controlling-data-collection.md)
