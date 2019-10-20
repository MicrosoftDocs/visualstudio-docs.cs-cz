---
title: Vlastnosti scénáře zátěžového testu
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 54159ca7b0d99e0bba7e7b048138ffacf6ab5b0b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652957"
---
# <a name="load-test-scenario-properties"></a>Vlastnosti scénáře zátěžového testu

Změňte nastavení vlastnosti scénáře zátěžového testu v aplikaci Visual Studio tak, aby splňovalo požadavky na zátěžové testování. Tento článek obsahuje seznam různých vlastností scénáře zátěžového testu podle kategorie.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>Obecné

|Vlastnost|Definice|
|-|----------------|
|**Jméno**|Název scénáře|

## <a name="mix"></a>Kombinace

|Vlastnost|Definice|
|-|----------------|
|**Kombinace prohlížečů**|Určuje kombinaci webového prohlížeče pro zátěžový test. Můžete určit různé typy webových prohlížečů a jejich distribuci zatížení.<br /><br />Kliknutím na tlačítko se třemi tečkami **(...)** otevřete dialogové okno **Upravit kombinaci prohlížečů** a pomocí možnosti **Přidat** a **Odebrat** vyberte typy webových prohlížečů v rámci zátěžového testu.<br /><br />Další informace najdete v tématu [Určení typů webových prohlížečů](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Kombinace sítě**|Určuje kombinaci sítí pro zátěžový test. Můžete určit typy sítí, které chcete zahrnout, a rozložení zátěže mezi nimi.<br /><br />Kliknutím na tlačítko se třemi tečkami **(...)** otevřete dialogové okno **Upravit kombinaci sítí** a pomocí možnosti **Přidat** a **Odebrat** vyberte typy sítě v rámci zátěžového testu.<br /><br />Další informace najdete v tématu [Určení typů virtuálních sítí](../test/specify-virtual-network-types-in-a-load-test-scenario.md).|
|**Kombinace testů**|Určuje kombinaci webového výkonu a testu jednotek pro zátěžový test. Můžete určit, které testy budou zahrnuty, a rozložení zátěže mezi nimi.<br /><br />Kliknutím na tlačítko se třemi tečkami **(...)** otevřete dialogové okno **Upravit kombinaci testů** a pomocí možnosti **Přidat** a **Odebrat** můžete vybrat testy v zátěžovém testu.<br /><br />Další informace najdete [v části kombinace testů pro scénář zátěžového testu](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Typ kombinace testů**|Určuje model kombinace testů pro zátěžový test.<br /><br />Kliknutím na tlačítko se třemi tečkami **(...)** otevřete dialogové okno **Upravit kombinaci testů** a pomocí rozevíracího seznamu pod položkou **model kombinace testů** vyberte model poměru testů, který chcete použít v zátěžovém testu.<br /><br />Další informace najdete v tématu [Úprava modelů kombinace textu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).|

## <a name="options"></a>Možnosti

|Vlastnost|Definice|
|-|----------------|
|**Agenti k použití**|Určuje agenty, které mají být použity při vzdáleném spuštění testu zatížení. Může být například potřeba určit konkrétní sadu agentů, aby byla při analýze trendů výkonu zachována konzistence. Agenty mohou být také geograficky rozmístěny tak, aby existovalo spřažení mezi spouštěnými skripty a umístěním agentu.<br /><br />Agenty musí být odděleny čárkami, například "**obdrží agent1, obdrží Agent2, obdrží Agent3**". Je-li tato vlastnost ponechána prázdná, scénář bude používat všechny dostupné agenty.<br /><br />Další informace najdete v tématu [Postupy: Určení testovacích agentů, které se mají použít](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md).|
|**Použít distribuci na zpoždění stimulace**|Logická hodnota, která se používá k určení, jestli chcete použít typickou prodlevu distribuce v modelu kombinace testů stimulace uživatele. Tato vlastnost se vztahuje pouze v případě, že vlastnost typ poměru **testů** je nastavena na hodnotu **podle tempa uživatele**.<br /><br />Další informace najdete v tématu [Postupy: použití distribuce na zpoždění stimulace](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|
|**Přepínání IP**|Logická hodnota, která se používá k určení, jestli se používá přepínání IP<br /><br />Přepínání IP umožňuje testovacímu agentovi odesílat požadavky na server pomocí rozsahu různých IP adres. To simuluje volání, která pocházejí z různých klientských počítačů. Přepínání IP je důležité při testování na webové farmě s vyrovnáváním zatížení. Většina nástrojů pro vyrovnávání zatížení vytváří spřažení mezi klientem a konkrétním webovým serverem pomocí IP adresy klienta. Pokud se všechny požadavky zdají vypadat jako z jednoho klienta, nástroj pro vyrovnávání zatížení nebude zatížení vyrovnávat. Aby bylo možné dosáhnout správného vyrovnávání zatížení ve webové farmě, je důležité, aby požadavky pocházejí z rozsahu IP adres.<br /><br />Přepínání IP je k dispozici pouze u testovacího agentu.|
|**Maximální počet iterací testu**|Číselná hodnota, která určuje maximální počet testů, které budou spuštěny ve scénáři. Hodnota 0 neurčuje žádné maximum.<br /><br />Další informace najdete v tématu [Konfigurace iterací testů pro scénáře](../test/configure-test-iterations-in-a-load-test-scenario.md).|
|**Procento nových uživatelů**|Číselná hodnota určující procentuální podíl nových uživatelů nebo prvních návštěvníků ve scénáři.<br /><br />Další informace naleznete v tématu [How to: zadejte procento virtuálních uživatelů, kteří používají data mezipaměti webu](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md).|
|**Profil považovat za**|Určuje, jestli bude scénář používat **Normální distribuci**, nebo jestli je profil pro pomýšlení **zapnutý** nebo **vypnutý**.<br /><br />Další informace najdete v tématu [úpravy časů pomýšlení pro simulaci zpoždění lidské interakce webu](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="timing"></a>Okamžiku

|Vlastnost|Definice|
|-|----------------|
|**Čas spuštění zpoždění**|Časová hodnota, která označuje, kolik hodin, minut a sekund bude trvat zpoždění spuštění po spuštění zátěžového testu. Pokud je vlastnost **Zakázat během zahřívání** nastavená na **hodnotu true**, použije se doba čekání po dokončení zahřívání.<br /><br />Další informace najdete v tématu [Konfigurace zpoždění spouštění scénářů](../test/configure-scenario-start-delays.md).|
|**Zakázat během zahřívání**|Logická hodnota, která se používá k určení, jestli se má scénář spustit, nebo ne během hodnoty doby **Trvání zahřívání** v nastavení běhu zátěžového testu.<br /><br />Další informace o vlastnostech nastavení běhu zátěžového testu naleznete v tématu [Vlastnosti nastavení běhu zátěžového testu](../test/load-test-run-settings-properties.md).<br /><br />Další informace najdete v tématu [Konfigurace zpoždění spouštění scénářů](../test/configure-scenario-start-delays.md).|
|**Časy přemýšlení mezi testovacími iteracemi**|Číselná hodnota, která se používá k určení doby čekání v sekundách mezi iteracemi testu.<br /><br />Další informace najdete v tématu [úpravy časů pomýšlení pro simulaci zpoždění lidské interakce webu](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="see-also"></a>Viz také:

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)