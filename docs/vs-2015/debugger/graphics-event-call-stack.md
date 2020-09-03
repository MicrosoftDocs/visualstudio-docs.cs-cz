---
title: Zásobník volání událostí grafiky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8344050d26286263e0c33974b976e4ae25ff18de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192763"
---
# <a name="graphics-event-call-stack"></a>Zásobník volání událostí grafiky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zásobník volání událostí grafiky v Analyzátor grafiky sady Visual Studio pomáhá mapovat vztah mezi problematickými událostmi grafiky a zdrojovým kódem vaší aplikace.  
  
 Toto je okno zásobníku volání událostí:  
  
 ![Zásobník volání předvolal událost DrawIndexed.](../debugger/media/gfx-diag-demo-graphics-event-call-stack-orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")  
  
## <a name="understanding-the-graphics-event-call-stack"></a>Porozumění zásobníku volání událostí grafiky  
 Pomocí zásobníku volání událostí můžete pochopit tok provádění, který vedlo k určité události Direct3D. Se podobá oknu zásobníku volání sady Visual Studio, s tím rozdílem, že místo zobrazení aktuálního zásobníku volání aktivního vlákna ve spuštěné aplikaci zobrazuje zásobník volání, který existoval, když dojde k vybrané události Direct3D. Ze zásobníku volání události můžete přejít na web volání vybrané události Direct3D a prozkoumat okolní kód.  
  
 Pomocí zásobníku volání událostí k identifikaci cesty kódu, ze které způsobuje událost problému, můžete použít vaše znalosti základu kódu k odvození potenciálních zdrojů problému nebo můžete přidat zarážky ve zdrojovém kódu vaší aplikace, aby bylo možné použít tradiční techniky ladění, abyste prozkoumali, jak stav aplikace nebo parametrů události způsobuje nesprávného chování události. Toto prověřování vám může pomáhat najít problémy ve zdrojovém kódu, které se projevují pouze jako problémy vykreslování.  
  
### <a name="graphics-event-call-stack-information"></a>Informace o zásobníku volání událostí grafiky  
 Zásobník volání události nepodporuje události předcházejících rámců ani uživatelsky definované události. Zásobník volání událostí grafiky se zobrazí ve formátu tabulky.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Name**|Symbol, který jedinečně identifikuje funkci obsahující web volání. Symbol ladění pro funkci je zobrazen, pokud je k dispozici; v opačném případě se zobrazí posun funkce.|  
|**Soubor**|Název souboru zdrojového kódu nebo souboru knihovny, který obsahuje web volání.|  
|**Umístění**|Číslo řádku webu volání.|  
  
### <a name="links-to-graphics-objects"></a>Odkazy na grafické objekty  
 Pro pochopení vybrané události grafiky můžete potřebovat informace o objektech Direct3D, které jsou k němu přidruženy. Odkazy na tyto informace jsou uvedeny v okně **zásobník volání událostí grafiky** .  
  
## <a name="see-also"></a>Viz také  
 [Návod: Chybějící objekty z důvodu použití vertex shaderu](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)
