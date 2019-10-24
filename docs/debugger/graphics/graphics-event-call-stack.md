---
title: Zásobník volání událostí grafiky | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c221a572264bf6a6aaed9edbec66fb3c0c3ff4b9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735504"
---
# <a name="graphics-event-call-stack"></a>Zásobník volání událostí grafiky
Zásobník volání událostí grafiky v Analyzátor grafiky sady Visual Studio pomáhá mapovat vztah mezi problematickými událostmi grafiky a zdrojovým kódem vaší aplikace.

 Toto je okno zásobníku volání událostí:

 ![Zásobník volání předcházející události DrawIndexed](media/gfx_diag_demo_graphics_event_call_stack_orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")

## <a name="understanding-the-graphics-event-call-stack"></a>Porozumění zásobníku volání událostí grafiky
 Pomocí zásobníku volání událostí můžete pochopit tok provádění, který vedlo k určité události Direct3D. Se podobá oknu zásobníku volání sady Visual Studio, s tím rozdílem, že místo zobrazení aktuálního zásobníku volání aktuálního vlákna ve spuštěné aplikaci zobrazuje zásobník volání, který existoval, když dojde k vybrané události Direct3D. Ze zásobníku volání události můžete přejít na web volání vybrané události Direct3D a prozkoumat okolní kód.

 Pomocí zásobníku volání událostí k identifikaci cesty kódu, ze které vznikla událost problému, můžete použít vaše znalosti základu kódu k odvození potenciálních zdrojů problému nebo můžete přidat zarážky ve zdrojovém kódu vaší aplikace, abyste mohli použít tradiční techniky ladění pro kontrolu toho, jak stav aplikace nebo parametrů události způsobuje, že se událost nechová. Toto prověřování vám může pomáhat najít problémy ve zdrojovém kódu, které se projevují pouze jako problémy vykreslování.

### <a name="graphics-event-call-stack-information"></a>Informace o zásobníku volání událostí grafiky
 Zásobník volání události nepodporuje události předcházejících rámců ani uživatelsky definované události. Zásobník volání událostí grafiky se zobrazí ve formátu tabulky.

|Kolo|Popis|
|------------|-----------------|
|**Jméno**|Symbol, který jedinečně identifikuje funkci obsahující web volání. Symbol ladění pro funkci je zobrazen, pokud je k dispozici; v opačném případě se zobrazí posun funkce.|
|**Souborů**|Název souboru zdrojového kódu nebo souboru knihovny, který obsahuje web volání.|
|**Poloha**|Číslo řádku webu volání.|

### <a name="links-to-graphics-objects"></a>Odkazy na grafické objekty
 Pro pochopení vybrané události grafiky můžete potřebovat informace o objektech Direct3D, které jsou k němu přidruženy. Odkazy na tyto informace jsou uvedeny v okně **zásobník volání událostí grafiky** .

## <a name="see-also"></a>Viz také:
- [Návod: Chybějící objekty z důvodu použití funkce vertex shading](walkthrough-missing-objects-due-to-vertex-shading.md)