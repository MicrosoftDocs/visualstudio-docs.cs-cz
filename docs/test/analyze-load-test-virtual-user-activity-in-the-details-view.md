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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0289ff0d4a20eacc4f6801d9300d39df594bc79e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591232"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analýza aktivity virtuálního uživatele zátěžového testu v zobrazení Podrobnosti analyzátoru zátěžového testu

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Graf aktivity virtuálního uživatele**

![Graf aktivity virtuálního uživatele](../test/media/virtual_actchart.png)

Zobrazení **Podrobnosti** zobrazuje **graf aktivity virtuálního uživatele**, který slouží k vizuální analýze toho, co jednotliví virtuální uživatelé provedli během zátěžového testu. **Virtuální graf aktivity uživatele** umožňuje zobrazit vzory aktivity uživatele, vzory zatížení, korelovat neúspěšné nebo pomalé testy a zobrazit požadavky s jinými aktivitami virtuálních uživatelů. **Virtuální graf aktivity uživatele** můžete také pomoci určit špičky v využití procesoru, kapky v požadavcích za sekundu a jaké testy nebo stránky byly spuštěny během špičky a kapky.

> [!NOTE]
> Před spuštěním zátěžového testu, pro který chcete použít **graf podrobností aktivity virtuálního uživatele**, je nutné ověřit, zda je vlastnost **Úložiště podrobností časování** nastavena na možnost **AllIndividualDetails** pomocí editoru sledování výkonu zatížení.

**Panel Legenda podrobností**

![Panel Legenda podrobností](../test/media/ltest_detailslegend.png)

Panel legendy podrobností je viditelný v **grafu virtuální aktivity uživatele**. Podokno legendy podrobností umožňuje odfiltrovat testy, stránky a transakce na základě několika různých kritérií. Můžete například odebrat určité testy ze zobrazení nebo odebrat všechny úspěšné testy nebo odebrat testy, které se nezdařily s určitými chybami. Můžete také odebrat všechny testy, které nemají protokoly.

Můžete zvýraznit testy, které se nezdařily, které zobrazují všechny neúspěšné testy zbarveny červeně. Můžete také zvýraznit testy, které mají protokoly testů. Testy s protokoly budou zbarveny zeleně.

**Panel výsledků filtru**

![Panel výsledků filtru](../test/media/ltest_filterresults.png)

Panel Výsledky filtru je viditelný v **grafu aktivity virtuálního uživatele**. Panel Výsledků filtru může filtrovat následující:

- **Zobrazit pouze výsledky s protokoly** Zobrazí pouze výsledky testů, které mají protokoly testů s nimi spojené.

- **Zobrazit úspěšné výsledky** Zobrazí úspěšné výsledky.

- **Zobrazit výsledky s chybami** Zobrazí výsledky s chybami, které mohou pomoci při ladění.

## <a name="tasks"></a>Úlohy

|Úlohy|Přidružená témata|
|-|-|
|**Spusťte zátěžový test:** Po vytvoření zátěžového testu a jeho konfiguraci tak, aby umožňoval shromažďování dat o aktivitách virtuálního uživatele, je nutné jej spustit, dokud nebude dokončen, aby bylo možné zobrazit **graf aktivity virtuálního uživatele**.||
|**Zobrazení výsledků zátěžového testu, které obsahují data o aktivitě virtuálního uživatele:** Po vytvoření, konfiguraci a dokončení zátěžového testu můžete zobrazit data aktivity virtuálního uživatele pomocí **grafu aktivity virtuálního uživatele**.|-   [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Postup: Analýza toho, co virtuální uživatelé dělají během zátěžového testu](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Izolovat problémy s výkonem v zátěžových testech:** Graf **aktivity virtuálního uživatele** můžete použít k nastavení problémů s výkonem v zátěžovém testu.|-   [Návod: Použití grafu aktivity virtuálního uživatele k odištit problémy](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Viz také

- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analýza výsledků zátěžových testů a chyb v zobrazení Tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
