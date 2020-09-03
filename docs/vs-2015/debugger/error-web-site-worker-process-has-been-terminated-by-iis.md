---
title: 'Chyba: pracovní proces webu byl ukončen službou IIS | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5707b972-71a6-4cc6-ab99-c7c00ca8628c
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 787785909cd980176fd9220f58198ae6cc272ea8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185467"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Chyba: Pracovní proces webu byl ukončen službou IIS.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladicí program zastavil provádění kódu na webu. To způsobilo Internetová informační služba (IIS), aby se předpokládalo, že pracovní proces přestal reagovat. Proto služba IIS ukončila pracovní proces.  
  
 Chcete-li pokračovat v ladění, je nutné nakonfigurovat službu IIS tak, aby bylo možné pokračovat v pracovním procesu. Tato chybová zpráva se nezobrazí s verzemi služby IIS, které jsou starší než služba IIS 7.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Konfigurace IIS 7, aby bylo možné pokračovat v pracovním procesu  
  
1. Otevřete okno **Nástroje pro správu** .  
  
   1. Klikněte na tlačítko **Start**a poté na příkaz **Ovládací panely**.  
  
   2. V **Ovládacích panelech**zvolte **přepínač přepnout do klasického zobrazení**, v případě potřeby a dvakrát klikněte na položku **Nástroje pro správu**.  
  
2. V okně **Nástroje pro správu** poklikejte na **Správce služby Internetová informační služba (IIS)**.  
  
    Spustí se správce služby IIS.  
  
3. V podokně **připojení** rozbalte \<computer name> uzel v případě potřeby.  
  
4. V \<computer name> uzlu klikněte na **fondy aplikací**.  
  
5. V seznamu **fondy aplikací** klikněte pravým tlačítkem na název fondu, ve kterém je aplikace spuštěná, a pak klikněte na **Upřesnit nastavení**.  
  
6. V dialogovém okně **Upřesnit nastavení** vyhledejte část **model procesu** a proveďte jednu z následujících akcí:  
  
   - Nastavte možnost **pøíkazového testu** na **hodnotu NEPRAVDA**.  
  
   - Nastavte **maximální dobu odezvy nástroje test** na hodnotu, která je větší než 90 sekund.  
  
     Nastavení možnosti **Povolit test** na **hodnotu false** zastaví službu IIS, aby zkontrolovala, jestli je stále spuštěný pracovní proces, a udržuje pracovní proces aktivní, dokud nezastavíte proces ladění. Nastavení **maximální doby odezvy** nástroje pro odeslání na velkou hodnotu umožní službě IIS pokračovat v monitorování pracovního procesu.  
  
7. Kliknutím na tlačítko **OK** zavřete dialogové okno **Upřesnit nastavení** .  
  
8. Zavřete Správce služby IIS a okno **Nástroje pro správu** .  
  
## <a name="see-also"></a>Viz také  
 [Chyby a řešení potíží se vzdáleným laděním](../debugger/remote-debugging-errors-and-troubleshooting.md)
