---
title: Napodobování skutečného používání webových stránek pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18e22cd151d8013a50e34a01757069dde9574e79
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589601"
---
# <a name="test-mix-models-overview"></a>Přehled modelů testovacích mixů

Pomocí možností modelování zatížení můžete přesněji předpovědět očekávané reálné využití webu nebo aplikace, které testujete zatížení. Je to důležité, protože zátěžový test, který není založen na přesném modelu zatížení, může generovat zavádějící výsledky.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-enhancements"></a>Vylepšení modelu kombinace testů

Pomocí editoru zátěžového testu nebo průvodce modelem kombinace testů můžete zadat následující typy kombinace testů pro scénář zátěžového testu. Další informace naleznete [v tématu Změna modelu kombinace testů ve scénáři](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Můžete zadat jednu z následujících možností modelu kombinace testů pro scénář zátěžového testu:

- **Na základě celkového počtu testů:** Určuje, který webový výkon nebo testování částí je spuštěno, když virtuální uživatel spustí iteraci testu. Na konci zátěžového testu počet, kolikrát konkrétní test spustit uzavřeno přiřazené testovací distribuce. Tento model kombinace testů použijte, pokud zakládáte kombinaci testů na procentech transakcí v protokolu iis nebo v produkčních datech. Další informace naleznete v [tématu Procento na základě spuštěné testy](#BasedOnTestsStarted).

- **Na základě počtu virtuálních uživatelů:** Určuje procento virtuálních uživatelů, kteří budou spouštět konkrétní webový výkon nebo testování částí. V libovolném bodě zátěžového testu počet uživatelů, kteří jsou spuštěny konkrétní test odpovídá přiřazené distribuce. Tento model kombinace testů použijte, pokud zakládáte kombinaci testů na procentu uživatelů, kteří spouštějí určitý test. Další informace naleznete v [tématu Procento založené na virtuálních uživatelích](#PercentageBasedonVirtualUsers).

- **Na základě uživatelského tempa:** V průběhu zátěžového testu je každý test výkonu webu nebo test částí spuštěn zadaný počet časů na uživatele za hodinu. Tento model kombinace testů použijte, pokud chcete, aby virtuální uživatelé spouštěli test určitým tempem v průběhu zátěžového testu. Další informace naleznete v [tématu Pacing test mix](#PacingTestMix).

    > [!TIP]
    > Kdy si vyberete **kombinaci procent testů** a kdy zvolíte **Procento na základě virtuálních uživatelů**? Rozdíl mezi těmito dvěma možnostmi je důležité, pokud některé testy v kombinaci testů mají mnohem delší dobu trvání než jiné testy. V takovém případě byste měli pravděpodobně zvolit **procento na základě virtuálních uživatelů**. Tato volba pomáhá vyhnout se spuštění testu, při kterém se zvyšuje pravděpodobnost, že příliš mnoho uživatelů bude spouštět dlouhodobé testy. Pokud však všechny testy mají podobnou dobu trvání, můžete bezpečněji zvolit **kombinaci procent testů**.

- **Na základě sekvenčního pořadí:** Každý virtuální uživatel spustí webové testy výkonu nebo jednotkových testů v pořadí, v jakém jsou testy definovány ve scénáři. Virtuální uživatel pokračuje v procházení testy v tomto pořadí, dokud není dokončen zátěžový test. Další informace naleznete v tématu [Sekvenční pořadí](#SequentialOrder).

### <a name="percentage-based-on-tests-started"></a><a name="BasedOnTestsStarted"></a>Procento založené na zahájeném testu

Pro každý test v mixu můžete určit procento, které určuje, jak často je test vybrán jako další test ke spuštění. Třem testům můžete například přiřadit následující procentuální hodnoty:

- Testa (50 %)

- TestB (35 %)

- TestC (15 %)

Pokud použijete toto nastavení, další test, který chcete spustit, je založen na přiřazených procentech. Provést bez přihlédnutí k počtu virtuálních uživatelů, kteří jsou aktuálně spuštěny každý test.

### <a name="percentage-based-on-virtual-users"></a><a name="PercentageBasedonVirtualUsers"></a>Procento na základě virtuálních uživatelů
Tento model kombinace testů určuje procento virtuálních uživatelů, kteří spustí konkrétní test. Pokud použijete tento model kombinace testů, další test, který chcete spustit, je založen nejen na přiřazených procentech, ale také na procentu virtuálních uživatelů, kteří aktuálně spouštějí určitý test. V libovolném bodě zátěžového testu počet uživatelů, kteří jsou spuštěny konkrétní test odpovídá přiřazené distribuce co nejblíže.

### <a name="pacing-test-mix"></a><a name="PacingTestMix"></a>Pacing test mix

Pokud zadáte kombinaci testování tempo, nastavíte rychlost spuštění testu pro každého virtuálního uživatele pro každý test v kombinaci testů. Pro každý test je tato rychlost vyjádřena jako testy spustit na virtuálního uživatele za hodinu. Můžete například přiřadit následující kombinaci testů s postupem do provozu k následujícím testům:

- TestA: 4 testy na uživatele za hodinu

- TestB: 2 testy na uživatele za hodinu

- TestC: 0,125 testů na uživatele za hodinu

Pokud používáte model kombinace pacing test, modul runtime zátěžového testu zaručuje, že skutečná rychlost, jakou jsou testy spuštěny, je menší nebo rovna zadané rychlosti. Pokud testy spustit příliš dlouho pro přiřazené číslo, které mají být dokončeny, je vrácena chyba.

Nastavení **Think Time Between Test Iterací** se nepoužije při použití kombinace testu s cákání.

#### <a name="apply-distribution-to-pacing-delay"></a>Použití distribuce na zpoždění přecházení dat
Hodnotu **vlastnosti Apply Distribution to Pacing Delay** ve scénáři zátěžového testu lze nastavit na hodnotu true nebo false:

- **Pravda:** Scénář použije typická zpoždění statistické distribuce určená hodnotou ve sloupci **Testy na uživatele za hodinu** v dialogovém okně Upravit **kombinaci testů.** Další informace naleznete [v tématu Úprava modelů kombinace textu k určení pravděpodobnosti virtuálního uživatele, který spouštěl test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Předpokládejme například, že máte **testy na uživatele za hodinu** hodnotu v dialogovém okně Upravit test **mix** pro testovací sadu 2 uživatelé za hodinu. Pokud je vlastnost **Použít distribuci na zpoždění pacingu** nastavena na **hodnotu True**, použije se na čekací dobu mezi testy typické statistické rozdělení. Testy budou stále spuštěny 2 testy za hodinu, ale nemusí to být nutně 30 minut mezi nimi. První test by mohl běžet po 4 minutách a druhý test po 45 minutách.

- **False**: Testy budou spuštěny specifickým tempem, které jste zadali pro hodnotu ve sloupci **Testy na uživatele za hodinu** v dialogovém okně Upravit **kombinaci testů.** Další informace naleznete [v tématu Úprava modelů kombinace textu k určení pravděpodobnosti virtuálního uživatele, který spouštěl test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Předpokládejme například, že máte **testy na uživatele za hodinu** hodnotu v dialogovém okně Upravit test **mix** pro testovací sadu 2 uživatelé za hodinu. Pokud je vlastnost **Použít distribuci na zpoždění nastavena** na **hodnotu False**, v podstatě při spuštění testů neposkytujete žádný prostor. Test bude spuštěn každých 30 minut. Tím zajistíte, že provedete 2 testy za hodinu.

  Další informace naleznete v [tématu Postup: Použití distribuce na zpoždění při použití modelu mixu testů tempa uživatele](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).

### <a name="sequential-order"></a><a name="SequentialOrder"></a>Sekvenční pořadí
Výběrem možnosti Na základě pořadí sekvenčního testu způsobí, že každý virtuální uživatel spustí všechny testy ve scénáři v pořadí, ve které byly testy definovány.

## <a name="test-iterations-property"></a>Test iterací, vlastnost
Ve vlastnostech Spustit nastavení můžete zadat hodnotu vlastnosti Testovat iteraci. Tato hodnota je počet iterací testu spustit v zátěžovém testu. Po spuštění zadaného počtu iterací testu nebudou spuštěny žádné další iterace testů navzdory nastavení některého z profilů zatížení. Po dokončení zadaného počtu zkušebních iterací se zátěžový test ukončí. Další informace naleznete v [tématu Postup: Určení počtu iterací testu v nastavení spuštění](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="initialize-and-terminate-tests"></a>Inicializovat a ukončit testy
Můžete vybrat testy, které se mají spustit na začátku a na konci relace zátěžového testování každého virtuálního uživatele. Další informace naleznete [v tématu Úprava modelů kombinace textu k určení pravděpodobnosti virtuálního uživatele, který spouštěl test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

- **Inicializovat test**. Tento test je spuštěn každý virtuální uživatel před spuštěním některého z testů v kombinaci testů.

- **Ukončete test**. Tento test je spuštěn po spuštění všech testů pro konkrétního virtuálního uživatele.

  Vezměte prosím na vědomí následující o inicializovat test a ukončit test:

- Dobu trvání zátěžového testu můžete určit podle času namísto podle počtu iterace. V tomto případě po dokončení doby spuštění zátěžového testu nebude ukončený test spuštěn.

- Pokud je test inicializovat testování jednotky nebo test výkonu webu, stav TestContext nebo WebTestContext, objekt po dokončení testu inicializovat je uložen. Poté se použije jako počáteční kontext pro iterací testů v kombinaci testů.

- Noví uživatelé, jak je definováno ve vlastnosti scénáře Procento nových uživatelů, vždy svedou inicializovat test, jednu iteraci testu ze kombinace testů a test ukončení.

## <a name="see-also"></a>Viz také

- [Úprava modelů kombinace textu pro určení pravděpodobnosti spuštění testu virtuálním uživatelem](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Úprava vzorů zatížení pro modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Upravte kombinaci testů a určete, které testy mají být zahrnuty do scénáře zátěžového testu](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Konfigurace nastavení spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
- [Změna modelu kombinace testů ve scénáři](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
