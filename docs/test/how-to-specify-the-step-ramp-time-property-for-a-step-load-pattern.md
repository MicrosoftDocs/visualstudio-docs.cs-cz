---
title: Doba náběhu kroku pro zátěžové testování
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 83ec0866407ef22e2f6c12e21207f8616b9a9477
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810572"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Postupy: určení vlastnosti doby rampy kroku pro vzor zatížení

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem**můžete pomocí **Editor zátěžového testu** změnit vlastnosti scénářů tak, aby vyhovovaly vašim požadavkům na testování a cílům. Další informace naleznete v tématu [Návod: vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Úplný seznam vlastností scénáře zátěžového testu a jejich popis naleznete v tématu [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

Vlastnost **Doba rampy kroku** je nastavena v okně **vlastnosti** . Vlastnosti scénáře zátěžového testu upravíte v **Editor zátěžového testu**.

Vlastnost **Doba rampy kroku** se používá pouze se vzorem zatížení kroku. Další informace najdete v tématu [Úpravy vzorů zatížení pro modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Vzor zatížení kroku se používá ke zvýšení zatížení serveru nebo serverů při spuštění zátěžového testu, abyste viděli, jak se výkon mění, protože se zvyšuje zatížení uživatele. Například chcete-li zjistit, jak server nebo servery fungují jako zvýšení zatížení uživatele 2 000 uživatelů, můžete spustit zátěžový test pomocí kroku vzor zatížení s následujícími vlastnostmi:

- Počáteční počet uživatelů: 100

- Maximální počet uživatelů: 2000

- Doba trvání kroku (sekundy): 1800

- Doba rozběhu kroku (sekundy): 20

- Počet kroků uživatele: 100

Tato nastavení mají zátěžový test spuštěný po dobu 30 minut (1800 sekund) v případě, že uživatel načítá 100, 200, 300, až 2 000 uživatelů.

> [!NOTE]
> Vlastnost **Doba rampy kroku** je jedinou vlastností, kterou není možné vybrat v **novém Průvodce zátěžovým testem**.

Vlastnost **Doba** rozjezdu kroku umožňuje zvýšit od jednoho kroku k dalšímu (například od 100 do 200 uživatelů), aby bylo možné postupovat spíše než okamžitě. V tomto příkladu se uživatelské zatížení zvýšilo z 100 na 200 uživatelů za 20 sekund období (zvýšení počtu 5 uživatelů každou sekundu).

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Úprava vlastnosti doby rampy kroku pro vzor zatížení

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu** . Zobrazí se strom zátěžového testu.

2. Ve složce **scénáře** stromů zátěžového testu otevřete uzel scénář, pro který chcete určit dobu trvání kroku.

3. Vyberte uzel **vzor zatížení kroku** .

    > [!NOTE]
    > Vzor zatížení pro scénář musí být vzor zatížení kroku. Pokud není, vzor zatížení zobrazí typ vzoru zatížení, který je aktuálně přidružen k tomuto scénáři. Další informace najdete v tématu [Úpravy vzorů zatížení pro modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md).

4. V nabídce **zobrazení** vyberte **okno Vlastnosti**.

     Kategorie a vlastnosti scénáře se zobrazí v okně **vlastnosti** .

5. Nastavte hodnotu vlastnosti doba přechodu **kroku** zadáním počtu sekund pořízených v jednotlivých krocích, abyste mohli postupně přidávat uživatele zadané pomocí vlastnosti **počet kroků uživatele** .

6. Po dokončení změny vlastnosti vyberte v nabídce **soubor** možnost **Uložit** . Pak můžete spustit zátěžový test s použitím nové hodnoty **času přístupnosti** .

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
- [Úprava vzorů zatížení pro modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md)
