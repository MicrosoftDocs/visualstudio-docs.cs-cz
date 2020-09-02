---
title: 'Postupy: vyloučení nebo zahrnutí krátkých funkcí z instrumentace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8bb49e650f2395bac8a3b5eb1d0f52e2e168731
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146108"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Postupy: Vyloučení funkce CShort z instrumentace nebo je zahrnout do instrumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve výchozím nastavení nástroje pro profilování vyloučí *malé funkce* z instrumentace. Malé funkce jsou krátké funkce, které nedělají žádná volání funkcí. Vyloučení těchto malých funkcí přináší méně režijních nákladů na instrumentaci, a proto zlepšuje rychlost instrumentace. Vyloučení malých funkcí také snižuje velikost souboru dat profilování výkonu (. vsp) a čas potřebný k analýze. Pokud jsou vyloučeny malé funkce, čas strávený v malých funkcích se počítá s výhradním a úplným časem jejich nadřazených funkcí. Malé funkce se dají vyloučit nebo zahrnout do instrumentace, jak je popsáno v následujícím postupu.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Vyloučení nebo zahrnutí krátkých funkcí z instrumentace  
  
1. V **prohlížeč výkonu**vyberte možnost **relace výkonu** , klikněte pravým tlačítkem myši a vyberte možnost **vlastnosti**.  
  
     Zobrazí se dialogové okno **Stránky vlastností**.  
  
2. Na **stránkách vlastností**klikněte na vlastnosti **instrumentace** .  
  
3. Pokud chcete vyloučit krátké funkce z instrumentace, vyberte **vyloučit krátké funkce z instrumentace**. Toto je výchozí nastavení.  
  
     -nebo-  
  
     Pokud chcete do instrumentace zahrnout krátké funkce, zrušte zaškrtnutí políčka **vyloučit krátké funkce z instrumentace**.  
  
4. Klikněte na **OK**.  
  
## <a name="see-also"></a>Viz také  
 [Řízení shromažďování dat](../profiling/controlling-data-collection.md)   
 [Vlastnosti výkonnostní relace](../profiling/performance-session-properties.md)
