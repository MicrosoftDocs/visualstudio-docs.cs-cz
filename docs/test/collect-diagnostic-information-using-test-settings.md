---
title: Shromažďování diagnostických informací pomocí nastavení testu
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14d98e34ef35efb1498d37071b2f53ef25bac4ad
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288855"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Shromažďování diagnostických informací pomocí nastavení testu

*Nastavení testů* v aplikaci Visual Studio můžete použít ke shromažďování dalších dat při spuštění testů. Například může být vhodné nahrávat video při spuštění testu. K dispozici jsou adaptéry diagnostických dat:

- Shromažďovat každý krok akce uživatelského rozhraní v textovém formátu

- Záznam každé akce uživatelského rozhraní pro přehrávání

- Shromažďování informací o systému

- Shromažďovat data protokolu událostí

- Shromažďovat data IntelliTrace, která vám pomůžou izolovat nereprodukovatelné chyby

Adaptéry diagnostických dat lze také použít ke změně chování testovacího počítače. Například s nastavením testu v aplikaci Visual Studio můžete emulovat různá kritická místa síťové topologie k vyhodnocení výkonu aplikace vašeho týmu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>Použití nastavení testu se sadou Visual Studio

Pro spuštění jednotky, kódovaného uživatelského rozhraní, výkonu webu nebo zátěžových testů pomocí sady Visual Studio můžete přidat, nakonfigurovat a vybrat nastavení testu, které chcete použít při spuštění testů. Chcete-li spustit testy, shromažďovat data nebo ovlivnit testovací počítač vzdáleně, je nutné zadat testovací kontrolér, který chcete použít v nastavení testu. Testovací kontrolér má agenty, které lze použít pro každou roli v nastavení testu.

## <a name="diagnostic-data-adapter-details"></a>Podrobnosti adaptéru diagnostických dat

Následující tabulka poskytuje přehled různých způsobů, jak se adaptéry diagnostických dat dají nakonfigurovat pro použití s rolemi místních nebo vzdálených počítačů.

|Adaptér diagnostických dat, který se používá v nastavení testu|Manuální testy v místním počítači|Automatizované testy|Manuální testy: shromažďování dat pomocí sady rolí a prostředí|Poznámky|
|-|-|-|-|-|
|**ASP.NET klientského proxy serveru pro IntelliTrace a dopad testu:** Tento proxy server umožňuje shromažďovat informace o voláních http z klienta na webový server pro adaptéry diagnostických dat IntelliTrace a test vlivu.|Ano|Ano|Ano|– Použijte tuto možnost pouze v případě, že jsou pro roli klienta vybrány adaptéry diagnostických dat IntelliTrace nebo test dopadu.|
|**Profiler ASP.NET:** Můžete vytvořit nastavení testu, které zahrnuje profilování ASP.NET, které shromažďuje údaje o výkonu pro webové aplikace v ASP.NET.|No|Ano (viz poznámky)|No|– Tento adaptér diagnostických dat je podporován pouze při spuštění zátěžových testů ze sady Visual Studio.|
|**Pokrytí kódu:** Můžete vytvořit nastavení testu, které obsahuje informace o pokrytí kódu, které slouží k prozkoumání toho, jak velká část kódu je pokryta testy.|No|Ano (viz poznámky)|No|– Pokrytí kódu lze použít pouze při spuštění automatizovaného testu ze sady Visual Studio nebo *mstest.exe*a pouze z počítače, na kterém je test spuštěn. Vzdálená kolekce není podporována.<br />– Shromažďování dat o pokrytí kódu nefunguje, pokud máte nastavení testu nakonfigurované na shromažďování informací IntelliTrace. **Poznámka:**  Tento adaptér diagnostických dat platí pouze pro nastavení testu sady Visual Studio. Nepoužívá se pro nastavení testu v Microsoft Test Manager (zastaralé v aplikaci Visual Studio 2017). Kromě toho je tento adaptér kompatibilní s projekty testů sady Visual Studio 2010. **Poznámka:**  Z důvodu kompatibility je pokrytí kódem použito při spuštění automatických testů z Microsoft Test Manager nebo na vzdáleném testovacím agentovi ze sady Visual Studio pomocí MSTest runneru.|
|**Protokol událostí:** Můžete nakonfigurovat nastavení testu tak, aby zahrnovalo shromažďování protokolů událostí, které je součástí výsledků testu.|Ano|Ano|Ano||
|**IntelliTrace:** Adaptér diagnostických dat pro *IntelliTrace* můžete nakonfigurovat tak, aby shromáždil konkrétní informace o trasování diagnostiky, které vám pomůžou izolovat chyby, které se obtížně reprodukovaly. Tím se vytvoří soubor IntelliTrace, který obsahuje tyto informace. Soubor IntelliTrace má příponu *. iTrace*. V případě neúspěchu testu můžete vytvořit chybu. Soubor IntelliTrace, který je uložen společně s výsledky testu, je automaticky propojen s touto chybou. Data shromažďovaná v souboru IntelliTrace zvyšují produktivitu ladění tím, že zkracuje dobu potřebnou k reprodukování a diagnostice chyby v kódu. Z tohoto souboru IntelliTrace je možné místní relaci simulovat na jiném počítači. Tím se snižuje riziko, že chyba není reprodukovatelná.|Ano|Ano|Ano|– Pokud povolíte shromažďování dat IntelliTrace, shromažďování dat o pokrytí kódu nefungují.<br />– Pokud používáte IntelliTrace pro roli webového klienta, je také nutné vybrat proxy klienta ASP.NET pro IntelliTrace a adaptér diagnostických dat dopadu testu.<br />-Podporovány jsou pouze následující verze služby IIS: IIS 7,0, IIS 7,5 a IIS 8,0.|
|**Emulace sítě:** Můžete určit, že chcete do testu umístit umělé zatížení sítě pomocí nastavení testu. Emulace sítě má vliv na komunikaci do a z počítače tím, že emuluje konkrétní rychlost síťového připojení, například telefonické připojení. |No|Ano (viz poznámky)|No|Adaptér diagnostických dat emulace sítě můžete použít pro roli klienta nebo serveru. Nemusíte používat adaptér na obou těchto rolích, které vzájemně komunikují. **Poznámka:**  Tento adaptér diagnostických dat platí pouze pro nastavení testu sady Visual Studio. Nepoužívá se pro nastavení testu v Microsoft Test Manager (zastaralé v aplikaci Visual Studio 2017). **Poznámka:**  K zvýšení rychlosti síťového připojení nelze použít emulaci sítě. **Upozornění:**  Pokud zahrnete adaptér diagnostických dat emulace sítě do nastavení testu a máte v úmyslu ho použít na místním počítači, je nutné také připojit ovladač emulace sítě k jednomu z síťových adaptérů vašeho počítače. Ovladač emulace sítě je vyžadován pro fungování adaptéru diagnostických dat síťové emulace. Ovladač emulace sítě je nainstalovaný a vázaný na adaptér dvěma způsoby: <ul><li>**Ovladač pro emulaci sítě nainstalovaný s Microsoft Visual Studio testovacího agenta:** Testovacího agenta sady Visual Studio lze použít na vzdálených počítačích i na místním počítači. Když nainstalujete testovacího agenta sady Visual Studio, proces instalace zahrnuje konfigurační krok, který váže ovladač emulace sítě k vaší síťové kartě. Další informace najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).</li><li>**Ovladač pro emulaci sítě nainstalovaný s Microsoft Visual Studio Test Professional:** Při prvním použití emulace sítě budete vyzváni k navázání ovladače emulace sítě na síťovou kartu.</li></ul> Ovladač emulace sítě můžete také nainstalovat z příkazového řádku na místním počítači bez instalace testovacího agenta sady Visual Studio pomocí následujícího příkazu: **VSTESTCONFIG NETWORKEMULATION/Install** **Upozornění:** adaptér emulace sítě je ignorován pomocí zátěžových testů. Místo toho testy zatížení používají nastavení, která jsou uvedena v síťové kombinaci scénáře zátěžového testu.|
|**Systémové informace:** Nastavení testu lze nastavit tak, aby obsahovalo systémové informace o počítači, na kterém je test spuštěn.|Ano|Ano|Ano||
|**Dopad testu:** Můžete shromažďovat informace o metodách kódu vaší aplikace, které byly použity při spuštění testovacího případu. To lze použít společně se změnami v kódu aplikace, které vývojáři udělali k určení, které testy byly ovlivněny změnami vývoje.|Ano|Ano|Ano|– Pokud shromažďujete data dopadu testu pro roli webového klienta, je také nutné vybrat proxy server klienta ASP.NET pro adaptér diagnostických dat IntelliTrace a dopad testu.<br />-Podporovány jsou pouze následující verze služby IIS: IIS 7,0, IIS 7,5 a IIS 8,0.|
|**Záznam videa:** Můžete vytvořit záznam videa relace plochy při spuštění testu. Video může pomáhat ostatním členům týmu izolovat problémy s aplikacemi, které se obtížně reprodukovaly.|Yes|Ano (viz poznámky)|Yes|– Pokud povolíte, aby byl software testovacího agenta spuštěn jako proces namísto služby, můžete vytvořit záznam videa při spuštění automatizovaných testů.|
