---
title: Sady čítačů zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.dialog.countersetmapping
helpviewer_keywords:
- counters, counter sets
- performance counters
- counter sets
- load tests, counter sets
ms.assetid: 64315c2f-a0b2-4378-be16-0774b99beef5
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 995cf0653886745d44ede4553e03f81ed45d37d7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049078"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>Postupy: Správa sad čítačů pomocí editoru zátěžových testů

Když vytvoříte zátěžový test pomocí **nového Průvodce zátěžovým testem**, můžete přidat počáteční sadu čítačů. Ty nabízejí sadu předdefinovaných sad čítačů pro zátěžové testy.

> [!NOTE]
> Pokud jsou zátěžové testy distribuovány napříč vzdálenými počítači, jsou čítače kontroléru a agentů namapovány na sady čítačů kontrolérů a agentů. Další informace o tom, aby používaly vzdálené počítače v zátěžovém testu naleznete v tématu [testovací kontrolery a testovací agenty](configure-test-agents-and-controllers-for-load-tests.md).

Správa sad čítačů zahrnuje sadu počítačů, které chcete shromažďovat data o výkonu z výběru a přiřazování sadu čítačů, které mají být shromažďovány z jednotlivých počítačů. Můžete spravovat čítače v **editoru zátěžových testů**.

![Správa sad čítačů](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>Spravovat sady čítačů

1.  Otevřete zátěžový test.

2.  Zvolte **spravovat sady čítačů** tlačítko.

     – nebo –

     Klikněte pravým tlačítkem na **sady čítačů** složky v zátěžového testování stromu a zvolte **spravovat sady čítačů**.

     **Spravovat sady čítačů** se zobrazí dialogové okno.

3.  (Volitelné) V **vybrané počítače a sady čítačů budou přidány pod následující nastavení spuštění** seznamu, vyberte jiný parametr spuštění.

    > [!NOTE]
    > To platí, pouze pokud máte více než jeden parametr spuštění zátěžového testu.

4.  (Volitelné) Zvolte **přidat počítač** k přidání nového počítače do monitorování. Zobrazí se výzva k zadání názvu. Zadejte název počítače a zobrazí se uzly pod novou položku. Například **ASP.NET**, **IIS**, **SQL**a další. Zaškrtněte políčka u uzlů, které chcete vybrat. Nové čítače joinkind **náhled vybrané možnosti** podokně.

5.  (Volitelné) V **značky počítače** textového pole zadejte značku pro přiřazení k počítači. Například "TestMachine12 v lab3."

     Značky počítače umožňují určit počítač s názvem snadno rozpoznat.

     Značky jsou zobrazeny v **mapování sady čítačů** uzel ve stromu v editoru zátěžového testu. Důležitější, značky se zobrazí v sestavách aplikace Excel, které pomáhají identifikovat účastníky jakou roli má počítač v zátěžovém testu. Například "Web Server1 v lab2" nebo "SQL Server2 Phoenixu". Další informace najdete v tématu [sestavy zátěžové testy s výsledky pro porovnávání testů a analýzu trendů](../test/compare-load-test-results.md).

6.  Zvolte **OK**.

## <a name="see-also"></a>Viz také:

- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Určení sad čítačů a mezních pravidel pro počítače v rámci zátěžového testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurace parametrů spuštění zátěžového testu](../test/configure-load-test-run-settings.md)