---
title: Vytvoření a spuštění zátěžového testu
ms.date: 10/01/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, in load tests
- unit tests, load test walkthrough
- load tests, walkthrough
ms.assetid: bbf075a5-96d5-48ed-a03c-330f0fc04748
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1c2ade11d4bffc3c9fdf812cb38d21cd742c9845
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590849"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>Návod: Vytvoření a spuštění zátěžového testu, který obsahuje testy jednotek

V tomto návodu vytvoříte zátěžový test, který obsahuje testy jednotek.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Tento návod obsahuje kroky vás provedou vytvořením a spuštěním zátěžového testu pomocí sady Visual Studio Enterprise. Zátěžový test je kontejner testů výkonnosti webu a testy jednotek. Vytváření zátěžových testů s **Průvodce novým zátěžovým testem**.

Zátěžové testy také vystaví mnoho vlastností spuštění, které lze upravit a generovat požadovanou simulaci zatížení. V tomto názorném postupu použijete **nového Průvodce zátěžovým testem** přidání jednotkových testů do zátěžového testu.

V tomto návodu dokončíte následující úkoly:

- Vytvořte zátěžový test, který používá testování částí.

- Změňte některá nastavení zátěžového testu.

- Spuštění zátěžového testu.

- Postupujte podle pokynů v [návod: vytváření a spouštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) k vytvoření jednoduché knihovny tříd C#, která obsahuje webového výkonu a test zatížení projektu s některá testování částí v ní.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Vytvořte zátěžový test obsahující testování částí pomocí nového Průvodce zátěžovým testem

### <a name="to-start-the-new-load-test-wizard"></a>Chcete-li spustit Průvodce novým zátěžovým testem

1. Otevřete bankovní řešení, které jste vytvořili [návod: vytváření a spouštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

2. V **Průzkumníka řešení**, otevřete místní nabídku uzlu bankovní řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.

     **Přidat nový projekt** zobrazí dialogové okno.

3. V **přidat nový projekt** dialogového okna rozbalte **Visual C#** a zvolte **Test**. V seznamu šablon zvolte **webový výkon a projekt zátěžového testu** a **název** zadejte `BankLoadTest`. Vyberte **OK**.

     BankLoadTest webového výkonu a zatížení testovací projekt je přidán do řešení.

4. Otevřete místní nabídku pro nové webového výkonu BankLoadTest a zátěžové testování projektu, klikněte na položku **přidat**a klikněte na tlačítko **zátěžový Test**.

5. **Průvodce novým zátěžovým testem** spustí.

6. **Úvodní** stránku **Průvodce novým zátěžovým testem** je první stránka.

7. Zvolte **Další**.

### <a name="to-edit-settings-for-load-test-scenario"></a>Chcete-li upravit nastavení scénáře zátěžového testu

1. V **zadejte název pro scénář testování zatížení** textového pole, typ **ScenarioSample**.

     A *scénář* virtuálních sítí je mechanismus seskupení. Skládá se ze sady testů a vlastnosti pro spuštění těchto testů při zatížení.

2. Nastavte **čas profil zvažte** k `Use normal distribution centered on recorded think times`. Časy přemýšlení představují čas, který by uživatel uvažoval na webové stránce před přechodem na další stránku.

1. Zvolte **Další** až budete hotoví.

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Chcete-li upravit nastavení vzoru zatížení pro scénář testování

1. Zvolte **krokové zatížení**.

    > [!NOTE]
    > Můžete vybrat ze dvou typů vzorů zatížení: konstantní a krokové. Každý typ má své funkce při testování zatížení, ale pro účely tohoto návodu zvolte **krokové zatížení**.

2. Nastavte **počáteční počet uživatelů** na 10 uživatelů.

3. Nastavte **doba trvání kroku** na 10 sekund.

4. Nastavte **krok počtu uživatelů** na 10 uživatelů/krok.

5. Nastavte **maximální počet uživatelů** až 100 uživatelů.

6. Zvolte **Další**.

### <a name="to-select-test-mix-model-for-the-scenario"></a>Vyberte model kombinace testů pro scénář

1. V části **jak by být poměr testů modelován**vyberte **podle celkového počtu testů**.

2. Zvolte **Další**.

### <a name="to-add-unit-tests-to-the-scenario"></a>Chcete-li přidat jednotkové testy do scénáře

1. Dalším krokem je **přidat testy do zátěžového testu scénář a upravit poměr testů**.

2. Zvolte **přidat** vyberte testy.

3. Zvolte **CreditTest** jednotek testů uvedených v **dostupné testy** podokno, které jsou uvedeny všechny testy webového výkonu a testy jednotek ve výkonnosti testu a projekt zátěžového testu.

4. Výběrem šipky přidejte **CreditTest** testu jednotky **vybrané testy** podokně.

5. Zopakujte kroky 3 a 4 pro **DebitTest** a **FreezeAccountTest** testování částí.

6. Po přidání všech tří testování jednotek zvolte **OK**.

     Budou vám nabídnuty kombinace testů.

7. Přesuňte posuvník v části **distribuce** pro **CreditTest** mírně vpravo k nastavení rozložení testu. Všimněte si, že i ostatní jezdce doleva automaticky přesunout tak, aby rozdělení zůstalo na 100 %.

8. Zvolte **Další**.

### <a name="to-select-network-mix-for-test-scenario"></a>Výběr kombinace sítě pro testovací scénář

1. Vyberte typ připojení LAN pro přidání do skupiny šířek pásma sítě.

     Můžete přidat další typy sítí. Pomocí jezdců nastavte testovací rozdělení a váhu.

2. Zvolte **Další**.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Chcete-li určete počítače sledované sadou čítačů při spuštění zátěžového testu

1. Zvolte **Další**.

     Další informace o sady čítačů viz [určení sad čítačů a mezních pravidel pro počítače v rámci zátěžového testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

### <a name="to-edit-run-setting-for-load-test"></a>Úprava nastavení spuštění pro zátěžový test

1. Vyberte **trvání zátěžového testu** a potom nastavte **doba běhu** 2 minuty za účelem *orientačního testování* zátěžového testu.

     Při vytváření zátěžových testů, je vhodné ověřit, že je vše nastaveno správně a běží podle očekávání, spuštěním krátkého lehkého zatížení testu. Tento proces se označuje jako *orientační testování*.

2. Zvolte **Dokončit**. Váš zátěžový test je otevře v **editoru zátěžových testů**.

## <a name="run-the-load-test"></a>Spusťte zátěžový test
 Po vytvoření zátěžového testu ji spusťte a zjistit, jak vaše bankovní aplikace reaguje na simulaci zatížení. Když je spuštěn zátěžový test, se zobrazí **Analyzéru zátěžového testu** okna.

### <a name="to-run-the-load-test"></a>Ke spuštění zátěžového testu

1. U tohoto zátěžového testu otevřít v **editoru zátěžových testů**, zvolte zelené **spustit Test** tlačítko na panelu nástrojů. Zátěžový test se spustí.

2. Pokud simulace testu překročí libovolný práh, zobrazí se ikony v uzlech stromových ovládacích prvků do označily narušení prahové hodnoty. Chyby mají překryv červeného kruhu a upozornění mají překryv žlutého trojúhelníku. Můžete nalézt čítač překročení této mezní hodnoty a vytvořit pro něj graf přetažením ikony na grafu. Můžete to provést, když je spuštěn test.

## <a name="see-also"></a>Viz také:

- [Upravit poměr testů k určení, které testy mají být zahrnuty do scénáře zátěžového testu](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Určení typů virtuálních sítí](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)
- [Úpravy vzorů zatížení pro model aktivity virtuálního uživatele](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Úpravy modelů kombinací testů a určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
