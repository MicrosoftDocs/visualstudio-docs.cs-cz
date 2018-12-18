---
title: Okno Prohlížeč výkonu | Dokumentace Microsoftu
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
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
ms.assetid: cb6a6efc-93a5-49a2-8d03-6969b5f3b6d7
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20a68ecb9f45265dd304a9bebf601020c6a300b8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798193"
---
# <a name="performance-explorer-window"></a>Okno Prohlížeč výkonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Prohlížeč výkonu** okna [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE) umožňuje konfiguraci a spuštění relace výkonu pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů pro profilaci sady.  
  
 **Požadavky**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="performance-explorer-toolbar"></a>Panel nástrojů Průzkumník výkonu  
 Tyto možnosti jsou k dispozici na **prohlížeč výkonu** nástrojů:  
  
-   **Spustit Průvodce výkonem** -zobrazí Průvodce výkonu a přidat novou relaci výkonu v okně Průzkumník výkonu.  
  
-   **Novou relaci výkonu** – přidá prázdný výkonnostní relaci v okně Průzkumník výkonu.  
  
-   **Spuštění** – **spuštění** příkaz seznamu umožňuje spustit cílovou aplikaci, která má, okamžitě povolená profilace (**spustit s nástrojem pro profilaci**) nebo pozastavené (profilací **Pozastaví spuštění profilací**).  
  
-   **Metoda** – Určuje, jestli je metodu relace profilace vzorkování nebo instrumentace.  
  
-   **Zastavit** – okamžitě ukončí cílové aplikace a profiler.  
  
-   **Attach/Detach** – zobrazí **připojit Profiler k procesu** dialogové okno Vybrat spuštěný proces, ke kterému chcete připojit profiler.  
  
## <a name="performance-explorer-window"></a>Okno Prohlížeč výkonu  
 **Prohlížeč výkonu** okno obsahuje ovládací prvek stromu, který zobrazuje binární soubory a soubory data sestav z jednoho nebo více výkonnostních relací.  
  
-   **Název relace** – kořenový adresář ovládacího prvku strom obsahuje název relace. Klikněte pravým tlačítkem na název relace, můžete nastavit vlastnosti relace nebo spustit cílovou aplikaci a profiler.  
  
-   **Cíle** -zobrazí názvy binárních souborů, které se má být profilována v relaci. Klikněte pravým tlačítkem na **cíle** s přidáváním a odebíráním binární soubor, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu nebo Web. Klikněte pravým tlačítkem na název cílového nastavení vlastností pro jednotlivé binárního souboru.  
  
-   **Sestavy** – zobrazuje názvy souborů dat profileru, které jsou generovány pro relaci. Klikněte pravým tlačítkem na **sestavy** můžete přidat existující sestavy nebo porovnání dvou souborů dat profileru. Klikněte pravým tlačítkem na název sestavy, čímž otevřete, odebrat nebo exportovat datového souboru profilování.  
  
## <a name="see-also"></a>Viz také  
 [Přehledy](../profiling/overviews-performance-tools.md)   
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)   
 [Řízení shromažďování dat](../profiling/controlling-data-collection.md)



