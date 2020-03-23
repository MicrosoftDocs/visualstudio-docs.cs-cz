---
title: Čas krokové rampy pro vzor krokového zatížení pro testování zatížení
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a40f7ce4aacfdc03b5e05becbfc83439945f7e8a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588912"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Postup: Určení vlastnosti čas ovou okružní rampu kroku pro vzor zatížení kroku

Po vytvoření zátěžového testu pomocí **Průvodce novým zátěžovým testem**můžete pomocí **Editoru zátěžového testu** změnit vlastnosti scénářů tak, aby vyhovovaly vašim potřebám a cílům testování. Další informace naleznete [v tématu Návod: Vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Úplný seznam vlastností scénáře zátěžového testu a jejich popisy naleznete v tématu [Load test scenario properties](../test/load-test-scenario-properties.md).

Vlastnost **Čas krokové rampy** je nastavena v okně **Vlastnosti.** Vlastnosti scénáře zátěžového testu můžete upravit v **editoru zátěžového testu**.

Vlastnost **Čas krokové rampy** se používá pouze se vzorem zatížení kroku. Další informace naleznete v [tématu Úprava vzorů zatížení k modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Vzor zatížení kroku se používá ke zvýšení zatížení serveru nebo serverů při spuštění zátěžového testu, takže můžete vidět, jak se liší výkon s nárůstem zatížení uživatele. Chcete-li například zjistit, jak si server nebo servery vedou, když se zatížení uživatele zvyšuje na 2 000 uživatelů, můžete spustit 10hodinový zátěžový test pomocí vzoru načtení kroku s následujícími vlastnostmi:

- Počet počátečních uživatelů: 100

- Maximální počet uživatelů: 2000

- Doba trvání kroku (v sekundách): 1800

- Čas na stupavé rampě (v sekundách): 20

- Počet uživatelů kroků: 100

Tato nastavení mají zátěžový test spuštěn po dobu 30 minut (1800 sekund) při zatížení uživatele 100, 200, 300, až 2 000 uživatelů.

> [!NOTE]
> Vlastnost **Čas čas krokové rampy** je jedinou z těchto vlastností, která není k dispozici v **Průvodci novým zátěžového testu**.

**Funkce Čas přechodu kroku** umožňuje zvýšení z jednoho kroku na další (například ze 100 na 200 uživatelů) být postupné, nikoli okamžité. V příkladu by se zatížení uživatele zvýšilo ze 100 na 200 uživatelů během 20 sekund (nárůst o 5 uživatelů každou sekundu).

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Úprava vlastnosti čas ovou okružní schodišti kroku pro vzorek zatížení kroku

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu.** Zobrazí se strom zátěžového testu.

2. Ve **složce** scénáře zátěžového testu otevřete uzel scénáře, pro který chcete zadat čas krokové rampy.

3. Vyberte uzel **Krokový vzorek.**

    > [!NOTE]
    > Vzor zatížení pro scénář musí být vzor zatížení krok. Pokud tomu tak není, vzorek zatížení zobrazí typ vzoru zatížení, který je aktuálně přidružen ke scénáři. Další informace naleznete v [tématu Úprava vzorů zatížení k modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md).

4. V nabídce **Zobrazení** vyberte **Okno vlastnosti**.

     Kategorie a vlastnosti scénáře jsou zobrazeny v okně **Vlastnosti.**

5. Nastavte hodnotu vlastnosti **Čas čas krokové rampy** zadáním čísla pro sekundy pořízené v každém kroku, abyste postupně přidávali uživatele určené vlastností **Počet uživatelů kroku.**

6. Po dokončení změny vlastnosti zvolte **Uložit** v nabídce **Soubor.** Potom můžete spustit zátěžový test pomocí nové hodnoty **čas krokové rampy.**

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
- [Úprava vzorů zatížení pro modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md)
