---
title: Dokument protokolu grafiky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.vsglog.error
- vs.graphics.experiment
- vs.graphics.vsglog
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 430c321c14226228b46bfb0e43f372851fb2a232
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161245"
---
# <a name="graphics-log-document"></a>Dokument grafických protokolů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dokument protokolu grafiky je záznam událostí grafiky, ke kterým došlo v době, kdy byla aplikace spuštěna v relaci diagnostiky grafiky. Po nahrání můžete prostudovat Analyzátor grafiky sady Visual Studio přihlášení a diagnostikovat problémy s vykreslováním a výkonem.  
  
 To je to, co vypadá v analyzátoru grafiky v podobě dokumentu protokolu grafiky:  
  
 ![Protokol grafiky obsahující dva zachycené snímky.](../debugger/media/gfx-diag-demo-graphics-log-orientation.png "gfx_diag_demo_graphics_log_orientation")  
  
## <a name="understanding-graphics-log-documents"></a>Porozumění dokumentům s protokolem grafiky  
 Pomocí analyzátoru grafiky pro prohlížení dokumentu s grafickým protokolem můžete vizualizovat účinky událostí Direct3D na cíl vykreslování, ke kterému došlo během zachytávání. Můžete určit oblasti cíle vykreslování, které obsahují Neočekávaný výstup. Když vyberete pixel v ovlivněné oblasti, můžete k jeho kontrole použít Diagnostika grafiky, jeho shadery, události Direct3D, které to ovlivnilo, zásobník volání aplikace, který vedl k těmto událostem, a objekty rozhraní DirectX, které tyto události podporují. Tyto informace můžete použít k diagnostice problémů s vykreslováním ve vaší hře nebo aplikaci.  
  
 Horní část okna (**Graphics experiment. vsglog**) zobrazí aktuální výstup cíle vykreslování vybraného rámce a dolní část zobrazí **seznam rámců** , který obsahuje miniatury zachycených snímků.  
  
#### <a name="to-inspect-a-frame"></a>Kontrola rámce  
  
- V **seznamu snímků**vyberte rámec, který chcete zkontrolovat. Výstup cíle vykreslování v horní části dokumentu protokolu grafiky je aktualizován tak, aby zobrazoval vybraný snímek.  
  
#### <a name="to-inspect-a-pixel"></a>Kontrola pixelu  
  
- V horní části dokumentu protokolu grafiky vyberte pixel, který chcete z výstupu cíle vykreslování. Když vyberete pixel, můžete použít okno **Historie pixelů grafiky** k zobrazení podrobných informací o vybraném pixelu. Další informace najdete v tématu [Historie pixelů](../debugger/graphics-pixel-history.md).  
  
## <a name="playback-machine"></a>Počítač pro přehrávání  
 Zobrazuje se také v pravém horním rohu **seznamu rámců** , který je **počítač pro přehrávání**. Počítač pro přehrávání je počítač nebo zařízení, které se používá k přehrávání grafických událostí ze souboru protokolu grafiky během pozdější relace diagnostiky grafiky. Když místo vývojového počítače použijete jiné zařízení k přehrání zachycených událostí, můžete přesnější reprodukci spouštěcího prostředí, ve kterém dochází k problému, například použít počítač, který má jiný grafický hardware nebo ovladače než ty, které váš vývojový počítač používá, nebo jiné druhy zařízení, jako je například tablet s Windows RT nebo zařízení Windows Phone s procesorem ARM.  
  
 Informace o tom, jak zadat počítač pro přehrávání, najdete v tématu [Postup: změna Diagnostika grafiky počítač pro přehrávání](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="graphics-log-summary-information"></a>Souhrnné informace o protokolu grafiky  
 Když je soubor protokolu grafiky aktivním dokumentem, zobrazí se v okně **vlastnosti** informace o prostředí, které hostuje relaci Diagnostika grafiky Capture. Zobrazí se několik kategorií informací.  
  
 **Informace Direct3D**  
 Zobrazí informace o vlastnostech hardwaru a ovladače grafického adaptéru, který se použil během relace zachycení.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**XR high color Format ve formátu 10 bitů**|**True** , pokud je podporován formát High Color XR s vysokým rozlišením. v opačném případě **false**.|  
|**DirectCompute CS 4. x**|**True** , pokud je podporována funkce compute shader 4,0; v opačném případě **false**.|  
|**Shadery s dvojitou přesností**|**True** , pokud zobrazovací adaptér podporuje hodnoty s plovoucí desetinnou čárkou s dvojitou přesností (64 bitů); v opačném případě **false**.|  
|**Seznamy příkazů ovladače**|**True** , pokud ovladač podporuje seznamy příkazů; v opačném případě **false**.|  
|**Souběžné vytváření ovladačů**|**True** , pokud ovladač podporuje souběžné (asynchronní) vytváření; v opačném případě **false**.|  
|**Rozšířené formáty (BGRA atd.)**|**True** , pokud jsou podporovány rozšířené formáty jako BGRA; v opačném případě **false**.|  
|**Maximální úroveň hardwarové funkce**|Zobrazuje nejvyšší úroveň funkce, kterou adaptér zobrazení podporuje.|  
  
 **Zobrazit informace**  
 Zobrazí informace o zobrazovacím adaptéru, který se použil během relace zachycení.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Popis**|Řetězec popisu zobrazovaného adaptéru|  
|**Zobrazit paměť**|Velikost paměti, která je nainstalovaná na grafickém adaptéru.|  
|**Driver Name**|Název ovladače grafického adaptéru.|  
|**Verze ovladače**|Verze ovladače grafického adaptéru.|  
|**Name**|Název grafického adaptéru.|  
  
 **Experimentovat soubor**  
 Obsahuje seznam informací o souboru experimentu, který je přidružen k relaci zachycení.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Cesta**|Cesta k souboru. vsglog **Poznámka:**  V části starší zachytávání se tato vlastnost nepoužívá.|  
  
 **Informace o modulu**  
 Zobrazuje název a verzi knihoven DLL, které aplikace zavedly během relace zachycení.  
  
 **Systémové informace**  
 Zobrazí informace o hardwaru a operačním systému, který hostuje aplikaci během relace zachycení.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Paměť**|Velikost paměti, která je nainstalována v počítači.|  
|**Architektura operačního systému**|Cílová architektura procesoru operačního systému.|  
|**Verze operačního systému**|Verze operačního systému.|  
|**Procesor**|Procesor, který je nainstalován v počítači.|  
|**Architektura cílové aplikace**|Cílová architektura procesoru aplikace Může se lišit od **architektury operačního systému**.|  
  
 **Cílová aplikace**  
 Zobrazí informace o aplikaci, která je předmětem relace zachycení.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Datum a čas poslední změny**|Datum a čas, kdy byla aplikace sestavena.|  
|**Cesta**|Cesta k aplikaci|  
|**ID procesu**|ID procesu, které bylo přiděleno aplikaci.|  
|**Verze**|Verze aplikace|  
  
 **Soubor protokolu VSG**  
 Zobrazí informace o dokumentu protokolu grafiky.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Vytvořil(a)**|Název aplikace, která vytvořila dokument protokolu grafiky. Pokud byla například relace zachycení iniciována z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (ruční zachytávání), hodnota této vlastnosti je [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|**Čas spuštění relace**|Datum a čas, kdy začala relace zachycení.|  
|**Velikost**|Velikost dokumentu protokolu grafiky|  
  
## <a name="see-also"></a>Viz také  
 [Návod: chybějící objekty z důvodu stínování vrcholu](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Návod: Ladění chyb vykreslování způsobených stínováním](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)
