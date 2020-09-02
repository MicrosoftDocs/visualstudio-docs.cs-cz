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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "78169375"
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>Návod: použití grafu aktivity virtuálního uživatele k izolaci problémů

V tomto návodu se dozvíte, jak pomocí grafu aktivity virtuálního uživatele izolovat chyby, ke kterým došlo u jednotlivých virtuálních uživatelů, kteří spustili zátěžový test.

Graf aktivity virtuálního uživatele umožňuje vizualizovat aktivitu virtuálního uživatele, která je přidružena k vašemu testu zatížení. Každý řádek v grafu představuje jednotlivého virtuálního uživatele. Graf aktivity virtuálního uživatele zobrazuje přesně to, co každý virtuální uživatel vykonává během testu. To vám umožní izolovat problémy s výkonem zobrazením vzorců aktivity uživatelů, vzorů zatížení, korelacemi neúspěšných nebo pomalých testů a zobrazit žádosti s jinou aktivitou virtuálního uživatele. Graf aktivity virtuálního uživatele je k dispozici až po dokončení zatížení po jeho spuštění.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Předpoklady

- Visual Studio Enterprise

- Dokončete tyto postupy:

  - [Zaznamenejte a spusťte test výkonnosti webu](/azure/devops/test/load-test/run-performance-tests-app-before-release#recordtests).

  - [Vytvoření a spuštění zátěžového testu](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-load-test)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Otevřete řešení ColorWebApp vytvořené v předchozích návodech.

1. Otevřete sadu Visual Studio.

2. Otevřete řešení **ColorWebApp** , které obsahuje *LoadTest1. LoadTest*. Výsledkem tohoto zátěžového testu je provedení kroků ve třech návodech uvedených na začátku tohoto tématu v části požadavky.

     Zbývající kroky v tomto návodu předpokládají webovou aplikaci s názvem ColorWebApp, test výkonnosti webu s názvem *ColorWebAppTest. webtest* a zátěžový test s názvem *LoadTest1. LoadTest*.

## <a name="run-the-load-test"></a>Spustit zátěžový test

Spusťte zátěžový test pro shromažďování dat o aktivitě virtuálního uživatele.

- V **Editor zátěžového testu**klikněte na panelu nástrojů na tlačítko **Spustit** . LoadTest1 začne běžet.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Izolace problémů v grafu aktivity virtuálního uživatele

Po spuštění zátěžového testu a shromáždění dat aktivity virtuálního uživatele můžete zobrazit data ve výsledcích zátěžového testu pomocí zobrazení podrobností **analyzátoru zátěžového testu** v **grafu aktivity virtuálního uživatele**. Kromě toho můžete pomocí **grafu aktivity virtuálního uživatele** zajistit izolaci problémů s výkonem v zátěžovém testu.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>Použití grafu aktivity virtuálních uživatelů ve výsledcích zátěžového testu

1. Po skončení běhu zátěžového testu se v **analyzátoru zátěžového testu**zobrazí stránka **Souhrn** pro výsledky zátěžového testu. Na panelu nástrojů klikněte na tlačítko **grafy** .

     Zobrazí se zobrazení grafů.

2. V grafu **Doba odezvy stránky** klikněte pravým tlačítkem myši poblíž jedné z ikon porušení mezní hodnoty a vyberte možnost **Přejít k podrobnostem uživatele**.

    > [!NOTE]
    > K otevření grafu aktivity uživatele můžete použít tlačítko **Podrobnosti** na panelu nástrojů **Editor zátěžového testu** . Pokud však použijete možnost **Přejít k podrobnostem uživatele** , **graf aktivity virtuálního uživatele** se automaticky přiblíží k části testu, kterou jste klepli v grafu přímo.

     Zobrazení podrobností se zobrazí s **grafem aktivity virtuálního uživatele** zaměřeného na časové období, kdy došlo k překročení mezních hodnot.

     Na ose y vodorovné zobrazení znázorňují jednotlivé virtuální uživatele. Na ose x se zobrazuje časová osa pro běh zátěžového testu.

3. V nástroji **přiblížení do časového období** pod **grafem aktivity virtuálního uživatele**upravte posuvníky vlevo a vpravo, dokud obě nebudou blízko ikony porušení mezní hodnoty. Tím se změní časová škála v **grafu aktivity virtuálního uživatele**

4. V **legendě podrobností**zaškrtněte políčko u **(zvýraznit chyby)**. Všimněte si, že virtuální uživatel, který způsobil porušení mezní hodnoty, je zvýrazněný.

5. Na panelu **výsledky filtru** zrušte zaškrtnutí políček **Zobrazit úspěšné výsledky** a **HttpError** , ale nechte políčko **ValidationRuleError** zaškrtnuté.

     V **grafu aktivity virtuálního uživatele** se zobrazí pouze virtuální uživatelé, kteří na stránce *Red. aspx* strávili více než 3 sekundy podle porušení mezní hodnoty nakonfigurovaného v předchozím návodu.

6. Umístěte ukazatel myši na vodorovnou čáru, která představuje virtuálního uživatele s chybou ověřovacího pravidla pro porušení prahové hodnoty.

7. Zobrazí se popis nástroje s následujícími informacemi:

    - **ID uživatele**

    - **Scénář**

    - **Test**

    - **Zaznamenaný**

    - **Síť**

    - **Čas spuštění**

    - **Doba trvání**

    - **Agenta**

    - **Protokol testu**

8. Všimněte si, že **protokol testu** je odkaz. Klikněte na odkaz **protokol testu** .

9. Test výkonnosti webu ColorWebTest, který je přidružen k protokolu, se otevře v **prohlížeči webového výkonu výsledky testů Viewer**. To umožňuje izolovat, kde došlo k překročení mezních hodnot.

     Můžete použít různá nastavení na panelech podrobností v **legendě podrobnosti** a **filtrovat** , které vám pomohou izolovat problémy s výkonem a chyby v zátěžových testech. Experimentujte s těmito nastaveními a nástrojem pro **přiblížení do časového období** , abyste viděli, jak se data virtuálního uživatele zobrazují v **grafu aktivity virtuálního uživatele**.

## <a name="see-also"></a>Viz také

- [Analýza aktivity virtuálních uživatelů v zobrazení podrobností](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Postupy: Vytvoření nastavení testu pro distribuovaný zátěžový test](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)
