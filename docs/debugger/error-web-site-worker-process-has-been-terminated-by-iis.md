---
title: Pracovní proces webu byl ukončen službou IIS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cf7832d71ab86c6dab973a07dbc46217274cb83b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870893"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Chyba: Pracovní proces webu byl ukončen službou IIS.
Ladicí program zastavil provádění kódu na webu. To způsobilo Internetová informační služba (IIS), aby se předpokládalo, že pracovní proces přestal reagovat. Proto služba IIS ukončila pracovní proces.

 Chcete-li pokračovat v ladění, je nutné nakonfigurovat službu IIS tak, aby bylo možné pokračovat v pracovním procesu. Tato chybová zpráva se nezobrazí s verzemi služby IIS, které jsou starší než služba IIS 7.

### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Konfigurace IIS 7, aby bylo možné pokračovat v pracovním procesu

1. Otevřete okno **Nástroje pro správu** .

   1. Klikněte na tlačítko **Start** a poté na příkaz **Ovládací panely**.

   2. V **Ovládacích panelech** zvolte **přepínač přepnout do klasického zobrazení**, v případě potřeby a dvakrát klikněte na položku **Nástroje pro správu**.

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
- [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)