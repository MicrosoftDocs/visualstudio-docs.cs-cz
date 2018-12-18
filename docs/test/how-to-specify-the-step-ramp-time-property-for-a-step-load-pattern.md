---
title: Doba doběhu kroku pro vzor zatížení kroku pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 81373e30498ad02f4007e096cfbc6a7cff953402
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895716"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Postupy: určení vlastnosti doby doběhu kroku pro vzor zatížení kroku

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem**, můžete použít **editoru zátěžového testu** Chcete-li změnit vlastnosti scénářů pro splnění potřebám a cílům testování. Další informace najdete v tématu [návod: vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Úplný seznam vlastnosti scénáře zátěžového testu a jejich popis najdete v tématu [vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

**Doba náběhu kroku** je nastavena **vlastnosti** okna. Upravit vlastnosti scénáře zátěžového testu v **editoru zátěžového testu**.

**Doba náběhu kroku** vlastnost se používá pouze pro vzor zatížení kroku. Další informace najdete v tématu [vzory zatížení úpravy aktivity virtuálního uživatele modelu](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Vzor zatížení kroku slouží ke zvýšení zatížení serveru nebo serverech při spuštění testu zatížení tak, abyste viděli, jak se mění výkon zvýšením zvýšení zatížení uživatele. Například pokud chcete zobrazit, jak váš server nebo servery fungují jako uživatelským zatížením zvyšuje na 2 000 uživatelů, můžete spustit 10 hodinový zátěžový test pomocí vzor zatížení kroku s následujícími vlastnostmi:

-   Počáteční počet uživatelů: 100

-   Maximální počet uživatelů: 2000

-   Doba trvání kroku (sekundy): 1800

-   Krok doba doběhu (sekundy): 20

-   Krok počtu uživatelů: 100

Tato nastavení mají spuštěný po dobu 30 minut (1800 sekund) zátěžový test při zatížení uživatele na 100, 200, 300 až 2 000 uživatelů.

> [!NOTE]
> **Doba náběhu kroku** vlastnost je pouze jeden z těchto vlastností, které nejsou k dispozici pro výběr v **Průvodce novým zátěžovým testem**.

**Doba náběhu kroku** vlastnost umožňuje postupné spíše než okamžité zvýšení z jednoho kroku do druhého (například z 100 až 200 uživatelů). V tomto příkladu uživatelské zatížení by se zvýšilo ze 100 na 200 uživatelů po dobu 20 sekund (zvýšení o 5 uživatelů každou sekundu).

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Chcete-li upravit vlastnosti doby doběhu kroku pro vzor zatížení kroku

1.  Otevřete zátěžový test.

     **Editoru zátěžových testů** se zobrazí. Zobrazí se strom zátěžového testu.

2.  V zátěžového testu stromů **scénáře** složku, otevřete uzel scénář, který chcete zadat doběhu kroku čas pro.

3.  Vyberte **vzor zatížení kroku** uzlu.

    > [!NOTE]
    > Vzor zatížení pro scénář musí být vzor zatížení kroku. Pokud není, zobrazí vzorek zatížení typ vzor zatížení, který je teď přidružená scénář. Další informace najdete v tématu [vzory zatížení úpravy aktivity virtuálního uživatele modelu](../test/edit-load-patterns-to-model-virtual-user-activities.md).

4.  Na **zobrazení** nabídce vyberte možnost **okno vlastností**.

     Tento scénář kategorie a vlastnosti jsou zobrazeny v **vlastnosti** okna.

5.  Nastavit hodnotu pro **doba náběhu kroku** zadáním čísla pro sekund provést postupně v každém kroku k přidání uživatelů zadaných ve vlastnosti **krok počtu uživatelů** vlastnost.

6.  Po dokončení změn vlastnosti, zvolte **Uložit** na **souboru** nabídky. Potom můžete spustit zátěžový test pomocí nového **doba náběhu kroku** hodnotu.

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
- [Úpravy vzorů zatížení pro model aktivity virtuálního uživatele](../test/edit-load-patterns-to-model-virtual-user-activities.md)