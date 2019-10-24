---
title: 'Chyba: nemáte oprávnění ke kontrole identity procesů&#39;| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: cad229f80676c3d1f7a7d23ad7a29729c834929b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736225"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Chyba: nemáte oprávnění ke kontrole identity procesů&#39;.
Nemáte oprávnění kontrolovat identitu procesu. Příčinou může být konfigurace vašeho systému.

 Ladicí program nemohl zkontrolovat identitu procesu, což je nezbytné informace pro ladění. Nejpravděpodobnější příčinou je, že služba Terminal Services je zakázána. Služba Terminal Services je ve výchozím nastavení povolená. Pomocí těchto kroků ho znovu povolte.

### <a name="to-enable-terminal-services"></a>Povolení Terminálové služby

1. Klikněte na tlačítko **Start** a poté na příkaz **Ovládací panely**.

2. V Ovládacích panelech zvolte **přepínač přepnout do klasického zobrazení**, v případě potřeby a dvakrát klikněte na položku **Nástroje pro správu**.

3. V okně **Nástroje pro správu** poklikejte na **Správa počítače**.

4. V okně Správa počítače rozbalte uzel **služby a aplikace** .

5. V části **služby a aplikace**klikněte na možnost **služby**.

     V pravém podokně se zobrazí seznam služeb.

6. V seznamu **služby** klikněte pravým tlačítkem na **Terminálová služba** a pak zvolte **vlastnosti**.

7. V okně **vlastnosti Terminálové služby** přejděte na kartu **Obecné** a nastavte **Typ spouštění** na **Ruční**.

8. Klikněte na tlačítko **OK**.

9. Restartujte počítač.

     Tento postup automaticky nepovoluje vzdálenou plochu. Pokud chcete povolit vzdálenou plochu na svém počítači, proveďte následující kroky.

### <a name="to-enable-remote-desktop"></a>Povolení vzdálené plochy

1. Klikněte na tlačítko **Start** a poté klikněte pravým tlačítkem myši na položku **Tento počítač**.

2. Vyberte **vlastnosti**.

     Zobrazí se okno **Vlastnosti systému** .

3. Klikněte na **vzdálené**.

4. V části **Vzdálená plocha**vyberte možnost **dovolit uživatelům vzdálené připojení k tomuto počítači**.

5. Klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:
- [Chyby při vzdáleném ladění a jejich řešení](../debugger/remote-debugging-errors-and-troubleshooting.md)