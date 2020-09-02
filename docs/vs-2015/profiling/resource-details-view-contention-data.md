---
title: Zobrazení podrobností o prostředku – data kolizí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 922edcd45dd42c8da5a9ec4dc8d3e8f450ceea09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67823602"
---
# <a name="resource-details-view---contention-data"></a>Zobrazení podrobností o prostředku – data kolizí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení Podrobnosti o prostředku představuje graf časové osy blokujících událostí, které byly způsobeny kolizí přes vybraný prostředek. K blokující události dojde, když je vlákno nuceno pozastavit provádění, protože jiné vlákno má zamčený přístup k prostředku.  
  
 Toto zobrazení představuje časovou osu spuštění každého vlákna jako vodorovný pruh a představuje každou blokující událost jako svislou čáru na časové ose vlákna. V případě potřeby můžete zvětšit část časové osy a zobrazit jednotlivé události. Chcete-li zobrazit cestu spuštění (zásobník volání) funkcí, které vedly k události, klikněte na panel událostí. Funkce se zobrazí v okně **zásobník volání** . Pokud je zdrojový kód funkce k dispozici, můžete kliknout na název funkce a upravit zdrojový soubor v rozhraní pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-magnify-a-timeline-segment"></a>Zvětšení segmentu časové osy  
  
- Přetáhněte ukazatel myši na oblast časové osy.  
  
     Po uvolnění tlačítka myši se zobrazení zvětší na vybraný časový segment. Můžete opakovat proces pro další zvětšení segmentu. Posunutí posuvníku na posuvníku času představuje relativní velikost časového segmentu, který se zobrazí v zobrazení.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>Přiblížení na časovou osu  
  
- Proveďte jeden z následujících kroků:  
  
  - Kliknutím na **oddálit** se vrátíte k předchozí úrovni přiblížení.  

  - Klikněte na tlačítko **obnovit nastavení** , aby se zobrazila veškerá časová osa v zobrazení.  

#### <a name="to-view-the-call-stack-of-an-event"></a>Zobrazení zásobníku volání události  
  
- V grafu časové osy klikněte na panel událostí.  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Zobrazení nebo úpravy zdrojového kódu funkce v zásobníku volání  
  
- V okně **zásobník volání** klikněte na název funkce.  
  
  Zdrojový kód funkce musí být součástí aktuálního projektu.  
  
#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Zobrazení stromu volání událostí sporu pro prostředek  
  
- V grafu časové osy klikněte na **celkem**.  
  
     Pro prostředek se zobrazí zobrazení sporů. Další informace najdete v tématu [zobrazení sporů prostředků.](../profiling/resource-contentions-view-contention-data.md)  
  
#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Zobrazení všech událostí sporu vlákna  
  
- V grafu časové osy klikněte na název nebo ID vlákna.  
  
     Zobrazí se zobrazení podrobností o vlákně pro vybrané vlákno. Další informace naleznete v tématu [zobrazení podrobností o vláknech](../profiling/thread-details-view-contention-data.md).
