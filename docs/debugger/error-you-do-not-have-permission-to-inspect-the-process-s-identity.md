---
title: 'Chyba: nemáte oprávnění kontrolovat &apos; identitu procesů | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: e91745b8910a9e87ccd4a22fe09c6764a2ab4c6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88706526"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Chyba: nemáte oprávnění kontrolovat identitu procesu&#39;s.
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

8. Klikněte na **OK**.

9. Restartujte počítač.

     Tento postup automaticky nepovoluje vzdálenou plochu. Pokud chcete povolit vzdálenou plochu na svém počítači, proveďte následující kroky.

### <a name="to-enable-remote-desktop"></a>Povolení vzdálené plochy

1. Klikněte na tlačítko **Start** a poté klikněte pravým tlačítkem myši na položku **Tento počítač**.

2. Zvolte **Properties** (Vlastnosti).

     Zobrazí se okno **Vlastnosti systému** .

3. Klikněte na **vzdálené**.

4. V části **Vzdálená plocha**vyberte možnost **dovolit uživatelům vzdálené připojení k tomuto počítači**.

5. Klikněte na **OK**.

## <a name="see-also"></a>Viz také
- [Chyby a řešení potíží se vzdáleným laděním](../debugger/remote-debugging-errors-and-troubleshooting.md)