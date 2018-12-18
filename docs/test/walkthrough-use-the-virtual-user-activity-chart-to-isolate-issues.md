---
title: Pomocí graf aktivity virtuálního uživatele pro zátěžové testy
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8e4584d386cb61aaf7809c8bb5ab748e49543c7e
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895922"
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>Návod: Izolace problémů pomocí graf aktivity virtuálního uživatele

V tomto podrobném návodu se dozvíte, jak izolovat chyby, ke kterým došlo u jednotlivých virtuálních uživatelů, které byly spuštěny zátěžového testu pomocí graf aktivity virtuálního uživatele.

Graf aktivity virtuálního uživatele vám umožňuje vizualizovat aktivitu virtuálního uživatele, který je spojen se zátěžovým testem. Každý řádek v tabulce představuje jednotlivého virtuálního uživatele. Přesně co jednotlivé virtuální uživatele se provádí během testu zobrazí graf aktivity virtuálního uživatele. To umožňuje izolovat problémy s výkonem tím, že zobrazíte vzory aktivity uživatelů, vzory zátěže, korelovat Nezdařená nebo pomalá testy a žádostí pomocí další aktivity virtuálního uživatele. Graf aktivity virtuálního uživatele je k dispozici pouze po načtení po dokončení.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Požadavky

-   Visual Studio Enterprise

-   Provedení těchto postupů:

    -   [Zaznamenání a spuštění testu výkonnosti webu](/azure/devops/test/load-test/run-performance-tests-app-before-release#recordtests).

    -   [Vytvoření a spuštění zátěžového testu](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-load-test)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Otevřete řešení ColorWebApp vytvořili v předchozí návody

1.  Spusťte sadu Visual Studio.

2.  Otevřít **ColorWebApp** řešení, které obsahuje *LoadTest1.loadtest*. Tento zátěžový test výsledky z provádění kroků ve třech návodech, které jsou uvedené na začátku tohoto tématu v části předpoklady.

     Zbývající kroky v tomto názorném postupu předpokládají webovou aplikaci s názvem ColorWebApp test výkonnosti webu s názvem *soubor colorwebapptest.webtest zkompilujete* a zátěžového testu s názvem *LoadTest1.loadtest*.

## <a name="run-the-load-test"></a>Spusťte zátěžový test

Spusťte zátěžový test a shromáždit data aktivity virtuálního uživatele.

-   V **editoru zátěžových testů**, zvolte **spustit** tlačítko na panelu nástrojů. LoadTest1 se spustí.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Izolovat problémy v graf aktivity virtuálního uživatele

Po spuštění zátěžového testu a shromažďují data aktivity virtuálního uživatele, můžete zobrazit data ve výsledcích zátěžového testu pomocí **Analyzéru zátěžového testu** v zobrazení podrobností **graf aktivity virtuálního uživatele** . Kromě toho můžete použít **graf aktivity virtuálního uživatele** a určit tak problémy s výkonem v zátěžovém testu.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>Chcete-li použít graf aktivity virtuálního uživatele ve vašich výsledcích zátěžového testu

1.  Po načtení dokončení testu spuštěn, **Souhrn** stránky pro výsledky zátěžového testu se zobrazí v **Analyzéru zátěžového testu**. Zvolte **grafy** tlačítko na panelu nástrojů.

     Zobrazí se zobrazení grafů.

2.  Na **doba odezvy stránky** graf, klikněte pravým tlačítkem na téměř jeden z ikony narušení prahové hodnoty a vyberte **přejít na podrobnosti uživatele**.

    > [!NOTE]
    > Můžete použít **podrobnosti** tlačítko **editoru zátěžových testů** panelu nástrojů otevřete příliš grafu aktivity uživatele. Ale pokud použijete **přejít na podrobnosti uživatele** možnost, **graf aktivity virtuálního uživatele** bude automaticky zvětšit nároku test, který jste klikli pravým tlačítkem myši na v grafu.

     Zobrazení podrobností se zobrazí u **graf aktivity virtuálního uživatele** zaměřené na toto časové období, kdy došlo k překročení mezních hodnot.

     Vodorovné vykreslení na ose y, představují jednotlivé virtuální uživatele. Osu x zobrazuje časovou osu pro spuštění zátěžového testu.

3.  V **přiblížení na dobu** nástroje níže **graf aktivity virtuálního uživatele**, upravte vlevo a vpravo posuvníky, dokud nebudou zavřít ikonu porušení prahové hodnoty. Tím se změní časového měřítka v **graf aktivity virtuálního uživatele**

4.  V **podrobné legendy**, zaškrtněte políčko pro **(zvýraznit chyby)**. Všimněte si, že virtuální uživatel, který způsobil porušení mezní hodnoty je zvýrazněn.

5.  V **filtrování výsledků** panelu, zrušte zaškrtnutí políček u **zobrazit úspěšné výsledky** a **HttpError** ale ponechte **ValidationRuleError**zaškrtnuté políčko.

     **Graf aktivity virtuálního uživatele** zobrazí pouze virtuálních uživatelů, které stráví více než tři sekundy *Red.aspx* stránce uvedená porušení mezní hodnoty, které jsou nakonfigurované v předchozím postupu.

6.  Umístěte ukazatel myši nad vodorovnou horizontální čáru představující virtuálních uživatelů se chyba ověřovacího pravidla pro porušení prahové hodnoty.

7.  Popis se zobrazí následující informace:

    -   **Id uživatele**

    -   **Scénář**

    -   **Test**

    -   **Výsledek**

    -   **Sítě**

    -   **Čas spuštění**

    -   **Doba trvání**

    -   **Agent**

    -   **Protokol testu**

8.  Všimněte si, že **protokol testu** odkaz. Zvolte **protokol testu** odkaz.

9. Test výkonnosti webu ColorWebTest přidružený k protokolu se otevře v **prohlížeče výsledků testu výkonnosti webu**. Díky tomu můžete izolovat, kde došlo k překročení mezních hodnot.

     Různá nastavení můžete použít v obou **podrobné legendy** a **filtrování výsledků** panelů na pomoc při izolaci problémů s výkonem a chyby v zátěžových testech. Experiment s těmito nastaveními a **přiblížení na dobu** nástroj zobrazíte prezentaci dat virtuálních uživatelů v **graf aktivity virtuálního uživatele**.

## <a name="see-also"></a>Viz také:

- [Analýza aktivity virtuálních uživatelů v podrobném zobrazení](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Postupy: vytvoření nastavení testu pro distribuovaný zátěžový test](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
- [Shromažďování diagnostických údajů pomocí nastavení testů](../test/collect-diagnostic-information-using-test-settings.md)
