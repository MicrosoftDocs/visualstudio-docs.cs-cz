---
title: 'Chyba: pracovní proces webu byl ukončen službou IIS | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d61f124d906137557b17b81122eba34e471a1a4
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85459997"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Chyba: Pracovní proces webu byl ukončen službou IIS.
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
- [Chyby a řešení potíží se vzdáleným laděním](../debugger/remote-debugging-errors-and-troubleshooting.md)