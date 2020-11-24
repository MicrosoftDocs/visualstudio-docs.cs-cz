---
title: Vytvoření a spuštění zátěžového testu
description: Naučte se vytvořit zátěžový test, který obsahuje testy jednotek. Zátěžové testy můžete vytvářet a spouštět pomocí Visual Studio Enterprise.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bdcd96e8fc87a7627689af1c67a81b69b2ecee72
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598260"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>Návod: vytvoření a spuštění zátěžového testu, který obsahuje testy jednotek

V tomto návodu vytvoříte zátěžový test, který obsahuje testy jednotek.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Tento názorný postup vás provede vytvořením a spuštěním zátěžového testu pomocí Visual Studio Enterprise. Zátěžový test je kontejnerem testů výkonnosti webu a testování částí. Zátěžové testy lze vytvořit pomocí **nového Průvodce zátěžovým testem**.

Zátěžový test také zpřístupňuje mnoho vlastností modulu runtime, které lze upravit, aby vygenerovalo požadovanou simulaci zatížení. V tomto návodu použijete **novou Průvodce zátěžovým testem** k přidání testů jednotek do zátěžového testu.

V tomto návodu provedete následující úlohy:

- Vytvořte zátěžový test, který používá testy jednotek.

- Změňte některá nastavení zátěžového testu.

- Spusťte zátěžový test.

- Proveďte kroky v [návodu: vytváření a spouštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) k vytvoření jednoduché knihovny tříd C#, která obsahuje projekt webového výkonu a zátěžového testu s některými testy jednotek v ní.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Vytvoření zátěžového testu obsahujícího testy jednotek pomocí nového Průvodce zátěžovým testem

### <a name="to-start-the-new-load-test-wizard"></a>Spuštění nového Průvodce zátěžovým testem

1. Ujistěte se, že máte nainstalovanou součást **Performance Test Tools a zátěžové testování** , která je popsaná v tématu [Vytvoření projektu zátěžového testu](../test/quickstart-create-a-load-test-project.md).

1. Otevřete bankovní řešení, které jste vytvořili v [návodu: vytváření a spouštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

1. V **Průzkumník řešení** otevřete místní nabídku pro uzel banka řešení, zvolte možnost **Přidat** a pak zvolte možnost **Nový projekt**.

     Zobrazí se dialogové okno **Přidat nový projekt** .

1. V dialogovém okně **Přidat nový projekt** rozbalte položku **Visual C#** a klikněte na tlačítko **test**. V seznamu šablon vyberte možnost **projekt webového výkonu a zátěžového testu** a do pole **název** zadejte `BankLoadTest` . Vyberte **OK**.

     Do řešení se přidá projekt webového výkonu a zátěžového testu BankLoadTest.

1. Otevřete místní nabídku pro nový projekt webového výkonu a zátěžového testu BankLoadTest, zvolte možnost **Přidat** a pak zvolte možnost **zátěžový test**.

1. Spustí se **nový Průvodce zátěžovým testem** .

1. **Úvodní** stránka **nového Průvodce zátěžovým testem** je první stránka.

1. Zvolte **Další**.

### <a name="to-edit-settings-for-load-test-scenario"></a>Úprava nastavení pro scénář zátěžového testu

1. Do textového pole **Zadejte název pro scénář zátěžového testu** zadejte **ScenarioSample**.

     *Scénář* je mechanismus seskupení. Skládá se ze sady testů a vlastností pro spuštění těchto testů v rámci zátěže.

2. Nastavte **si časový profil** do úvahy `Use normal distribution centered on recorded think times` . Časy přemýšlení reprezentují čas, kdy by uživatel uvažoval webovou stránku, než začne pokračovat na další stránku.

1. Po dokončení klikněte na tlačítko **Další** .

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Úprava nastavení vzoru zatížení pro testovací scénář

1. Vyberte **Krok zatížení**.

    > [!NOTE]
    > Můžete vybrat ze dvou typů vzorů zatížení: konstanta a krok. Každý typ má svou funkci v testování zatížení, ale pro účely tohoto návodu vyberte **Krok zatížení**.

2. Nastavte **počet počátečních uživatelů** na 10 uživatelů.

3. Nastavte **dobu trvání kroku** na 10 sekund.

4. Nastavte **Krok počet uživatelů** na 10 uživatelů/krok.

5. Nastavte **maximální počet uživatelů** na 100 uživatelů.

6. Zvolte **Další**.

### <a name="to-select-test-mix-model-for-the-scenario"></a>Výběr modelu kombinace testů pro scénář

1. V části **jak má být kombinace testů modelována**, vyberte na **základě celkového počtu testů**.

2. Zvolte **Další**.

### <a name="to-add-unit-tests-to-the-scenario"></a>Přidání jednotkových testů do scénáře

1. Dalším krokem je **Přidat testy do scénáře zátěžového testu a upravit kombinaci testů**.

2. Zvolte možnost **Přidat** a vyberte testy.

3. Vyberte testy jednotek **CreditTest** uvedené v podokně **Dostupné testy** , které uvádí všechny testy výkonnosti webu a testy jednotek v projektu webového výkonu a zátěžového testu.

4. Vyberte šipku pro přidání testu jednotek **CreditTest** do podokna **vybrané testy** .

5. Zopakujte kroky 3 a 4 pro testy jednotek **DebitTest** a **FreezeAccountTest** .

6. Až dokončíte přidávání tří testů jednotek, klikněte na **tlačítko OK**.

     Zobrazí se kombinace testů.

7. Přesunutím posuvníku v oblasti **distribuce** pro **CreditTest** mírně napravo upravte distribuci testu. Všimněte si, že ostatní posuvníky se přesunou doleva automaticky, takže distribuce zůstane v 100%.

8. Zvolte **Další**.

### <a name="to-select-network-mix-for-test-scenario"></a>Výběr kombinace sítě pro testovací scénář

1. Vyberte typ připojení LAN, který chcete přidat k kombinaci šířky pásma sítě.

     Můžete přidat další typy sítě. Pro úpravu distribuce a vážení testů použijte posuvníky.

2. Zvolte **Další**.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Určení počítačů, které se mají monitorovat pomocí sad čítačů během běhu zátěžového testu

1. Zvolte **Další**.

     Další informace o sadách čítačů naleznete v tématu [Určení sad čítačů a mezních pravidel pro počítače v rámci zátěžového testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

### <a name="to-edit-run-setting-for-load-test"></a>Úprava nastavení spuštění pro zátěžový test

1. Vyberte **Doba trvání zátěžového testu** a pak nastavte dobu běhu na 2 minuty, *aby se zátěžový test* zátěžového testu **vypustil** .

     Při sestavování zátěžových testů je vhodné ověřit, zda je vše správně nakonfigurováno a spuštěno podle očekávání, spuštěním krátkého, světlého zátěžového testu. Tento proces se označuje jako *testování kouře*.

2. Klikněte na tlačítko **Dokončit**. Zátěžový test je otevřen v **Editor zátěžového testu**.

## <a name="run-the-load-test"></a>Spustit zátěžový test
 Po vytvoření zátěžového testu jej spusťte, chcete-li zobrazit, jak vaše bankovní aplikace reaguje na simulaci zatížení. I když je spuštěn zátěžový test, vidíte okno **analyzátor zátěžového testu** .

### <a name="to-run-the-load-test"></a>Spuštění zátěžového testu

1. S otevřeným zátěžovým testem v **Editor zátěžového testu** vyberte zelené tlačítko **Spustit test** na panelu nástrojů. Zátěžový test začne běžet.

2. Pokud vaše simulace testů překročí prahové hodnoty, zobrazí se v uzlech ovládacího prvku stromové struktury ikony, které označují porušení prahové hodnoty. Chyby mají překryv červeného kruhu, upozornění mají překryv žlutého trojúhelníku. Můžete najít čítač, který překročil prahovou hodnotu a graf přetáhnete přetažením ikony do grafu. To můžete provést, když je test spuštěn.

## <a name="see-also"></a>Viz také

- [Úprava poměru testů pro určení testů, které mají být zahrnuty do scénáře zátěžového testu](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Určení typů virtuálních sítí](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
- [Úprava vzorů zatížení pro modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Upravit modely kombinace textu za účelem určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
