---
title: Přidání čítačů do sad čítačů pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: b2a6ba058ba7c09eb66c15cb578fcaaf36d2ced2
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894700"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>Postupy: přidání čítačů do sad čítačů pomocí editoru zátěžových testů

Když vytvoříte zátěžový test pomocí **Průvodce zátěžovým testem**, můžete přidat počáteční sadu čítačů. Ty nabízejí sadu předdefinovaných sad čítačů pro zátěžové testy. Další informace najdete v tématu [určení sad čítačů a mezních pravidel pro počítače v rámci zátěžového testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Pokud jsou zátěžové testy distribuovány napříč vzdálenými počítači, jsou čítače kontroléru a agentů namapovány na sady čítačů kontrolérů a agentů. Další informace o tom, aby používaly vzdálené počítače v zátěžovém testu naleznete v tématu [testovací kontrolery a testovací agenty](configure-test-agents-and-controllers-for-load-tests.md).

Můžete spravovat čítače v **editoru zátěžových testů**. Sady čítačů, které již byly přidány do testu jsou viditelné v **sad čítačů** uzel zátěžového testu. Po vytvoření zátěžového testu můžete přidat nové čítače do existující sady čítačů.

## <a name="to-add-counters-to-a-counter-set"></a>Přidání čítačů do sady čítačů

1.  Otevřete zátěžový test.

2.  Rozbalte **sady čítačů** uzlu. Jsou zobrazeny všechny sady čítačů, které byly přidány do zátěžového testu.

    > [!NOTE]
    > Také obsahuje hierarchii strom zátěžového testu **parametrů běhu** uzlu. Tento uzel obsahuje **mapování sady čítačů** uzlu, který se zobrazí všechny počítače a sady čítačů, které jsou mapovány na těchto počítačích.

3.  Klikněte pravým tlačítkem myši na existující sadu čítačů a klikněte na tlačítko **přidat čítače**.

     **Vyberte čítačů výkonu** zobrazí dialogové okno.

4.  V **počítače** rozevírací pole, zadejte název počítače chcete namapovat. Další možností v rozevíracím seznamu vyberte jednu z počítače.

    > [!NOTE]
    > Protože sady čítačů musí být namapována na počítači předtím, než se shromažďují data o výkonu, je nutné zadat počítač, na které se mají shromažďovat data o výkonu.

5.  Vyberte **kategorie výkonu** k filtrování kategorií dat čítače výkonu. Zobrazí se dva sloupce dat, ze kterého chcete vyberte čítačů výkonu.

    > [!NOTE]
    > Některé kategorie čítačů bude vyžadovat také vyberte výchozí instanci. Například pokud vyberete čítače SQL, musíte vybrat instanci SQL vzhledem k tomu může být více než jednu instanci SQL, které jsou nainstalované v cílovém počítači.

6.  Vyberte čítač a instance pro přidání do vaší vlastní sadu čítačů.

     \- nebo –

     Vyberte **všechny čítače** přepínačů k výběru všechny dostupné čítače.

7.  Zvolte **OK**.

    > [!NOTE]
    > Je také možné přidat čítače do sady výběrem existující čítače nebo kategorie čítačů, výběrem příkazu kopírování čítače a následným vložením do různých čítačů nastavte uzel. Další čítače, které jsou zkopírovány, ale nejsou vyžadovány, je možné odstranit.

## <a name="see-also"></a>Viz také:

- [Určení sad čítačů a mezních pravidel pro počítače v rámci zátěžového testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurace parametrů spuštění zátěžového testu](../test/configure-load-test-run-settings.md)