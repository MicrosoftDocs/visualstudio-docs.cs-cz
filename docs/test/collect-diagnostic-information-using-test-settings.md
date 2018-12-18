---
title: Shromažďování diagnostických údajů pomocí nastavení testů
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 288d1ce5511d33a48006c97030d2b9c2f12ec88c
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895207"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Shromažďování diagnostických údajů pomocí nastavení testů

Můžete použít *nastavení testu* v sadě Visual Studio ke sběru dat navíc při spuštění testů. Například můžete chtít vytvořit nahrávání při spuštění testu videa. Existují adaptéry diagnostických dat:

-   Shromažďovat každý krok akce uživatelského rozhraní v textovém formátu

-   Záznam každé akce uživatelského rozhraní pro přehrávání

-   Shromáždění systémových informací

-   Shromažďování dat protokolu událostí

-   Shromažďovat data IntelliTrace pro izolování nereprodukovatelných chyb

Adaptéry diagnostických dat lze také použít ke změně chování testovacího počítače. Test nastavení v sadě Visual Studio, například může emulovat různá problémová místa síťové topologie a vyhodnotit výkon aplikace vašeho týmu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>Použít nastavení testu pomocí sady Visual Studio

Ke spuštění jednotky, kódované UI, výkonu webu nebo zátěžového testu pomocí sady Visual Studio, můžete přidat, konfigurovat a vybrat nastavení testu pro použití při spuštění testů. Chcete-li spustit testy, shromažďovat data nebo ovlivnit testovací počítače vzdáleně, je nutné zadat testovací řadiče na použití ve vašem nastavení testu. Kontroler testů obsahuje agenty, které můžete použít pro každou roli v nastavení testu.

## <a name="diagnostic-data-adapter-details"></a>Podrobnosti o adaptéru diagnostických dat

Následující tabulka obsahuje přehled různých způsobů, že adaptéry diagnostických dat může být nakonfigurována pro použití s místním nebo vzdáleném počítači rolích.

|Adaptér diagnostických dat, který se používá v nastavení testu|Ruční testy v místním počítači|Automatizované testy|Ruční testy: Sběr dat s použitím sady rolí a prostředí|Poznámky|
|-|-|-|-|-|
|**Klient Proxy ASP.NET pro IntelliTrace a dopad testu:** tento server proxy umožňuje shromažďovat informace o voláních http z klienta na webový server pro adaptéry diagnostických dat IntelliTrace a dopad testu.|Ano|Ano|Ano|-Používejte pouze v případě, že adaptéry diagnostických dat IntelliTrace nebo dopad testu jsou vybrány pro roli klienta.|
|**Profiler technologie ASP.NET:** můžete vytvořit nastavení testu, které zahrnuje profilování technologie ASP.NET, které shromažďuje údaje o výkonu webových aplikací ASP.NET.|Ne|Ano (viz poznámky)|Ne|– Tento adaptér diagnostických dat je podporován pouze v případě spuštění zátěžových testů ze sady Visual Studio.|
|**Pokrytí kódu:** můžete vytvořit nastavení testu, který obsahuje informace o pokrytí kódu, který slouží k prověření, jak velká část kódu je pokryta testy.|Ne|Ano (viz poznámky)|Ne|– Můžete použít pokrytí kódu pouze při spuštění automatického testování z Visual Studia nebo *mstest.exe*a pouze z počítače, který spouští test. Vzdálený sběr není podporován.<br />– Shromažďování dat pokrytí kódu nebude fungovat, pokud máte nastavení testu nakonfigurováno shromažďování informací IntelliTrace. **Poznámka:** tento adaptér diagnostických dat platí pouze pro nastavení testu Visual Studio. Pro nastavení testu v nástroji Microsoft Test Manager se nepoužívá. Kromě toho tento adaptér je z důvodu kompatibility s testovacími projekty Visual Studio 2010. **Poznámka:** z důvodu kompatibility se pokrytí kódem uplatňuje při automatickém spuštění testů z nástroje Microsoft Test Manager nebo na vzdáleného testovacího agenta ze sady Visual Studio pomocí starší verze MSTest runner.|
|**Protokol událostí:** můžete nakonfigurovat tak, aby shromažďoval události protokolu, nastavení testu, který je zahrnut ve výsledcích testu.|Ano|Ano|Ano||
|**IntelliTrace:** můžete konfigurovat adaptér diagnostiky dat pro *IntelliTrace* shromažďovat informace o specifickém diagnostickém trasování a určit tak chyby, které je obtížné reprodukovat. Tím se vytvoří soubor IntelliTrace, který obsahuje tyto informace. Soubor IntelliTrace s příponou *.iTrace*. Pokud test selže, může vytvořit chybu. Soubor IntelliTrace, který je uložen s výsledky testu je automaticky přiřazen k této chybě. Data sbírána do souboru IntelliTrace zvyšují efektivitu ladění zkrácením doby potřebné k reprodukci a diagnostice chyby v kódu. Z tohoto IntelliTrace souboru místní relace může být Simulovaná v jiném počítači. Tím se snižuje riziko nereprodukovatelnosti chyby.|Ano|Ano|Ano|– Pokud povolíte shromažďování dat IntelliTrace, kolekce dat pokrytí kódu nefunguje.<br />– Pokud používáte nástroj IntelliTrace pro roli webového klienta, musíte také vybrat Proxy klienta ASP.NET pro adaptér diagnostických dat IntelliTrace a dopad testu.<br />– Jsou podporovány jenom následující verze služby IIS: IIS 7.0, IIS 7.5 a IIS 8.0.|
|**Emulace sítě:** můžete určit, že chcete ustaví testu umělé zatížení sítě s použitím nastavení testu. Emulace sítě ovlivňuje komunikaci do a z počítače emulací konkrétního síťového připojení s rychlostí, vytáčeného. |Ne|Ano (viz poznámky)|Ne|Adaptér diagnostických dat síťové emulace můžete použít pro roli klienta nebo serveru. Není nutné použít adaptér na obou těchto rolích, které mezi sebou komunikovat. **Poznámka:** tento adaptér diagnostických dat platí pouze pro nastavení testu Visual Studio. Pro nastavení testu v nástroji Microsoft Test Manager se nepoužívá. **Poznámka:** emulaci sítě nelze použít ke zvýšení rychlosti připojení k síti. **Upozornění:** Pokud zahrnete emulaci adaptéru diagnostických dat sítě v nastavení testu a máte v úmyslu použít na místním počítači, pak musíte také svázat ovladač emulace sítě do jednoho ze síťových adaptérů v počítači. Ovladač emulace sítě je vyžadován pro adaptér diagnostických dat síťové emulace na funkci. Ovladač emulace sítě je nainstalován a svázán k adaptéru dvěma způsoby: <ul><li>**Ovladač pro emulaci sítě nainstalovaný s Microsoft Visual Studio Test Agent:** The Visual Studio Test Agent lze použít na vzdálených počítačích a v místním počítači. Když instalujete Visual Studio Test Agent, instalační proces zahrnuje krok konfigurace, spojující ovladač emulace sítě se síťovou kartou. Další informace najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).</li><li>**Ovladač pro emulaci sítě nainstalovaný s Microsoft Visual Studio Test Professional:** při prvním použití emulace sítě, budete vyzváni k vytvoření vazby ovladač emulace sítě se síťovou kartou.</li></ul> Můžete také nainstalovat ovladač emulace sítě z příkazového řádku na místním počítači bez instalace testovacího agenta sady Visual Studio pomocí následujícího příkazu: **VSTestConfig NETWORKEMULATION/Install**  **Upozornění:** adaptér emulace sítě je testy zatížení ignorován. Místo toho zátěžové testy pomocí nastavení, které jsou určené v síťové skladbě scénáře testování zatížení.|
|**Informace o systému:** nastavení testu lze upravit na obsahovalo systémové informace o počítači, na kterém je test spuštěn.|Ano|Ano|Ano||
|**Testování vlivu:** můžete shromažďovat informace o metodách kódu aplikace byly použity při spuštění testovacího procesu. To je možné společně se změnami provedenými vývojáři k určení, jaké zkoušky byly ovlivněny změnami vývoje kódu aplikace.|Ano|Ano|Ano|– Pokud shromažďujete data dopadu testu pro roli webového klienta, musíte také vybrat Proxy klienta ASP.NET pro adaptér diagnostických dat IntelliTrace a dopad testu.<br />– Jsou podporovány jenom následující verze služby IIS: IIS 7.0, IIS 7.5 a IIS 8.0.|
|**Záznam videa:** můžete vytvořit záznam videa relace plochy při spuštění testu. Video může pomoci ostatním členům týmu izolovat problémy aplikací, které je obtížné reprodukovat.|Ano|Ano (viz poznámky)|Ano|– Pokud povolíte, aby software testovacího agenta ke spuštění jako proces místo jako služba, můžete vytvořit záznam videa při spuštění automatizovaných testů.|