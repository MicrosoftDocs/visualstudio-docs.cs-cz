---
title: Vlastnosti scénáře zátěžového testu
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 65508c3a7594c0943b80fbbb898c62b0fc013557
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894596"
---
# <a name="load-test-scenario-properties"></a>Vlastnosti scénáře zátěžového testu

Změňte nastavení zátěžového testu scénář vlastnost v sadě Visual Studio k splňují vaše požadavky zátěžového testu. Tento článek uvádí různé vlastnosti scénáře zátěžového testu podle kategorie.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>Obecné

|Vlastnost|Definice|
|-|----------------|
|**Jméno**|Název scénáře|

## <a name="mix"></a>Kombinace

|Vlastnost|Definice|
|-|----------------|
|**Poměr prohlížečů**|Určuje kombinaci webových prohlížečů pro zátěžový test. Můžete určit typy různých webových prohlížečů a rozložení zátěže mezi nimi.<br /><br />Zvolte tři tečky **(...)**  tlačítko Otevřít **upravit poměr prohlížečů** dialogové okno a použijte **přidat** a **odebrat** a vyberte typy webových prohlížečů v zátěžovém testu.<br /><br />Další informace najdete v tématu [určení typů webových prohlížečů](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Poměr sítí**|Určuje kombinaci sítí pro zátěžový test. Můžete určit typy sítí, které chcete zahrnout, a rozložení zátěže mezi nimi.<br /><br />Zvolte tři tečky **(...)**  tlačítko Otevřít **upravit kombinaci sítí** dialogové okno a použijte **přidat** a **odebrat** a vyberte typy sítí v zátěžovém testu.<br /><br />Další informace najdete v tématu [určení typů virtuálních sítí](../test/specify-virtual-network-types-in-a-load-test-scenario.md).|
|**Poměr testů**|Určuje že poměr pro zátěžový test výkonnosti webu a jednotky testů. Můžete určit, které testy budou zahrnuty, a rozložení zátěže mezi nimi.<br /><br />Zvolte tři tečky **(...)**  tlačítko Otevřít **upravit kombinaci testů** dialogové okno a použijte **přidat** a **odebrat** vyberte testy v zátěžovém testu.<br /><br />Další informace najdete [upravit poměr testů pro scénář testování zatížení](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Typ poměru testů**|Určuje model kombinace testů pro zátěžový test.<br /><br />Zvolte tři tečky **(...)**  tlačítko Otevřít **upravit kombinaci testů** dialogové okno a pomocí rozevíracího seznamu v části **model kombinace testů** vyberte model kombinace testů pro použití v zátěžovém testu.<br /><br />Další informace najdete v tématu [úpravy modelů kombinací testů](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).|

## <a name="options"></a>Možnosti

|Vlastnost|Definice|
|-|----------------|
|**Agenti k použití**|Určuje, že testovací agenty, které má váš scénář použít, pokud používáte zatížení vzdáleně. Může být například potřeba určit konkrétní sadu agentů, aby byla při analýze trendů výkonu zachována konzistence. Agenty mohou být také geograficky rozmístěny tak, aby existovalo spřažení mezi spouštěnými skripty a umístěním agentu.<br /><br />Agenty musí být odděleny čárkami, například "**Agent1, Agent2, Agent3**". Je-li tato vlastnost ponechána prázdná, scénář bude používat všechny dostupné agenty.<br /><br />Další informace najdete v tématu [postupy: určení testovacích agentů](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md).|
|**Použít rozdělení na zpoždění stimulace**|Logická hodnota, která se používá k určení, zda chcete použít typické rozložení zpoždění stimulace model kombinace testů uživatele. Tato vlastnost platí jenom v případě, **typ kombinace testu** je nastavena na **založený na kroku uživatele**.<br /><br />Další informace najdete v tématu [jak: použít rozdělení na zpoždění stimulace](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|
|**Přepínání IP**|Logická hodnota, která se používá k určení, pokud bude použito přepínání IP.<br /><br />Přepínání protokolu IP umožňuje testovacího agenta k odesílání požadavků na server pomocí celé řady různých IP adresách. To simuluje volání, které pocházejí z různých klientských počítačů. Přepínání IP je důležité při testování proti load balanced webové farmy. Většina Vyrovnávání zatížení vytvoří spřažení mezi klientem a konkrétní webový server s použitím IP adresy klienta. Pokud všechny požadavky zdá, že pocházejí z jednoho klienta, nebude nástroj pro vyrovnávání zatížení vyrovnávat zatížení. K dosažení dobré rovnováhy zatížení ve webové farmě, je důležité, že požadavky pocházejí z rozsahu IP adres.<br /><br />Přepínání IP je k dispozici pouze u testovacího agentu.|
|**Maximální počet iterací testu**|Číselná hodnota, která určuje maximální počet testů, které budou spuštěny ve scénáři. Hodnota 0 neurčuje žádné maximum.<br /><br />Další informace najdete v tématu [konfigurace iterací testů ve scénářích](../test/configure-test-iterations-in-a-load-test-scenario.md).|
|**Procentuální podíl nových uživatelů**|Číselná hodnota určující procentuální podíl nových uživatelů nebo prvních návštěvníků ve scénáři.<br /><br />Další informace najdete v tématu [postupy: určení procentuální podíl virtuálních uživatelů, které používají data ve webové mezipaměti](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md).|
|**Profil uvažování**|Určuje, zda bude scénář používat **normální rozdělení**, nebo pokud je profil uvažování nastaven **na** nebo **vypnout**.<br /><br />Další informace najdete v tématu [zvažte úpravy časy pro simulaci prodlev při zásahem ze strany obsluhy webu](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="timing"></a>Časování

|Vlastnost|Definice|
|-|----------------|
|**Zpoždění spuštění**|Časová hodnota, která označuje, kolik hodin, minut a sekund bude trvat zpoždění spuštění po spuštění zátěžového testu. Pokud **zakázat při zahřívání** je nastavena na **True**, platí dobu čekání po dokončení doby zahřívání.<br /><br />Další informace najdete v tématu [konfigurace zpoždění pro spuštění scénáře](../test/configure-scenario-start-delays.md).|
|**Zakázat při zahřívání**|Logická hodnota, která se používá k určení, pokud by měly být spuštěny ve scénáři nebo neměl **zahřívání** nastavení běhu hodnota vlastnosti čas zadaný v zátěžovém testu.<br /><br />Další informace o nastavení vlastností zátěžového testu, naleznete v tématu [zátěžového testu spusťte nastavení](../test/load-test-run-settings-properties.md).<br /><br />Další informace najdete v tématu [konfigurace zpoždění pro spuštění scénáře](../test/configure-scenario-start-delays.md).|
|**Doba uvažování mezi iteracemi testu**|Číselná hodnota, která se používá k určení doby čekání v sekundách mezi iteracemi testu.<br /><br />Další informace najdete v tématu [zvažte úpravy časy pro simulaci prodlev při zásahem ze strany obsluhy webu](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)