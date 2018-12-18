---
title: Dokumentu protokolu grafiky | Dokumentace Microsoftu
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
- vs.graphics.vsglog.error
- vs.graphics.experiment
- vs.graphics.vsglog
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 097f431446ed2148e2a61c6f85266843fe7ada44
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745173"
---
# <a name="graphics-log-document"></a>Dokument grafických protokolů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dokumentu protokol grafiky je záznam událostí grafiky, ke kterým došlo, když byla aplikace spuštěna v rámci relace diagnostiky grafiky. Po zapsání můžete prozkoumat v protokolu ve Visual Studio Graphics Analyzer k diagnostice problémů vykreslování a výkonu.  
  
 Toto je co dokument grafických protokolů vypadá podobně jako v analyzátoru grafiky:  
  
 ![Protokol grafiky obsahuje dva zachycené snímky. ](../debugger/media/gfx-diag-demo-graphics-log-orientation.png "gfx_diag_demo_graphics_log_orientation")  
  
## <a name="understanding-graphics-log-documents"></a>Vysvětlení grafiky protokolu dokumenty  
 Pomocí analyzátoru grafiky sady k prozkoumání dokument grafických protokolů můžete sledovat účinky událostmi rozhraní Direct3D na cíl vykreslování, ke které došlo při zachytávání. Můžete určit oblasti cíle vykreslování, které obsahují neočekávaný výstup. Když vyberte pixel v ovlivněné oblasti, můžete ke kontrole, jeho shadery, události rozhraní Direct3D, které měla vliv na to, zásobník volání aplikace, která vedla k těmto událostem a objekty rozhraní DirectX, které podporují tyto události modulu Diagnostika grafiky. Tyto informace můžete použít k diagnostice problémů vykreslování ve hře nebo aplikaci.  
  
 Horní část okna (**grafiky Experiment.vsglog**) zobrazí aktuální výstup cíle vykreslení vybraného snímku a v dolní části zobrazují **seznam snímků** obsahující obrázky miniatur zachycené snímky.  
  
#### <a name="to-inspect-a-frame"></a>Chcete-li prověřit blok  
  
-   V **seznam snímků**, vyberte snímek, který chcete zkontrolovat. Výstup cíle vykreslení v horní části dokumentu protokol grafiky se aktualizuje a zobrazí vybraný rámec.  
  
#### <a name="to-inspect-a-pixel"></a>Chcete-li prověřit pixel  
  
-   V horní části dokumentu protokol grafiky vyberte pixel, který chcete výstup cíle vykreslení. Když je vybraný pixel, můžete **historie pixelů grafiky** okno k zobrazení podrobných informací o vybraný pixel. Další informace najdete v tématu [historie pixelů](../debugger/graphics-pixel-history.md).  
  
## <a name="playback-machine"></a>Počítač pro přehrávání  
 Zobrazí také v pravém horním rohu **seznam snímků** je **počítač pro přehrávání**. Počítač pro přehrávání je počítač nebo zařízení, které slouží k přehrání událostí grafiky z grafického protokolu souboru během novější relace diagnostiky grafiky. Pomocí jiného zařízení místo svého vývojového počítače k přehrání zachycené události může přesněji reprodukovat spouštěcí prostředí, ve kterém dochází k problému – například můžete použít počítač, který má jiný grafický hardware nebo ovladače než ty, které používá vývojovém počítači, nebo jiných typů zařízení, například tablety Windows RT založené na ARM nebo zařízení Windows Phone.  
  
 Informace o tom, jak určit počítač pro přehrávání, naleznete v tématu [postupy: Změna počítače pro přehrávání diagnostiky grafiky](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="graphics-log-summary-information"></a>Souhrnné informace protokolu grafiky  
 Když soubor protokolu grafiky je aktivní dokument **vlastnosti** okno zobrazuje informace o prostředí, jehož hostitelem relace zachycení diagnostiky grafiky. Zobrazí se několik kategorií informací.  
  
 **Informace o rozhraní Direct3D**  
 Obsahuje informace o funkcí hardwaru a ovladače grafického adaptéru, který se používá během relace zachytávání.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Formát High Color 10-bit XR**|**Hodnota TRUE** Pokud 10-bit XR high color formát je podporovaná; v opačném případě **False**.|  
|**DirectCompute CS 4.x**|**Hodnota TRUE** Pokud výpočetní Shader 4.0 je podporovaná; v opačném případě **False**.|  
|**Shadery dvojnásobné přesnosti**|**Hodnota TRUE** Pokud grafický adaptér podporuje dvojité přesnosti s plovoucí desetinnou čárkou hodnoty (64 bitů); v opačném případě **False**.|  
|**Seznamy příkazů ovladače**|**Hodnota TRUE** Jestliže ovladač podporuje seznamy příkazů; v opačném případě **False**.|  
|**Souběžné produkty ovladače**|**Hodnota TRUE** Jestliže ovladač podporuje souběžné vytvoření (asynchronní); v opačném případě **False**.|  
|**Rozšířené formáty (BGRA atd.)**|**Hodnota TRUE** Pokud rozšířené formátech, jako jsou BGRA jsou podporované; v opačném případě **False**.|  
|**Úroveň hardwarové výbavy Max**|Zobrazí nejvyšší úroveň funkce, který podporuje grafický adaptér.|  
  
 **Zobrazení informací**  
 Obsahuje informace o grafický adaptér, který se používá během relace zachytávání.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Popis**|Zobrazovaný řetězec popis adaptéru.|  
|**Zobrazení paměti**|Velikost paměti, která je nainstalovaná na grafický adaptér.|  
|**Název ovladače**|Název ovladače grafického adaptéru.|  
|**Verze ovladače**|Verze ovladače grafického adaptéru.|  
|**Jméno**|Název grafického adaptéru.|  
  
 **Soubor experimentu**  
 Obsahuje informace o souboru experiment, který je spojen s relace zachytávání.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Cesta**|Cestu k souboru .vsglog. **Poznámka:** pod starší verze zachycení, tato vlastnost se nepoužívá.|  
  
 **Informace o modulu**  
 Zobrazuje název a verze dynamické knihovny (DLL), která byla načtena aplikace během relace zachycení.  
  
 **Systémové informace**  
 Obsahuje informace o hardwaru a operačního systému, který je hostitelem aplikace během relace zachycení.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Paměť**|Množství paměti, která je nainstalována v počítači.|  
|**Architektura operačního systému**|Cílové architektury procesoru operačního systému.|  
|**Verze operačního systému**|Verze operačního systému.|  
|**Procesor**|Procesor, který je nainstalován v počítači.|  
|**Architektura cílové aplikace**|Cílové architektuře procesoru v aplikaci. To může být jiné než **Architektura operačního systému**.|  
  
 **Cílové aplikace**  
 Obsahuje informace o aplikaci, která je předmětem relace zachytávání.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Datum/čas poslední změny**|Datum a čas, kterou byla aplikace vytvořena.|  
|**Cesta**|Cesta aplikace.|  
|**ID procesu**|ID procesu, který byl zadán pro aplikaci.|  
|**Verze**|Verze aplikace.|  
  
 **Soubor protokolu VSG**  
 Obsahuje informace o dokumentu protokol grafiky.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Vytvořil**|Název aplikace, kterou vytvořili grafiky protokolu dokumentu. Například, pokud byla relace zachytávání iniciovaná [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (ruční capture) hodnota této vlastnosti je [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|**Čas spuštění relace**|Datum a čas zahájení relace zachytávání.|  
|**Velikost**|Velikost dokument grafických protokolů.|  
  
## <a name="see-also"></a>Viz také  
 [Návod: Chybějící objekty z důvodu použití funkce Vertex Shading](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Návod: Ladění chyb při vykreslování způsobených stínováním](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)



