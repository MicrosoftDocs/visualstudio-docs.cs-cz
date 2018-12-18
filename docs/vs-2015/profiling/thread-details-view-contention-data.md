---
title: Podrobnosti zobrazení vláknu – Data kolizí | Dokumentace Microsoftu
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
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da2cac3503f97976fe5c0918f86e5b25f2b89329
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795648"
---
# <a name="thread-details-view---contention-data"></a>Zobrazení podrobností o vláknu – data kolizí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení podrobností vláken představuje graf časové osy blokujících událostí ve vybrané vláknu spuštění profilování, které byly způsobeny kolizí nad prostředky. Blokování události dojde, když vlákno je nucen k pozastavení provádění, protože jiné vlákno má uzamčený přístup k prostředku.  
  
 Toto zobrazení představuje na časové ose provádění vlákna jako vodorovný pruh a blokujících událostí jako svislý pruh na vodorovné ose pro vlákno. V případě potřeby můžete přiblížit na části časové osy a zobrazte jednotlivé události. Chcete-li zobrazit postupu provádění funkcí, které vedly k události, klikněte na panelu události. Funkce se zobrazí v okně zásobník volání. Pokud zdrojový kód funkce je k dispozici, můžete kliknout na její název upravit zdrojový soubor v integrovaném vývojovém prostředí sady Visual Studio.  
  
## <a name="navigating-the-timeline"></a>Procházení na časové ose  
  
#### <a name="to-zoom-in-on-a-timeline-segment"></a>Přiblížit na segment časové osy  
  
-   Klikněte a tažením ukazatele myši a vyberte oblast na časové ose.  
  
     Když uvolníte tlačítko myši, přiblížení zobrazení vybraného časového úseku. Postup přiblížení podrobněji, můžete opakovat. Posuvníku na posuvníku čas představuje relativní velikost časového úseku, který se zobrazí v zobrazení.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>Chcete-li oddálení časové osy  
  
-   Klikněte na tlačítko **Oddálit** se vraťte na předchozí úroveň přiblížení.  
  
-   Klikněte na tlačítko **přiblížení resetování** zobrazíte celý časové osy v zobrazení.  
  
#### <a name="to-view-the-call-stack-of-an-event"></a>Chcete-li zobrazit zásobník volání události  
  
-   Časová osa grafu klikněte na svislý pruh, který představuje událost...  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Chcete-li zobrazit nebo upravit zdrojový kód funkce v zásobníku volání  
  
- V okně zásobník volání klikněte na název funkce.  
  
  Zdrojový kód funkce musí být součástí aktuálního projektu.  
  
#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>Chcete-li zobrazit kolizní události z prostředku ve všech vláknech při spuštění profilace  
  
-   Časová osa grafu klikněte na název nebo id prostředku.  
  
     [Zobrazení podrobností o prostředku](../profiling/resource-details-view-contention-data.md) se zobrazí pro vybraný prostředek.  
  
#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>Chcete-li zobrazit data kolize vlákna v okně procesy  
  
-   Časová osa grafu, klikněte na tlačítko **celkový**.  
  
     [Zobrazení procesu](../profiling/process-view-contention-data.md) se zobrazí s vláknem vybrali.



