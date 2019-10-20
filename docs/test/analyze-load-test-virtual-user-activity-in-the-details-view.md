---
title: Analýza aktivity virtuálního uživatele zátěžového testu
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bba807eae2a7767b9b4271d0df48e962a2113285
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665359"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analýza aktivity virtuálního uživatele zátěžového testu v zobrazení podrobností analyzátoru zátěžového testu

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Graf aktivity virtuálního uživatele**

![Graf aktivity virtuálního uživatele](../test/media/virtual_actchart.png)

V zobrazení **podrobností** se zobrazuje **graf aktivity virtuálního uživatele**, který se používá k vizuální analýze toho, co jednotliví uživatelé provedli během zátěžového testu. **Graf aktivity virtuálního uživatele** umožňuje zobrazit vzory aktivity uživatelů, vzory zatížení, korelaci neúspěšných nebo pomalých testů a zobrazit žádosti s jinou aktivitou virtuálního uživatele. **Graf aktivity virtuálního uživatele** vám také pomůže určit špičky využití procesoru, pokles požadavků za sekundu a jaké testy nebo stránky byly spuštěny během špičky a poklesu.

> [!NOTE]
> Před spuštěním zátěžového testu, pro který chcete použít **graf podrobností aktivity virtuálního uživatele**, je nutné ověřit, že vlastnost **úložiště podrobností časování** je nastavena na možnost **AllIndividualDetails** pomocí editoru testu výkonu zátěže.

**Panel legendy podrobností**

![Panel legendy podrobností](../test/media/ltest_detailslegend.png)

Panel legenda podrobností je viditelný v **grafu aktivity virtuálního uživatele**. Podokno Podrobnosti o legendě umožňuje odfiltrovat testy, stránky a transakce na základě několika různých kritérií. Můžete například odebrat některé testy ze zobrazení nebo odebrat všechny úspěšné testy nebo odebrat testy, které selhaly s určitými chybami. Můžete také odebrat všechny testy, které nemají protokoly.

Můžete zvýraznit testy, u kterých došlo k chybě, která zobrazuje všechny neúspěšné testy barevně červené. Můžete také zvýraznit testy, které mají protokoly testů. Testy s protokoly budou barevné zeleně.

**Panel výsledků filtru**

![Panel výsledků filtru](../test/media/ltest_filterresults.png)

Panel výsledků filtru je viditelný v **grafu aktivity virtuálního uživatele**. Panel výsledků filtru může filtrovat následující:

- **Zobrazit pouze výsledky s protokoly** Zobrazí pouze výsledky testů, ke kterým jsou přidruženy protokoly testů.

- **Zobrazit úspěšné výsledky** Zobrazí úspěšné výsledky.

- **Zobrazit výsledky s chybami** Zobrazí výsledky s chybami, které mohou při ladění pomáhat.

## <a name="tasks"></a>Úkoly

|Úkoly|Přidružená témata|
|-|-|
|**Spusťte zátěžový test:** Jakmile vytvoříte zátěžový test a nakonfigurujete ho tak, aby umožňoval shromažďování dat aktivity virtuálního uživatele, je nutné spustit test, dokud není dokončen, aby bylo možné zobrazit **graf aktivity virtuálního uživatele**.||
|**Zobrazení výsledků zátěžového testu, které obsahují data aktivity virtuálního uživatele:** Po vytvoření, konfiguraci a dokončení zátěžového testu můžete zobrazit data aktivity virtuálního uživatele pomocí **grafu aktivity virtuálního uživatele**.|-   [analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Postupy: analýza virtuálních uživatelů během zátěžového testu](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Izolace potíží s výkonem v zátěžových testech:** **Graf aktivity virtuálního uživatele** můžete použít ke zjištění problémů s výkonem v zátěžovém testu.|-   [Návod: použití grafu aktivity virtuálního uživatele k izolaci problémů](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Viz také:

- [Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analýza výsledků zátěžových testů a chyb v zobrazení tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)