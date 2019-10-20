---
title: Přidání vlastních sad čítačů pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e35794dd238ad816badeff34094a340e8e21d16d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664840"
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>Postupy: Přidání vlastních sad čítačů pomocí Editor zátěžového testu

Při vytváření zátěžového testu s **novým Průvodce zátěžovým testem**přidáte počáteční sadu čítačů. Ty nabízejí sadu předdefinovaných sad čítačů pro zátěžové testy.

> [!NOTE]
> Pokud jsou zátěžové testy distribuovány napříč vzdálenými počítači, jsou čítače kontroléru a agentů namapovány na sady čítačů kontrolérů a agentů. Další informace o použití vzdálených počítačů v rámci zátěžového testu naleznete v tématu [řadiče testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

Čítače můžete spravovat v **Editor zátěžového testu**. Sady čítačů, které jsou již přidány do testu, jsou zobrazeny v uzlu **sady čítačů** zátěžového testu. Po vytvoření zátěžového testu k němu lze přidat nové vlastní sady čítačů.

![Vlastní sada čítačů](../test/media/loadtestcustomcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>Přidání vlastní sady čítačů k zátěžovému testu

1. Otevřete zátěžový test.

2. Rozbalte uzel **sady čítačů** . Jsou zobrazeny všechny sady čítačů, které byly přidány do zátěžového testu.

3. Klikněte pravým tlačítkem na uzel **sady čítačů** a vyberte **Přidat vlastní sadu čítačů**.

    > [!NOTE]
    > Sadě čítačů je přiřazen výchozí název, například **vlastní1**. Název můžete změnit pomocí okna **vlastnosti** . Stisknutím klávesy **F4** zobrazte okno **vlastnosti** .

4. Chcete-li přidat čítače do vlastní sady čítačů, klikněte pravým tlačítkem myši na novou sadu čítačů a zvolte možnost **Přidat čítače**. Další informace o tom, jak přidat čítače, najdete v tématu [Postupy: Přidání čítačů do sad čítačů](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md).

    > [!NOTE]
    > Vlastní sadu čítačů lze také přidat kliknutím pravým tlačítkem myši na existující sadu čítačů, výběrem příkazu kopírování a následným vložením do uzlu sad čítačů. Další čítače, které jsou zkopírovány, ale nejsou vyžadovány, je možné odstranit. Název nové sady čítačů můžete změnit pomocí okna **vlastnosti** .

## <a name="see-also"></a>Viz také:

- [Určení sad čítačů a mezních pravidel pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurovat nastavení běhu zátěžového testu](../test/configure-load-test-run-settings.md)