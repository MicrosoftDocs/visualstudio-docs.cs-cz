---
title: Postup otevření zobrazení zpráv z okna pro hledání | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3258e45e47c263912957ff5066ea9d02ad03e57e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85349481"
---
# <a name="how-to-open-messages-view-from-find-window"></a>Postupy: Otevření zobrazení zpráv z vyhledávacího okna
Může být vhodné použít dialogové okno **Najít okno** k výběru cílového okna a následně otevřít zobrazení zpráv tohoto okna.

### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>Otevření okna zobrazení zpráv pomocí dialogového okna Najít okno

1. Uspořádejte okna tak, aby se zobrazila okna Spy + + i cílové okno.

2. V nabídce **Spy** vyberte možnost **Najít okno**.

    Otevře se [dialogové okno Najít okno](../debugger/find-window-dialog-box.md) .

3. Z karty **Windows** přetáhněte **Nástroj hledání** přes cílové okno. Při přetahování nástroje se v dialogovém okně **Najít okno** zobrazí podrobnosti o vybraném okně.

   - ani

     Pokud máte popisovač okna, které chcete prošetřit (například zkopírovaný z ladicího programu), můžete ho zadat do textového pole **popisovač** .

4. V části **Zobrazit**vyberte **zprávy**.

5. Stiskněte **OK**.

    Otevře se okno [zobrazení prázdné zprávy](../debugger/messages-view.md) a do panelu nástrojů Spy + + se přidá nabídka **zprávy** .

6. V nabídce **zprávy** vyberte **Možnosti protokolování**.

    Otevře se [dialogové okno Možnosti zprávy](../debugger/message-options-dialog-box.md) .

7. Vyberte možnosti pro zprávy, které chcete zobrazit.

8. Kliknutím na tlačítko **OK** zahajte protokolování zpráv.

    V závislosti na vybraných možnostech zprávy zahájí streamování do okna zobrazení aktivní zprávy.

9. Máte-li dostatek zpráv, v nabídce **zprávy** vyberte možnost **zastavit protokolování** .
