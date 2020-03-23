---
title: Použití grafu aktivity virtuálního uživatele pro zátěžové testy
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c58dd4f6e6a0c8fe1bd468053bf18c3635b1ee9d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169375"
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>Návod: Použití grafu virtuální aktivity uživatele k odištit problémy

V tomto návodu se dozvíte, jak pomocí grafu virtuální aktivity uživatelů izolovat chyby, ke kterým došlo pro jednotlivé virtuální uživatele, kteří spustili zátěžový test.

Virtuální graf aktivity uživatele umožňuje vizualizovat aktivitu virtuálního uživatele, která je přidružena k zátěžovému testu. Každý řádek v grafu představuje jednotlivého virtuálního uživatele. Graf aktivity virtuálního uživatele zobrazuje přesně to, co každý virtuální uživatel prováděl během testu. To umožňuje izolovat problémy s výkonem zobrazením vzorů aktivity uživatele, vzorů zatížení, korelace neúspěšných nebo pomalých testů a zobrazení požadavků s jinými aktivitami virtuálního uživatele. Virtuální graf aktivity uživatele je k dispozici pouze po načtení po dokončení spuštění.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Požadavky

- Visual Studio Enterprise

- Dokončete tyto postupy:

  - [Zaznamenejte a spusťte test výkonu webu](/azure/devops/test/load-test/run-performance-tests-app-before-release#recordtests).

  - [Vytvoření a spuštění zátěžového testu](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-load-test)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Otevření řešení ColorWebApp vytvořeného v předchozích návodech

1. Otevřete sadu Visual Studio.

2. Otevřete řešení **ColorWebApp,** které obsahuje *LoadTest1.loadtest*. Tento zátěžový test je výsledkem provedení kroků ve třech návodech, které jsou uvedeny na začátku tohoto tématu v části požadavky.

     Zbývající kroky v tomto návodu předpokládají webovou aplikaci s názvem ColorWebApp, test výkonu webu s názvem *ColorWebAppTest.webtest* a zátěžový test s názvem *LoadTest1.loadtest*.

## <a name="run-the-load-test"></a>Spuštění zátěžového testu

Spusťte zátěžový test pro shromažďování dat o virtuální aktivitě uživatelů.

- V **Editoru zátěžových testů**zvolte tlačítko **Spustit** na panelu nástrojů. LoadTest1 spustí.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Izolujte problémy v grafu virtuální aktivity uživatelů

Po spuštění zátěžového testu a shromáždění dat o aktivitě virtuálního uživatele můžete zobrazit data ve výsledcích zátěžového testu pomocí zobrazení **Podrobnosti analyzátoru zátěžového testu** v **grafu aktivity virtuálního uživatele**. Kromě toho můžete použít **virtuální graf aktivity uživatele** k řešení problémů s výkonem v zátěžovém testu.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>Použití grafu aktivity virtuálního uživatele ve výsledcích zátěžového testu

1. Po dokončení zátěžového testu se v **analyzátoru zátěžového testu**zobrazí stránka **Souhrn** pro výsledky zátěžového testu . Zvolte tlačítko **Grafy** na panelu nástrojů.

     Zobrazí se zobrazení Grafy.

2. V grafu **Doba odezvy stránky** klepněte pravým tlačítkem myši na jednu z ikon porušení prahové hodnoty a vyberte **možnost Přejít na podrobnosti uživatele**.

    > [!NOTE]
    > Pomocí tlačítka **Podrobnosti** v pruhu nástrojů **Editor zatížení testu** můžete také otevřít graf Aktivita uživatele. Pokud však použijete možnost **Přejít na podrobnosti uživatele,** **virtuální graf aktivity uživatelů** se automaticky přiblíží k části testu, na kterou jste v grafu klikli pravým tlačítkem myši.

     Zobrazení Podrobnosti se zobrazí s **grafem aktivity virtuálního uživatele** zaměřeným na časové období, kdy došlo k porušení prahové hodnoty.

     Na ose y představují vodorovné obrázky jednotlivé virtuální uživatele. Osa x zobrazuje časovou osu pro spuštění zátěžového testu.

3. V nástroji **Lupa k časovému období** pod **virtuálním grafem aktivity uživatele**upravte posuvníky vlevo a vpravo tak, aby se oba přiblížili k ikoně porušení prahové hodnoty. Tím se změní časové měřítko v **grafu aktivity virtuálního uživatele.**

4. V **legendě podrobností**zaškrtněte políčko **(Zvýraznit chyby).** Všimněte si, že virtuální uživatel, který způsobil porušení prahové hodnoty je zvýrazněna.

5. V panelu **Filtrovat výsledky** zrušte zaškrtnutí políček **Zobrazit úspěšné výsledky** a Chyba **HttpError,** ale ponechte zaškrtnuté políčko **ValidationRuleError.**

     **Graf aktivity virtuálního uživatele** zobrazuje pouze virtuální uživatele, kteří strávili více než 3 sekundy na stránce *Red.aspx,* jak je určeno porušením prahové hodnoty nakonfigurovaným v předchozím návodu.

6. Místo ukazatele myši nad vodorovnou čáru, která představuje virtuální uživatele s chybou ověřovacího pravidla pro porušení prahové hodnoty.

7. Zobrazí se tip nástroje s následujícími informacemi:

    - **ID uživatele**

    - **Scénář**

    - **Test**

    - **Výsledek**

    - **Síť**

    - **Čas zahájení**

    - **Doba trvání**

    - **Agent**

    - **Testovací protokol**

8. Všimněte si, že **protokol test** je odkaz. Zvolte odkaz **Protokol test.**

9. Test výkonu webu ColorWebTest, který je přidružen k protokolu, se otevře v **prohlížeči výsledků testu výkonu webu**. To umožňuje izolovat, kde došlo k porušení prahové hodnoty.

     Můžete použít různá nastavení v **panelech Podrobnosti legenda** a **filtr výsledky** pomoci při izolaci problémy s výkonem a chyby v zátěžových testů. Experimentujte s těmito nastaveními a nástrojem **Zoom to time period,** abyste zjistili, jak jsou virtuální uživatelská data prezentována v **grafu virtuální aktivity uživatele**.

## <a name="see-also"></a>Viz také

- [Analýza aktivity virtuálního uživatele v zobrazení Podrobnosti](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Postup: Vytvoření testovacího nastavení pro distribuovaný zátěžový test](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)
