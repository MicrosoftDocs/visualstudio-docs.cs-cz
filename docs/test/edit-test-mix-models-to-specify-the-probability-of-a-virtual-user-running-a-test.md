---
title: Úpravy modelů kombinací testů
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 62c817a2df6c56f70ab2217292feeb545cf66c85
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593210"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Úprava modelů poměru testů a určení pravděpodobnosti, že virtuální uživatel spustí test

*Model kombinace testů* určuje pravděpodobnost, že virtuální uživatel spustí daný test ve scénáři testu zatížení. To umožňuje simulovat zatížení více realisticky. Namísto toho, aby pouze jeden pracovní postup prostřednictvím aplikace, může mít několik pracovních postupů, což je užší jak koncoví uživatelé pracují s vašimi aplikacemi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-options"></a>Možnosti modelu kombinace testů

Můžete určit jednu z následujících možností model kombinace testů pro vašeho scénáře zkušebního zatížení:

- **Na základě celkového počtu testů:** Určuje, který webového výkonu nebo Jednotkový test se spustí, když virtuální uživatel spustí iteraci testu. Na konci zátěžového testu odpovídá počet případů, kdy byla spuštěna určitého testu rozdělení přiřazeného testu. Použijte tento model kombinace testů, pokud vytváříte poměru testů podílu transakcí v protokolu služby IIS nebo v údajích o produkci.

- **Na základě počtu virtuálních uživatelů:** Určuje procentuální podíl virtuálních uživatelů, kteří budou používat konkrétního webového výkonu nebo Jednotkový test. Kdykoli během zátěžového testu odpovídá počet uživatelů, kteří jsou spuštěn určitý test přiřazené distribuce. Použijte tento model kombinace testů, pokud vytváříte poměr testů na procento uživatelů, kteří spuštěn určitý test.

- **Založený na kroku uživatele:** v průběhu zátěžového testu je každý test webového výkonu nebo Jednotkový test spustit zadaný počet opakování za uživatele za hodinu. Použijte tento model kombinace testů, když potřebujete virtuálních uživatelů pro spuštění testu v určitém tempu zátěžového testu.

- **Na základě pořadí sekvenčního:** každý virtuální uživatel spouští testy webového výkonu nebo Jednotkový v pořadí, že testy jsou definovány ve scénáři. Virtuální uživatel pokračuje procházením testy v tomto pořadí, dokud není dokončen zátěžový test.

## <a name="tasks"></a>Tasks

|Tasks|Související témata|
|-|-----------------------|
|**Určení poměru testů pro zátěžový test:** při vytváření zátěžového testu, můžete zadat nastavení pro zátěžový test v **nového Průvodce zátěžovým testem**. V **Průvodce novým zátěžovým testem**, zvolte existující web a testy jednotek pro přidání do počáteční scénář. Po přidání testy do scénáře, určete kombinace testů pro scénář.<br /><br /> Pomocí možnosti modelování zatížení více přesně předpovědět očekávaného reálného využití webu nebo aplikace, které jsou zátěžové testování. Je důležité provést, protože zátěžový test, který není založen na modelu přesné zatížení lze generovat zavádějící výsledky.|-   [Emulovat očekávaného reálného využití webu nebo aplikace](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Upravit model kombinace testů:** do scénáře zátěžového testu pomocí jedné z modelů poměru testů můžete změnit **editoru zátěžového testu**.||
|**Konfigurace nemusely zpoždění pro model poměru testů tempem uživatele:** Pokud vašeho scénáře zkušebního zatížení je konfigurován pro použití **založený na kroku model kombinace testů uživatele**, můžete určit, jak chcete rozdělení zpoždění Pacing nakonfigurované.|-   [Postupy: použít rozdělení na zpoždění stimulace, když model kombinace testů se stimulací podle uživatele](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Změňte model kombinace testů ve scénáři

Po vytvoření zátěžového testu s použitím **nového Průvodce zátěžovým testem**, můžete použít **editoru zátěžového testu** Chcete-li změnit vlastnosti scénářů pro splnění potřebám a cílům testování.

> [!NOTE]
> Úplný seznam vlastností parametrů zatížení a jejich popis najdete v části [vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

Pomocí **editoru zátěžového testu**, model kombinace testů ve scénáři testu zatížení můžete změnit úpravou **typ kombinace testu** vlastnost **vlastnosti** okna.

### <a name="to-change-the-test-mix-model"></a>Chcete-li změnit model kombinace testů

1. Otevřete zátěžový test.

     **Editoru zátěžových testů** se zobrazí. Zobrazí se strom zátěžového testu.

2. V *scénáře* složky strom zátěžového testu, vyberte uzel scénář, pro kterou chcete určit maximální počet iterací testu.

3. Na **zobrazení** nabídce vyberte možnost **okno vlastností**.

     Jsou zobrazeny kategorie a vlastnosti scénáře.

4. V **typ kombinace testu** vlastnost, zvolte tlačítko se třemi tečkami ( **...** ).

     **Upravit kombinaci testů** se zobrazí dialogové okno.

5. Zvolte rozevírací seznam v části **model kombinace testů** a vyberte model kombinace testů, který chcete použít pro tento scénář.

6. (Volitelné) Úpravy poměru testů pomocí **přidat**, **odebrat** a **rozmístit** tlačítka a distribuce posuvníky. Další informace najdete v tématu [upravit poměr testů k určení, které testy mají být zahrnuty do scénáře zátěžového testu](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

7. (Volitelné) Zadejte webový test výkonu a jednotky k inicializaci nebo ukončit pomocí zaškrtávacích políček a výběrem požadované testy. Další informace najdete v tématu [Emulate očekávané využití z reálného světa webu nebo aplikaci](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md).

8. Vyberte **OK**.

     **Vlastnosti** okno zobrazuje nový model kombinace testů pro **typ kombinace testu** vlastnost.

9. Po změně vlastnosti zvolte **Uložit** na **souboru** nabídky. Potom můžete spustit zátěžový test pomocí nového **typ kombinace testu** hodnotu.

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
