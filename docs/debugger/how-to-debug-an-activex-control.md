---
title: Ladění ovládacího prvku ActiveX | Microsoft Docs
Description: Naučte se ladit ovládací prvek ActiveX. Je nutné zadat obsažený spustitelný soubor, který lze provádět na stránkách vlastností projektu nebo při zahájení ladění.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 83522eb13350d86ef0531d90b3db844ece8f6655
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913397"
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

5. Zadejte název cesty pro kontejner. Například C:\Program Files\Internet Explorer\IEXPLORE.EXE.

6. Pokud jako kontejner určíte aplikaci Internet Explorer a používáte službu Active Desktop, zadejte `/new` do pole **argumenty příkazu** .

7. Klikněte na **OK**.

     Pokud nezadáte kontejner do dialogového okna **stránky vlastností projektu** , můžete zadat kontejner při zahájení ladění. Když vyberete příkaz pro spuštění pro spuštění ladění, zobrazí se [dialogové okno spustitelný soubor pro relaci ladění](../debugger/executable-for-debugging-session-dialog-box.md) . Zadejte název cesty kontejneru v dialogovém okně.

## <a name="see-also"></a>Viz také

- [Ovládací prvky ActiveX](/cpp/mfc/activex-controls)
- [Testování vlastností a událostí pomocí kontejneru testů](/cpp/mfc/testing-properties-and-events-with-test-container)
- [Ladění modelu COM a ActiveX](../debugger/com-and-activex-debugging.md)
- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)