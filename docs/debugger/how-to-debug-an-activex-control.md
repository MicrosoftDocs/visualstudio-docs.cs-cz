---
title: 'Postupy: ladění ovládacího prvku ActiveX | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75abf76516d3827a748e1b896d4c2e8c93bb34da
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733872"
---
# <a name="how-to-debug-an-activex-control"></a>Postupy: Ladění ovládacího prvku ActiveX

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce Nástroje klikněte na položku Nastavení importu a exportu. Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

Chcete-li ladit ovládací prvek ActiveX, je nutné zadat kontejner (spustitelný soubor), v němž bude ovládací prvek spuštěn.

## <a name="to-specify-a-container-for-the-debug-session"></a>Určení kontejneru pro relaci ladění

1. V Průzkumník řešení vyberte projekt.

2. V nabídce **zobrazení** klikněte na položku **stránky vlastností**.

3. V dialogovém okně **stránky vlastností projektu** otevřete složku **Vlastnosti konfigurace** a vyberte možnost **ladění**.

4. V kategorii **ladění** vyhledejte vlastnost **Command** .

5. Zadejte název cesty pro kontejner. Například C:\Program Files\Internet Explorer\IEXPLORE. Programu.

6. Pokud jako kontejner určíte aplikaci Internet Explorer a používáte službu Active Desktop, zadejte do pole **argumenty příkazu** `/new`.

7. Klikněte na tlačítko **OK**.

     Pokud nezadáte kontejner do dialogového okna **stránky vlastností projektu** , můžete zadat kontejner při zahájení ladění. Když vyberete příkaz pro spuštění pro spuštění ladění, zobrazí se [dialogové okno spustitelný soubor pro relaci ladění](../debugger/executable-for-debugging-session-dialog-box.md) . Zadejte název cesty kontejneru v dialogovém okně.

## <a name="see-also"></a>Viz také:

- [ActiveX – ovládací prvky](/cpp/mfc/activex-controls)
- [Testování vlastností a událostí pomocí testovacího kontejneru](/cpp/mfc/testing-properties-and-events-with-test-container)
- [Ladění modelů COM a prvků ActiveX](../debugger/com-and-activex-debugging.md)
- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)