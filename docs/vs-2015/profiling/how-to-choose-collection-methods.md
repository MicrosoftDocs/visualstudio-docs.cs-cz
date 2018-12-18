---
title: 'Postupy: výběr metod kolekcí | Dokumentace Microsoftu'
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
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6ca8018b572671f349c058e314b26f7897e421b9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727632"
---
# <a name="how-to-choose-collection-methods"></a>Postupy: Výběr metod kolekcí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástrojů pro profilaci sady podporují tři metody shromažďování dat výkonu: vzorkování, instrumentace a souběžnosti. Metoda vzorkování nebo instrumentace můžete také použít ke shromažďování dat o přidělování a životnosti paměti .NET.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Můžete použít relaci výkonu **metoda** vlastnosti a určit nejvhodnější metodu kolekce pro vaši aplikaci. Můžete nastavit metodu kolekce z Průvodce výkonem, prohlížeč výkonu, nebo ze stránek vlastností relace výkonu. Pokud používáte nástroje příkazového řádku, naleznete v tématu [profilace z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md) Další informace.  
  
## <a name="performance-wizard"></a>Průvodce výkonu  
  
#### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Výběr metody kolekce, pomocí průvodcem výkonu  
  
-   Na první stránce průvodce vyberte jednu z následujících možností:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Vzorkování procesoru**|Shromažďuje statistiky aplikace, které jsou užitečné pro počáteční analýzu a analyzovat problémy s využitím procesoru.|  
|**Instrumentace**|Shromažďuje podrobných dat časování, které jsou užitečné pro přesně zacílenou analýzu a analyzovat problémy s výkonem vstupu a výstupu.|  
|**Přidělení paměti .NET**|Shromažďuje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] data o přidělování paměti pomocí metoda profilování vzorkování.|  
|**Souběžnost**|Shromažďuje data kolize prostředků číselná.|  
  
## <a name="performance-explorer"></a>Prohlížeč výkonu  
  
#### <a name="to-select-a-collection-method-using-performance-explorer"></a>Chcete-li vybrat metodu kolekce pomocí Průzkumníku výkonu  
  
1.  Na **prohlížeč výkonu** nástrojů, klepněte na šipku vedle položky **metoda** rozevíracího seznamu.  
  
2.  Klikněte na metodu kolekce, který preferujete.  
  
## <a name="performance-session-property-pages"></a>Stránky vlastností relace výkonu  
  
#### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Chcete-li vybrat vzorkování nebo instrumentace metodu pomocí vlastnosti výkonnostní relace  
  
1.  V **prohlížeč výkonu**, vyberte relaci výkonu.  
  
     Název souboru relace výkonu má .psess rozšíření.  
  
2.  Klikněte pravým tlačítkem na relaci výkonu a pak klikněte na tlačítko **vlastnosti**.  
  
3.  V **stránky vlastností**, klikněte na tlačítko **Obecné**.  
  
4.  Klikněte na metodu kolekce, který preferujete.  
  
    -   Informace o možnostech, které jsou k dispozici při shromažďování dat vzorkování, naleznete v tématu [shromažďování statistik výkonu pomocí pomocí odběru vzorků](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
    -   Informace o možnostech, které jsou k dispozici při shromažďování dat vzorkování, naleznete v tématu [shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).  
  
#### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Chcete-li vybrat shromažďování dat paměti .NET pomocí vlastnosti výkonnostní relace  
  
1.  V **prohlížeč výkonu**, vyberte relaci výkonu.  
  
     Název souboru relace výkonu má .psess rozšíření.  
  
2.  Klikněte pravým tlačítkem na relaci výkonu a pak klikněte na tlačítko **vlastnosti**.  
  
3.  V **stránky vlastností**, klikněte na tlačítko **Obecné**.  
  
4.  Klikněte na tlačítko **vzorkování** nebo **instrumentace**.  
  
5.  Klikněte na tlačítko **.NET shromažďovat informace o přidělení objektu** shromažďovat velikosti a počtu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] přidělení objektu.  
  
6.  (Volitelné) Klikněte na tlačítko **také shromažďovat informace o životnosti objektů .NET** ke shromažďování dat o generace uvolňování paměti kolekce, ve kterých byl regenerované paměti objektu.  
  
     Informace o možnostech, které jsou k dispozici při shromažďování dat paměti .NET najdete v tématu [shromažďuje alokaci paměti .NET a Data o životním cyklu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).  
  
#### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Chcete-li vybrat shromažďování dat souběžnosti pomocí vlastnosti výkonnostní relace  
  
1.  V **prohlížeč výkonu**, klikněte pravým tlačítkem na relaci výkonu a pak klikněte na tlačítko **vlastnosti**.  
  
2.  V **stránky vlastností**, klikněte na tlačítko **Obecné**.  
  
3.  Klikněte na tlačítko **souběžnosti**.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)   
 [Porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)   
 [Vlastnosti výkonnostní relace](../profiling/performance-session-properties.md)



