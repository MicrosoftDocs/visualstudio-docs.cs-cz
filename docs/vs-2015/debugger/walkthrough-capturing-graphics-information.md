---
title: 'Návod: Zaznamenání grafických informací | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2f419e80cec27807ba3bd7ac98f7fb7108a49377
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802132"
---
# <a name="walkthrough-capturing-graphics-information"></a>Návod: Zaznamenání grafických informací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak používat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] diagnostiky grafiky k ručně zachytit informace grafiky z aplikace Direct3D.  
  
 Tento návod ilustruje tyto úkoly:  
  
-   Zachycení diagnostiky grafiky do vaší aplikace  
  
-   Zachycení informací grafiky  
  
## <a name="capturing-graphics-information"></a>Zachycení informací grafiky  
 Použití nástrojů diagnostiky grafiky, je nejprve nutné zachytit informace grafiky, která ho využívá. K povolení funkce capture, použijte **spustit diagnostiku** příkaz, který připojí nástroj Diagnostika grafiky do vaší aplikace při spuštění.  
  
#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Chcete-li povolit zachycení informací grafiky po projekt nebo řešení je načteno  
  
1.  V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], načtení souboru projektu nebo řešení pro aplikaci, kterou chcete zachytit informace grafiky z.  
  
2.  Na panelu nástrojů diagnostiky grafiky **spustit diagnostiku**.  
  
#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Chcete-li povolit zachycení informací grafiky bez načítání projektu nebo řešení  
  
1. V panelu nabídky zvolte **souboru**, **otevřít**, **projekt či řešení**. **Otevřít projekt** zobrazí se dialogové okno.  
  
2. Místo souboru projektu nebo řešení, zadejte spustitelný soubor pro aplikaci, kterou chcete zachytit informace grafiky z a klikněte na tlačítko **otevřít**.  
  
3. V panelu nabídky zvolte **ladění**, **grafiky**, **spustit diagnostiku**.  
  
   Po spuštění aplikace a je vykreslování rámce, může zachytit grafické informace.  
  
#### <a name="to-capture-graphics-information"></a>Chcete-li zachytit informace grafiky  
  
- Na panelu nástrojů diagnostiky grafiky **zachycení** tlačítko. ![Zachytávání grafiky ikonu tlačítka](../debugger/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
   -nebo-  
  
   S aplikací fokus, stiskněte klávesu **Print Screen**.  
  
  Pokaždé, když zaznamenat informace o snímek, diagnostiky grafiky zaznamenává události rozhraní Direct3D a přidružený stav a přidá tato data do protokolu grafiky. Pro každou relaci diagnostiky grafiky je vytvořen nový protokol grafiky. Informace o protokoly grafiky, naleznete v tématu [přehled](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="next-steps"></a>Další kroky  
 Tento názorný postup ukázal, jak lze zachytit informace grafiky ručně. V dalším kroku vezměte v úvahu tuto možnost:  
  
-   Zjistěte, jak analyzovat zachycené informace grafiky pomocí nástrojů diagnostiky grafiky. Zobrazit [přehled](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Viz také  
 [Zaznamenání grafických informací](../debugger/capturing-graphics-information.md)



