---
title: Přidat vlastní sady čítačů pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7438f657af2ba40fbda5afefbd8a12cc56a2a4c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114866"
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>Postup: Přidání vlastních sad čítačů pomocí Editoru zátěžového testu

Při vytváření zátěžového testu pomocí **Průvodce novým zátěžovým testem**přidáte počáteční sadu čítačů. Ty nabízejí sadu předdefinovaných sad čítačů pro zátěžové testy.

> [!NOTE]
> Pokud jsou zátěžové testy distribuovány napříč vzdálenými počítači, jsou čítače kontroléru a agentů namapovány na sady čítačů kontrolérů a agentů. Další informace o používání vzdálených počítačů v zátěžovém testu naleznete v [tématu Test controllers and test agents](configure-test-agents-and-controllers-for-load-tests.md).

Čítače spravujete v **Editoru zátěžových testů**. Sady čítačů, které jsou již přidány do testu jsou viditelné v uzlu **sady čítačů** zátěžového testu. Po vytvoření zátěžového testu k němu lze přidat nové vlastní sady čítačů.

![Vlastní sada čítačů](../test/media/loadtestcustomcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>Přidání vlastní sady čítačů k zátěžovému testu

1. Otevřete zátěžový test.

2. Rozbalte uzel **sady čítačů.** Jsou zobrazeny všechny sady čítačů, které byly přidány do zátěžového testu.

3. Klepněte pravým tlačítkem myši na uzel **Sady čítačů** a vyberte **přidat vlastní sadu čítačů**.

    > [!NOTE]
    > Sada čítačů má výchozí název, například **Custom1**. Název můžete změnit pomocí okna **Vlastnosti.** Stisknutím **klávesy F4** zobrazte okno **Vlastnosti.**

4. Chcete-li do vlastní sady čítačů přidat čítače, klepněte pravým tlačítkem myši na novou sadu čítačů a pak zvolte **Přidat čítače**. Další informace o přidání čítačů naleznete v [tématu Jak: Přidání čítačů k sadám čítačů](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md).

    > [!NOTE]
    > Vlastní sadu čítačů lze také přidat kliknutím pravým tlačítkem myši na existující sadu čítačů, výběrem příkazu kopírování a následným vložením do uzlu sad čítačů. Další čítače, které jsou zkopírovány, ale nejsou vyžadovány, je možné odstranit. Název nové sady čítačů můžete změnit pomocí okna **Vlastnosti.**

## <a name="see-also"></a>Viz také

- [Určení sad čítačů a prahových hodnot pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurace nastavení spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
