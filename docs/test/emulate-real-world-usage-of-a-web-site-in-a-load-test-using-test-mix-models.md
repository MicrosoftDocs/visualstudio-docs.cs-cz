---
title: Emulace reálného využití webové stránky pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 33f44051025310072972ef3c15a1d4a4325c0efe
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896572"
---
# <a name="emulate-expected-real-world-usage-of-a-website-or-application-in-a-load-test-using-a-test-mix-model"></a>Emulovat očekávaného reálného využití webu nebo aplikace v rámci zátěžového testu pomocí modelu kombinace testů

Pomocí možnosti modelování zatížení více přesně předpovědět očekávaného reálného využití webu nebo aplikace, které jsou zátěžové testování. Je důležité provést, protože zátěžový test, který není založen na modelu přesné zatížení lze generovat zavádějící výsledky.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-enhancements"></a>Vylepšení model poměru testů

Pomocí editoru zátěžových testů nebo v Průvodci modelů poměru testů, můžete zadat následující typy poměru testů pro scénář testování zatížení. Další informace najdete v tématu [změnit model kombinace testů ve scénáři](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Můžete určit jednu z následujících možností model kombinace testů pro vašeho scénáře zkušebního zatížení:

-   **Na základě celkového počtu testů:** Určuje, který webového výkonu nebo Jednotkový test se spustí, když virtuální uživatel spustí iteraci testu. Na konci zátěžového testu odpovídá počet případů, kdy se spuštěním určitého testu rozdělení přiřazeného testu. Použijte tento model kombinace testů, pokud vytváříte poměru testů podílu transakcí v protokolu služby IIS nebo v údajích o produkci. Další informace najdete v tématu [procento podle spuštěných testů](#BasedOnTestsStarted).

-   **Na základě počtu virtuálních uživatelů:** Určuje procentuální podíl virtuálních uživatelů, kteří budou používat konkrétního webového výkonu nebo Jednotkový test. Kdykoli během zátěžového testu odpovídá počet uživatelů, kteří jsou spuštěn určitý test přiřazené distribuce. Použijte tento model kombinace testů, pokud vytváříte poměr testů na procento uživatelů, kteří jsou spuštěn určitý test. Další informace najdete v tématu [virtuálních uživatelů na základě procento](#PercentageBasedonVirtualUsers).

-   **Založený na kroku uživatele:** v průběhu zátěžového testu je každý test webového výkonu nebo Jednotkový test spustit zadaný počet opakování za uživatele za hodinu. Použijte tento model kombinace testů, když potřebujete virtuálních uživatelů pro spuštění testu v určitém tempu zátěžového testu. Další informace najdete v tématu [poměru testů Pacing](#PacingTestMix).

    > [!TIP]
    > Pokud zvolíte **procentuální poměr testů** a pokud zvolíte **virtuálních uživatelů na základě procento**? Rozdíl mezi tyto dvě možnosti je důležité, pokud některé testy v kombinaci testů mnohem delší dobu než jiné testy. V takovém případě byste měli pravděpodobně zvolit **virtuálních uživatelů na základě procento**. Tato volba pomáhá zabránit spuštění testu, ve které pravděpodobnost zvyšuje, že příliš mnoho uživatelů poběží testy dlouhé doby trvání. Nicméně pokud všechny testy mají podobné doby trvání, bezpečně můžete **procentuální poměr testů**.

-   **Na základě pořadí sekvenčního:** každý virtuální uživatel spouští testy webového výkonu nebo Jednotkový v pořadí, že testy jsou definovány ve scénáři. Virtuální uživatel pokračuje procházením testy v tomto pořadí, dokud není dokončen zátěžový test. Další informace najdete v tématu [pořadí](#SequentialOrder).

###  <a name="BasedOnTestsStarted"></a> Procento podle spuštěných testů
 Pro každý test v kombinaci můžete určit procento, která určuje, jak často testu jako další test vybrané ke spuštění. Například může přiřadit následující hodnoty procento tři testy:

- TestA (50%)

- TestB (35 %)

- TestC (15%)

  Pokud použijete toto nastavení, následující test spuštění je založená na přiřazené procenta. Můžete to provést bez ohledu na počet virtuálních uživatelů, kteří jsou aktuálně spuštěním každého testu.

###  <a name="PercentageBasedonVirtualUsers"></a> Procento podle virtuálních uživatelů
 Model poměru testů Určuje procentuální podíl virtuálních uživatelů, kteří se spuštěním určitého testu. Pokud používáte model kombinace testů, další test spustit je založena pouze na přiřazené procenta, ale také na procentuální podíl virtuálních uživatelů, kteří jsou aktuálně spuštěný určitý test. Kdykoli během zátěžového testu odpovídá počet uživatelů, kteří jsou spuštěn určitý test co nejpřesněji přiřazené distribuce.

###  <a name="PacingTestMix"></a> Interval poměru testů
 Pokud zadáte nemusely kombinace testů, nastavte počet spuštění testu pro jednotlivé virtuální uživatele pro každý test v kombinaci testů. Pro každý test je tato sazba vyjádřené jako testy spuštěny na virtuálního uživatele za hodinu. Například můžete přiřadit následující nemusely poměr testů na následující testy:

- TestA: 4 testů na uživatele za hodinu

- TestB: 2 testů na uživatele za hodinu

- TestC: 0,125 testů na uživatele za hodinu

  Pokud používáte nemusely model kombinace testů, modulu runtime testu zatížení zaručuje, že skutečné kurz, ve kterém jsou testy spouštěny je menší než nebo rovna hodnotě zadané frekvence. Pokud testy se spouštějí příliš dlouhý pro číslo přiřazené k dokončení, je vrácena chyba.

  **Myslíte, že doba mezi cykly testu** nastavení neplatí při použití nemusely poměru testů.

#### <a name="apply-distribution-to-pacing-delay"></a>Použít rozdělení na zpoždění stimulace
 Hodnota **použít rozdělení na zpoždění stimulace** ve scénáři testu zatížení může být nastavena na hodnotu true nebo false:

- **True**: Tento scénář bude platit statistické typické rozložení zpoždění určený hodnotou v **testů na uživatele za hodinu** sloupec v **upravit kombinaci testů** dialogového okna. Další informace najdete v tématu [úpravy modelů kombinací testů a určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Předpokládejme například, že máte **testů na uživatele za hodinu** hodnotu **upravit kombinaci testů** dialogové okno pro testovací nastavení pro 2 uživatele za hodinu. Pokud **použít rozdělení na zpoždění stimulace** je nastavena na **True**, typické statistické rozdělení se použije na čekací dobu mezi testy. Testy budou spuštěny stále 2 testů za hodinu, ale nemusí být nutně 30 minut mezi nimi. První test spustit až 4 minuty a druhý test za 45 minut.

- **False**: testy budou spuštěny konkrétní tempem, které jste zadali pro hodnotu v **testů na uživatele za hodinu** sloupec **upravit kombinaci testů** dialogového okna. Další informace najdete v tématu [úpravy modelů kombinací testů a určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Předpokládejme například, že máte **testů na uživatele za hodinu** hodnotu **upravit kombinaci testů** dialogové okno pro testovací nastavení pro 2 uživatele za hodinu. Pokud **použít rozdělení na zpoždění stimulace** je nastavena na **False**, v podstatě udělujete žádné volnost při spuštění testů. Test se spouští každých 30 minut. Tím je zajištěno, že spustíte 2 testů za hodinu.

  Další informace najdete v tématu [jak: použít rozdělení na zpoždění stimulace, když model kombinace testů se stimulací podle uživatele](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).

###  <a name="SequentialOrder"></a> Pořadí
 Výběr založený na možnost pořadí sekvenčního testu díky jednotlivé virtuální uživatele spouštět všechny testy ve scénáři v pořadí, že testy nebyly definovány.

## <a name="test-iterations-property"></a>Vlastnost iterace testu
 V dialogovém okně Vlastnosti parametrů běhu můžete zadat hodnotu pro vlastnost testovacích iterací. Tato hodnota je počet iterací testu ke spuštění v rámci zátěžového testu. Po spuštění zadaného počtu testovacích iterací, nespustí se žádné další test iterací bez ohledu na nastavení u všech profilů zatížení. Po dokončení počtu testovacích iterací zadán, ukončí zátěžového testu. Další informace najdete v tématu [postupy: určení počtu testovacích iterací v nastavení spuštění](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="initialize-and-terminate-tests"></a>Inicializační a ukončovací testy
 Můžete vybrat testy ke spuštění na začátek a konec jednotlivých virtuálních uživatelů pro zátěžové testování relace. Další informace najdete v tématu [úpravy modelů kombinací testů a určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

- **Inicializace testu**. Každý virtuální uživatel spouštění testu před spuštěním některý z testů v poměru testů.

- **Ukončit test**. Tento test běží po spuštění všech testů pro konkrétní virtuálních uživatelů.

  Mějte prosím na paměti následující skutečnosti související inicializační test a ukončovacího testu:

- Doba trvání zkušebního zatížení můžete určit podle času místo podle počtu iterací. V takovém případě po dokončení zátěžového testu, dobu trvání spuštění ukončovacího testu se nespustí.

- Je-li inicializovat test Jednotkový test nebo test výkonnosti webu, je uložen stav objektu TestContext nebo WebTestContext, po dokončení inicializace testu. Poté použije jako počáteční kontext pro iterace testů v poměru testů.

- Nové uživatele, jak je definováno ve vlastnosti scénář procento noví uživatelé, vždy spustit inicializační test, test z kombinace testů a ukončovacího testu jedné iterace.

## <a name="see-also"></a>Viz také:

- [Úpravy modelů kombinací testů a určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Úpravy vzorů zatížení pro model aktivity virtuálního uživatele](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Upravit poměr testů k určení, které testy mají být zahrnuty do scénáře zátěžového testu](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Konfigurace parametrů spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
- [Změňte model kombinace testů ve scénáři](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)