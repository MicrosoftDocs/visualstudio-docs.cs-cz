---
title: Vlastnosti scénáře zátěžového testu
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2011438f1fcb0230cde0de527216456553e7c64
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584436"
---
# <a name="load-test-scenario-properties"></a>Vlastnosti scénáře zátěžového testu

Změňte nastavení vlastnosti scénáře zátěžového testu v sadě Visual Studio tak, aby splňovala požadavky na zátěžové testování. Tento článek uvádí různé vlastnosti scénáře zátěžového testu podle kategorie.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>Obecné

|Vlastnost|Definice|
|-|----------------|
|**Název**|Název scénáře|

## <a name="mix"></a>Kombinace

|Vlastnost|Definice|
|-|----------------|
|**Mix prohlížeče**|Určuje kombinaci webového prohlížeče pro zátěžový test. Můžete určit různé typy webových prohlížečů a jejich rozložení zatížení.<br /><br />Zvolte tlačítko tři tečky **(...)** pro otevření dialogového okna **Upravit kombinaci prohlížeče** a pomocí příkazu **Přidat** a **odebrat** vyberte typy webových prohlížečů v zátěžovém testu.<br /><br />Další informace naleznete [v tématu Specify web browsers types](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Síťový mix**|Určuje kombinaci sítí pro zátěžový test. Můžete určit typy sítí, které chcete zahrnout, a rozložení zátěže mezi nimi.<br /><br />Zvolte tlačítko tři tečky **(...)** pro otevření dialogového okna **Upravit síťový mix** a pomocí příkazu **Přidat** a **odebrat** vyberte typy sítí v zátěžovém testu.<br /><br />Další informace naleznete v [tématu Specify virtual network types](../test/specify-virtual-network-types-in-a-load-test-scenario.md).|
|**Testovací směs**|Určuje kombinaci výkonu webu a testování částí pro zátěžový test. Můžete určit, které testy budou zahrnuty, a rozložení zátěže mezi nimi.<br /><br />Zvolte tlačítko tři tečky **(...)** pro otevření dialogového okna **Upravit kombinaci testů** a pomocí příkazu **Přidat** a **odebrat** vyberte testy v zátěžovém testu.<br /><br />Další [informace, upravit kombinaci testů pro scénář zátěžového testu](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Typ kombinace testů**|Určuje model kombinace testů pro zátěžový test.<br /><br />Zvolte tlačítko tři tečky **(...)** pro otevření dialogového okna **Upravit kombinaci testů** a pomocí rozevíracího pole v části **Model kombinace testů** vyberte model kombinace testů, který se má použít v zátěžovém testu.<br /><br />Další informace naleznete v tématu [Úprava modelů mixů textu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).|

## <a name="options"></a>Možnosti

|Vlastnost|Definice|
|-|----------------|
|**Agenti k použití**|Určuje agenty, které má váš scénář použít, pokud vzdáleně spouštěte zátěžový test. Může být například potřeba určit konkrétní sadu agentů, aby byla při analýze trendů výkonu zachována konzistence. Agenty mohou být také geograficky rozmístěny tak, aby existovalo spřažení mezi spouštěnými skripty a umístěním agentu.<br /><br />Agenti musí být odděleni čárkami, například**Agent1, Agent2, Agent3**.. Je-li tato vlastnost ponechána prázdná, scénář bude používat všechny dostupné agenty.<br /><br />Další informace naleznete v [tématu How to: Specify test agents to use](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md).|
|**Použít distribuci na zpoždění přecházení dat**|Logická hodnota, která se používá k určení, pokud chcete použít typické distribuční zpoždění v modelu kombinace testů uživatele. Tato vlastnost platí pouze v případě, že je vlastnost **Test Mix Type** **nastavena na základě uživatelského tempa**.<br /><br />Další informace naleznete v [tématu Jak: Použití distribuce na zpoždění přecházení](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|
|**Přepínání IP adres**|Logická hodnota, která se používá k určení, zda se používá přepínání IP adres.<br /><br />Přepínání IP umožňuje testovacímu agentovi odesílat požadavky na server pomocí řady různých adres IP. To simuluje volání, které pocházejí z různých klientských počítačů. Přepínání IP je důležité při testování proti webové farmě s vyrovnáváním zatížení. Většina vykladačů zatížení vytvořit spřažení mezi klientem a konkrétní webový server pomocí IP adresy klienta. Pokud všechny požadavky vypadají, jako by pocházely z jednoho klienta, nevyvažovač zatížení nevyvažuje zatížení. Chcete-li získat správné vyrovnávání zatížení ve webové farmě, je důležité, aby požadavky pocházejí z řady IP adres.<br /><br />Přepínání IP je k dispozici pouze u testovacího agentu.|
|**Maximální test iterace**|Číselná hodnota, která určuje maximální počet testů, které budou spuštěny ve scénáři. Hodnota 0 neurčuje žádné maximum.<br /><br />Další informace naleznete v [tématu Konfigurace iterací testů pro scénáře](../test/configure-test-iterations-in-a-load-test-scenario.md).|
|**Procento nových uživatelů**|Číselná hodnota určující procentuální podíl nových uživatelů nebo prvních návštěvníků ve scénáři.<br /><br />Další informace naleznete v [tématu Postup: Určení procenta virtuálních uživatelů, kteří používají data webové mezipaměti](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md).|
|**Think Profil**|Určuje, zda bude scénář používat **normální distribuci**nebo zda je profil think **zapnuto** nebo **vypnuto**.<br /><br />Další informace naleznete v [tématu Úprava doby přemýšlení pro simulaci zpoždění interakce s lidmi na webu](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="timing"></a>Časování

|Vlastnost|Definice|
|-|----------------|
|**Zpoždění počátečního času**|Časová hodnota, která označuje, kolik hodin, minut a sekund bude trvat zpoždění spuštění po spuštění zátěžového testu. Pokud **zakázat během zahřívání** vlastnost je nastavena na **True**, množství času čekání platí po dokončení období zahřívání.<br /><br />Další informace naleznete v [tématu Konfigurace zpoždění spuštění scénáře](../test/configure-scenario-start-delays.md).|
|**Zakázat během zahřívání**|Logická hodnota, která se používá k určení, zda má být scénář spuštěn nebo ne během hodnoty času trvání **zahřívání** zadaný v nastavení spuštění zátěžového testu.<br /><br />Další informace o vlastnostech nastavení spuštění zátěžového testu naleznete v [tématu Načtení vlastností nastavení spuštění testu](../test/load-test-run-settings-properties.md).<br /><br />Další informace naleznete v [tématu Konfigurace zpoždění spuštění scénáře](../test/configure-scenario-start-delays.md).|
|**Myslete na časy mezi iteracemi testů**|Číselná hodnota, která se používá k určení doby čekání v sekundách mezi iteracemi testu.<br /><br />Další informace naleznete v [tématu Úprava doby přemýšlení pro simulaci zpoždění interakce s lidmi na webu](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
