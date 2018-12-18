---
title: Zásobník volání událostí grafiky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77c53db002fd0d300a01b5cc142f6ed2daf4daa2
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510575"
---
# <a name="graphics-event-call-stack"></a>Zásobník volání událostí grafiky
Zásobníku volání události grafiky v analyzátoru grafiky sady Visual Studio umožňuje mapovat vztah mezi událostí grafiky problematické a zdrojový kód vaší aplikace.  
  
 Toto je v okně zásobník volání události:  
  
 ![Před událostí DrawIndexed zásobníku volání. ](media/gfx_diag_demo_graphics_event_call_stack_orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")  
  
## <a name="understanding-the-graphics-event-call-stack"></a>Principy zásobník volání událostí grafiky  
 Zásobník volání událostí můžete použít k pochopení toku provádění, která vedla k určité události rozhraní Direct3D. Vypadá podobně jako okno zásobníku volání sady Visual Studio, s tím rozdílem, že místo aktuální zásobník volání aktuálního vlákna ve spuštěné aplikaci, se zobrazí zásobník volání podle existovala, když došlo k vybrané události rozhraní Direct3D. Z zásobník volání událostí můžete přejít na lokalitu volání vybrané události rozhraní Direct3D ke kontrole okolním kódem.  
  
 Pomocí zásobník volání událostí k identifikaci do cesty kódu, ze kterého pochází událost problému svoje znalosti v oblasti základu kódu můžete použít k odvození potenciálních zdrojů problému nebo přidat zarážky ve zdrojovém kódu vaší aplikace tak, aby vám tradiční techniky pro zjištění, jak stav parametry aplikace nebo události způsobují událost, abyste misbehave ladění. Při této kontrole můžete najít problémy ve zdrojovém kódu, které jsou pouze označované jako problémů s vykreslováním.  
  
### <a name="graphics-event-call-stack-information"></a>Informace o zásobník volání událostí grafiky  
 Zásobník volání událostí nepodporuje události předběžné snímků nebo uživatelem definované události. Zásobník volání událostí grafiky se zobrazí ve formátu tabulky.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Symbol, který jednoznačně identifikuje funkce, která obsahuje lokalitu volání. Symbol ladění pro funkce se zobrazí, když je k dispozici. v opačném případě se zobrazí funkce Posun.|  
|**Soubor**|Název souboru souboru se zdrojovým kódem nebo soubor knihovny, která obsahuje lokalitu volání.|  
|**Poloha**|Číslo řádku lokalitu volání.|  
  
### <a name="links-to-graphics-objects"></a>Odkazy na grafických objektů  
 Porozumění události vybrané grafiky, budete pravděpodobně potřebovat informace o Direct3D objekty, které jsou k ní přidružena. **Zásobník volání událostí grafiky** okno obsahuje odkazy na tyto informace.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Chybějící objekty z důvodu použití funkce vertex shading](walkthrough-missing-objects-due-to-vertex-shading.md)