---
title: Zobrazení podrobností o vláknu – data kolizí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 16ee86e69cb3a150a98de5077aa0c545545833e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145594"
---
# <a name="thread-details-view---contention-data"></a>Zobrazení podrobností o vláknu – data kolizí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení podrobností o vlákně prezentuje graf časové osy blokujících událostí ve vybraném vláknu procesu profilace, které byly způsobeny kolizími přes prostředky. K blokující události dojde, když je vlákno nuceno pozastavit provádění, protože jiné vlákno má zamčený přístup k prostředku.  
  
 Toto zobrazení představuje časovou osu spuštění vlákna jako vodorovný pruh a blokující události jako svislé pruhy na vodorovné ose pro vlákno. V případě potřeby můžete přiblížit část časové osy a zobrazit jednotlivé události. Chcete-li zobrazit cestu spuštění funkcí, které vedly k události, klikněte na panel událostí. Funkce se zobrazí v okně zásobník volání. Pokud je zdrojový kód funkce k dispozici, můžete kliknout na název funkce a upravit zdrojový soubor v integrovaném vývojovém prostředí sady Visual Studio.  
  
## <a name="navigating-the-timeline"></a>Navigace na časové ose  
  
#### <a name="to-zoom-in-on-a-timeline-segment"></a>Přiblížení segmentu časové osy  
  
- Kliknutím a přetažením ukazatele myši vyberte oblast časové osy.  
  
     Když uvolníte myš, zobrazení se zvětší na vybraný časový segment. Tento postup můžete opakovat a podrobněji tak zvětšit. Posuvník v časovém posuvníku znázorňuje relativní velikost časového segmentu, který je zobrazen v zobrazení.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>Přiblížení na časovou osu  
  
- Kliknutím na **oddálit** se vrátíte k předchozí úrovni přiblížení.  
  
- Kliknutím na tlačítko **obnovit obnovení** zobrazíte celou časovou osu v zobrazení.  
  
#### <a name="to-view-the-call-stack-of-an-event"></a>Zobrazení zásobníku volání události  
  
- V grafu časové osy klikněte na svislou čáru, která představuje událost..  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Zobrazení nebo úpravy zdrojového kódu funkce v zásobníku volání  
  
- V okně zásobník volání klikněte na název funkce.  
  
  Zdrojový kód funkce musí být součástí aktuálního projektu.  
  
#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>Zobrazení událostí kolizí prostředku ve všech vláknech při spuštění profilace  
  
- V grafu časové osy klikněte na název nebo ID prostředku.  
  
     Zobrazí se [zobrazení Podrobnosti o prostředku](../profiling/resource-details-view-contention-data.md) pro vybraný prostředek.  
  
#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>Zobrazení dat kolizí vlákna v okně procesy  
  
- V grafu časové osy klikněte na **celkem**.  
  
     [Zobrazení procesu](../profiling/process-view-contention-data.md) se zobrazí s vybraným vláknem.
