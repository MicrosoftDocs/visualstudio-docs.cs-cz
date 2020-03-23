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
ms.openlocfilehash: 780485a4d42cad574cddaaa5a9ae51a65a1a9b7d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093631"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>Návod: Vytvoření a spuštění zátěžového testu, který obsahuje testy částí

V tomto návodu vytvoříte zátěžový test, který obsahuje testy částí.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Tento návod vás provede vytvořením a spuštěním zátěžového testu pomocí sady Visual Studio Enterprise. Zátěžový test je kontejner testů výkonu webu a testování částí. Zátěžové testy vytváříte pomocí **Průvodce novým zátěžovým testem**.

Zátěžový test také zveřejňuje mnoho vlastností za běhu, které lze upravit tak, aby generovaly požadovanou simulaci zatížení. V tomto návodu použijete **Průvodce novým zátěžového testu** k přidání testů částí do zátěžového testu.

V tomto návodu dokončíte následující úkoly:

- Vytvořte zátěžový test, který používá testy částí.

- Změňte některá nastavení zátěžového testu.

- Spusťte zátěžový test.

- Proveďte kroky v [návodu: Vytvoření a spuštění testů částí spravovaného kódu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) k vytvoření jednoduché knihovny tříd c# obsahující webový výkon a projekt zátěžového testu s některými testy částí.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Vytvoření zátěžového testu obsahujícího testy částí pomocí Průvodce novým zátěžovými testy

### <a name="to-start-the-new-load-test-wizard"></a>Spuštění Průvodce novým zátěžového testu

1. Ujistěte se, že jste nainstalovali součást **nástrojů pro testování výkonu webu a zátěžového testování** popsanou v části Vytvoření projektu [zátěžového testu](../test/quickstart-create-a-load-test-project.md).

1. Otevřete bankovní řešení, které jste vytvořili v [návodu: Vytvoření a spuštění testů částí spravovaného kódu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

1. V **Průzkumníku řešení**otevřete místní nabídku pro uzel bankovního řešení, zvolte **Přidat**a pak zvolte **Nový projekt**.

     Zobrazí se dialogové okno **Přidat nový projekt.**

1. V dialogovém okně **Přidat nový projekt** rozbalte visual **c#** a zvolte **Testovat**. Ze seznamu šablon zvolte **Projekt webového výkonu a zátěžového testu** a v poli **Název** zadejte `BankLoadTest`. Vyberte **OK**.

     Projekt webového výkonu a zátěžového testu BankLoadTest je přidán do řešení.

1. Otevřete místní nabídku pro nový webový výkon BankLoadTest a načíst testovací projekt, zvolte **Přidat**a pak zvolte **Load Test**.

1. Spustí se **Průvodce novým zátěžového testem.**

1. **Úvodní** stránka **Průvodce novým zátěžového testu** je první stránkou.

1. Zvolte **Další**.

### <a name="to-edit-settings-for-load-test-scenario"></a>Úprava nastavení scénáře zátěžového testu

1. Do pole **Zadejte název textového** pole scénář zátěžového testu zadejte **ScenarioSample**.

     *Scénář* je mechanismus seskupení. Skládá se ze sady testů a vlastnosti pro spuštění těchto testů pod zatížením.

2. Nastavte **časový profil** `Use normal distribution centered on recorded think times`Myslet na . Představte si, že časy představují čas, kdy by uživatel přemýšlel o webové stránce před tím, než by se na další stránku.

1. Po dokončení zvolte **Další.**

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Úprava nastavení vzoru zatížení pro testovací scénář

1. Zvolte **Načíst krok**.

    > [!NOTE]
    > Můžete si vybrat ze dvou typů vzorů zatížení: konstantní a krok. Každý typ má svou funkci v zátěžovém testování, ale pro účely tohoto návodu zvolte **krok zatížení**.

2. Nastavte **počet uživatelů Start** na 10 uživatelů.

3. Nastavte **dobu trvání kroku** na 10 sekund.

4. Nastavte **počet uživatelů kroku** na 10 uživatelů/krok.

5. Nastavte **maximální počet uživatelů** na 100 uživatelů.

6. Zvolte **Další**.

### <a name="to-select-test-mix-model-for-the-scenario"></a>Výběr modelu kombinace testů pro scénář

1. V části **Jak by měla být kombinace testů modelována**vyberte Na základě celkového počtu **testů**.

2. Zvolte **Další**.

### <a name="to-add-unit-tests-to-the-scenario"></a>Přidání testů částí do scénáře

1. Dalším krokem je **přidání testů do scénáře zátěžového testu a úprava kombinace testů**.

2. Zvolte **Přidat,** chcete-li vybrat testy.

3. Zvolte testy částí **CreditTest** uvedené v podokně **Dostupné testy,** které uvádí všechny testy výkonu webu a testy částí v projektu webového výkonu a zátěžového testu.

4. Zvolte šipku, chcete-li přidat test jednotky **CreditTest** do **podokna Vybrané testy.**

5. Opakujte kroky 3 a 4 pro testy částí **DebitTest** a **FreezeAccountTest.**

6. Po přidání tří testů částí zvolte **OK**.

     Zobrazí se kombinace testů.

7. Posunutím posuvníku v části **Distribuce** pro **CreditTest** mírně doprava upravit rozložení testu. Všimněte si, že ostatní posuvníky přesunout doleva automaticky tak, aby rozdělení zůstane na 100 %.

8. Zvolte **Další**.

### <a name="to-select-network-mix-for-test-scenario"></a>Výběr kombinace sítí pro testovací scénář

1. Vyberte typ připojení k síti LAN, který chcete přidat do kombinace šířky pásma sítě.

     Můžete přidat další typy sítí. Pomocí posuvníků nastavte rozložení a vážení testu.

2. Zvolte **Další**.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Určení počítačů, které mají být sledovány pomocí sad čítačů během spuštění zátěžového testu

1. Zvolte **Další**.

     Další informace o sadách čítačů naleznete [v tématu Určení sad čítačů a prahových hodnot pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

### <a name="to-edit-run-setting-for-load-test"></a>Úprava nastavení spuštění pro zátěžový test

1. Vyberte **dobu trvání zátěžového testu** a pak nastavte dobu **běhu** na 2 minuty, aby bylo možné *testovat* zátěžový test.

     Při vytváření zátěžových testů je vhodné ověřit, že vše je správně nakonfigurováno a spuštěno podle očekávání spuštěním krátkého testu lehkého zatížení. Tento proces se nazývá *testování kouře*.

2. Zvolte **Dokončit**. Zátěžový test se otevře v **Editoru zátěžového testu**.

## <a name="run-the-load-test"></a>Spuštění zátěžového testu
 Po vytvoření zátěžového testu jej spusťte a zobrazte, jak bankovní aplikace reaguje na simulaci zatížení. Při spuštění zátěžového testu se zobrazí okno **Load Test Analyzer.**

### <a name="to-run-the-load-test"></a>Spuštění zátěžového testu

1. Při otevřeném zátěžovém testu v **Editoru zátěžového testu**zvolte zelené tlačítko **Spustit test** v panelu nástrojů. Spustí se zátěžový test.

2. Pokud testovací simulace překročí všechny prahové hodnoty, zobrazí se v uzlech ovládacího prvku stromu ikony označující porušení prahové hodnoty. Chyby mají překrytí červeného kruhu, varování mají překrytí žlutého trojúhelníku. Můžete najít čítač, který překročil prahovou hodnotu a graf je přetažením ikony do grafu. Můžete to provést v době, kdy je test spuštěn.

## <a name="see-also"></a>Viz také

- [Upravte kombinaci testů a určete, které testy mají být zahrnuty do scénáře zátěžového testu](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Určení typů virtuálních sítí](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
- [Úprava vzorů zatížení pro modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Úprava modelů kombinace textu pro určení pravděpodobnosti spuštění testu virtuálním uživatelem](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
