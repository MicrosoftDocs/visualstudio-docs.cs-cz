---
title: Emulace reálného využití webu pro zátěžové testování
description: Použijte možnosti modelování zatížení k přesnější odhadu očekávaného reálného využití webu nebo aplikace, které provádíte při testování zátěže.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba5bba0b90acdfab932196ceda7dd8ad971efde1
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441258"
---
# <a name="test-mix-models-overview"></a>Přehled modelů kombinace testů

Možnosti zátěžového modelování můžete použít k přesnější předpovědi očekávaného reálného využití webu nebo aplikace, které zátěžové testování provádí. Je důležité to udělat, protože zátěžový test, který není založen na přesný model zatížení, může generovat zavádějící výsledky.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-enhancements"></a>Vylepšení modelu kombinace testů

Pomocí Editor zátěžového testu nebo průvodce modelem kombinace testů můžete zadat následující typy kombinace testů pro scénář zátěžového testu. Další informace najdete v tématu [Změna modelu kombinace testů ve scénáři](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Pro scénář zátěžového testu můžete zadat jednu z následujících možností modelu kombinace testů:

- **Na základě celkového počtu testů:** Určuje, který webový výkon nebo test jednotek se spustí, když virtuální uživatel spustí iteraci testu. Na konci zátěžového testu je počet, kolikrát se konkrétní testovací běh shodoval s přiřazenou distribucí testu. Tento model kombinace testů použijte, když vytváříte kombinaci testů v procentech transakcí v protokolu služby IIS nebo v provozních datech. Další informace naleznete v [procentech na základě spuštěných testů](#BasedOnTestsStarted).

- **Na základě počtu virtuálních uživatelů:** Určuje procentuální podíl virtuálních uživatelů, kteří spustí určitý webový výkon nebo test jednotky. V jakémkoli bodě zátěžového testu odpovídá počet uživatelů, kteří spouštějí určitý test, přiřazenému rozdělení. Tento model kombinace testů použijte, když vytváříte kombinaci testů na procentu uživatelů, kteří spouštějí určitý test. Další informace najdete v [procentech na základě virtuálních uživatelů](#PercentageBasedonVirtualUsers).

- **Podle tempa uživatele:** V průběhu zátěžového testu každý test výkonnosti webu nebo test jednotky spustí určitý počet opakování na uživatele za hodinu. Tento model kombinace testů použijte, pokud chcete, aby virtuální uživatelé spouštěli test s použitím určitého tempa v průběhu zátěžového testu. Další informace najdete v tématu [stimulace test směs](#PacingTestMix).

    > [!TIP]
    > Když zvolíte **procentuální poměr testů** a když zvolíte **procento na základě virtuálních uživatelů**? Rozdíl mezi těmito dvěma možnostmi je důležitý, pokud některé testy v poměru testů mají mnohem delší dobu než jiné testy. V takové situaci byste pravděpodobně zvolili **procento na základě virtuálních uživatelů**. Tato volba pomáhá předejít testovacímu běhu, ve kterém pravděpodobnost zvyšuje, že příliš mnoho uživatelů bude spouštět testy s dlouhou dobou trvání. Pokud ale všechny testy mají podobnou dobu trvání, můžete bezpečněji vybrat **procentuální poměr testů**.

- **Na základě sekvenčního pořadí:** Každý virtuální uživatel spouští testy webového výkonu nebo jednotek v pořadí, ve kterém jsou testy definovány ve scénáři. Virtuální uživatel pokračuje v provádění testů v tomto pořadí, dokud není dokončen zátěžový test. Další informace najdete v tématu [sekvenční pořadí](#SequentialOrder).

### <a name="percentage-based-on-tests-started"></a><a name="BasedOnTestsStarted"></a> Procento na základě spuštěných testů

Pro každý test v kombinaci můžete zadat procento, které určuje, jak často je test vybrán jako další test ke spuštění. Například můžete přiřadit následující procentuální hodnoty k třem testům:

- TestA (50%)

- TestB (35%)

- TestC (15%)

Pokud použijete toto nastavení, další test ke spuštění vychází z přiřazených procent. Provedete to bez nutnosti brát v úvahu počet virtuálních uživatelů, kteří aktuálně spouštějí každý test.

### <a name="percentage-based-on-virtual-users"></a><a name="PercentageBasedonVirtualUsers"></a> Procento na základě virtuálních uživatelů
Tento model kombinace testů Určuje procentuální podíl virtuálních uživatelů, kteří spustí určitý test. Použijete-li tento model kombinace testů, je další test ke spuštění založen nejen na přiřazených procentech, ale také na procentu virtuálních uživatelů, kteří aktuálně spouštějí určitý test. V jakémkoli bodě zátěžového testu odpovídá počet uživatelů, kteří spouštějí určitý test, co nejblíže k přidělenému rozdělení.

### <a name="pacing-test-mix"></a><a name="PacingTestMix"></a> Kombinace testů stimulace

Pokud zadáte kombinaci testů stimulace, nastavíte míru provádění testů pro každého virtuálního uživatele pro každý test v kombinaci testů. Pro každý test se tato frekvence vyjádří jako testy spouštěné za virtuální uživatele za hodinu. Například můžete přiřadit následující testy stimulace testů:

- TestA: 4 testy na uživatele za hodinu

- TestB: 2 testy na uživatele za hodinu

- TestC: 0,125 testů na uživatele za hodinu

Použijete-li model kombinace testů stimulace, modul runtime zátěžového testu zaručuje, že skutečná rychlost, kterou jsou testy spuštěny, je menší než nebo rovna zadané sazbě. Pokud testy běžely příliš dlouho na dokončení přiřazeného čísla, je vrácena chyba.

V případě, že používáte kombinaci testů stimulace, neplatí **čas pomýšlení mezi nastavením iterací testu** .

#### <a name="apply-distribution-to-pacing-delay"></a>Použít distribuci na zpoždění stimulace
V případě scénáře zátěžového testu může být hodnota vlastnosti **použít rozdělení na stimulace zpoždění** nastavena na hodnotu true nebo false:

- **True**: scénář bude uplatňovat typickou prodlevu statistické distribuce zadanou hodnotou ve sloupci testy na **uživatele za hodinu** v dialogovém okně **Upravit kombinaci testů** . Další informace najdete v tématu [Úpravy modelů kombinace textu a určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Předpokládejme například, že máte **testy na hodnotu uživatele za hodinu** v dialogovém okně **Upravit kombinaci testů** pro test nastavený na 2 uživatele za hodinu. Pokud je vlastnost **použít distribuci na stimulace Delay** nastavená na **hodnotu true**, použije se pro dobu čekání mezi testy typická statistická distribuce. Testy budou pořád spouštět 2 testy za hodinu, ale nemusí to být nutně 30 minut. První test může běžet po 4 minutách a druhý test po 45 minutách.

- **False**: testy se spustí s konkrétním tempem, které jste zadali pro hodnotu ve sloupci **testy na uživatele za hodinu** v dialogovém okně **Upravit kombinaci testů** . Další informace najdete v tématu [Úpravy modelů kombinace textu a určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Předpokládejme například, že máte **testy na hodnotu uživatele za hodinu** v dialogovém okně **Upravit kombinaci testů** pro test nastavený na 2 uživatele za hodinu. Pokud je vlastnost **použít distribuci na stimulace zpoždění** nastavená na **hodnotu false**, nebudete při spuštění testů v podstatě poskytovat žádné Leeway. Test se spustí každých 30 minut. Tím zajistíte, že spustíte 2 testy za hodinu.

  Další informace najdete v tématu [Postupy: použití distribuce na zpoždění stimulace při použití modelu kombinace testů pro uživatele tempa](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).

### <a name="sequential-order"></a><a name="SequentialOrder"></a> Sekvenční pořadí
Když vyberete možnost pořadí sekvenčního testování, každý virtuální uživatel spustí všechny testy ve scénáři v pořadí, v jakém byly testy definovány.

## <a name="test-iterations-property"></a>Vlastnost iterací testu
Ve vlastnostech parametrů běhu můžete zadat hodnotu vlastnosti iterace testu. Tato hodnota je počet iterací testu, které mají být spuštěny v rámci zátěžového testu. Po spuštění zadaného počtu testovacích iterací se žádné další iterace testu nespustí navzdory nastavení žádného z profilů zatížení. Po dokončení zadaného počtu testovacích iterací skončí zátěžový test. Další informace naleznete v tématu [How to: zadejte počet testovacích iterací v nastavení spuštění](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="initialize-and-terminate-tests"></a>Inicializovat a ukončit testy
Můžete vybrat testy, které se mají spustit na začátku a konci relace zátěžového testování virtuálních uživatelů. Další informace najdete v tématu [Úpravy modelů kombinace textu a určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

- **Inicializovat test**. Tento test spouští každý virtuální uživatel před spuštěním kteréhokoli z testů v kombinaci testů.

- **Ukončete test**. Tento test se spustí po spuštění všech testů pro konkrétního virtuálního uživatele.

  Upozorňujeme prosím na následující informace o inicializaci testu a ukončení testu:

- Můžete určit dobu trvání zátěžového testu podle času, nikoli podle počtu iterací. V tomto případě, když je dokončená doba běhu zátěžového testu, test ukončení se nespustí.

- Pokud je inicializací testu jednotkovým testem nebo testem výkonnosti webu, je uložen stav TestContext nebo WebTestContext objektu po dokončení inicializačního testu. Pak bude použit jako počáteční kontext pro iterace testů v kombinaci testů.

- Noví uživatelé, jak je definováno v procentech vlastnosti scénáře pro nové uživatele, vždy spustí inicializační test, jednu iteraci testu z kombinace testů a test ukončení.

## <a name="see-also"></a>Viz také

- [Upravit modely kombinace textu za účelem určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Úprava vzorů zatížení pro modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Úprava poměru testů pro určení testů, které mají být zahrnuty do scénáře zátěžového testu](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Konfigurovat nastavení běhu zátěžového testu](../test/configure-load-test-run-settings.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
- [Změna modelu kombinace testů ve scénáři](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
