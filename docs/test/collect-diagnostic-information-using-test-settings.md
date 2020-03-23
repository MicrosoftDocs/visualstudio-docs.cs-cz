---
title: Shromažďování diagnostických informací pomocí nastavení testu
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bf82ee72d4398095f25de2493c28c5155456b55
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588860"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Shromažďování diagnostických informací pomocí nastavení testu

*Nastavení testu* v sadě Visual Studio můžete použít ke shromažďování dalších dat při spuštění testů. Můžete například chtít provést záznam videa při spuštění testu. Existují adaptéry diagnostických dat, které:

- Shromáždit každý krok akce ui v textovém formátu

- Zaznamenat každou akci ui pro přehrávání

- Shromažďovat systémové informace

- Shromažďování dat protokolu událostí

- Shromažďování dat IntelliTrace, které pomáhají izolovat nereprodukovatelné chyby

Adaptéry diagnostických dat lze také použít ke změně chování testovacího počítače. Například s nastavením testu v sadě Visual Studio můžete emulovat různá kritická místa topologie sítě k vyhodnocení výkonu aplikace vašeho týmu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>Použití nastavení testu v sadě Visual Studio

Chcete-li spustit jednotku, kódované uživatelské rozhraní, výkon webu nebo zátěžové testy pomocí sady Visual Studio, můžete přidat, nakonfigurovat a vybrat nastavení testu, které se má použít při spuštění testů. Chcete-li spustit testy, shromažďovat data nebo vzdáleně ovlivnit testovací počítač, je nutné zadat testovací řadič, který se použije v nastavení testu. Testovací řadič má agenty, které lze použít pro každou roli v nastavení testu.

## <a name="diagnostic-data-adapter-details"></a>Podrobnosti o adaptéru diagnostických dat

Následující tabulka obsahuje přehled různých způsobů, jak lze adaptéry diagnostických dat nakonfigurovat pro použití s místními nebo vzdálenými rolemi počítače.

|Adaptér diagnostických dat, který se používá v nastavení testu|Ruční testy na místním počítači|Automatizované testy|Ruční testy: Shromažďování dat pomocí sady rolí a prostředí|Poznámky|
|-|-|-|-|-|
|**ASP.NET proxy klienta pro IntelliTrace a dopad testu:** Tento proxy server umožňuje shromažďovat informace o volání http z klienta na webový server pro adaptéry diagnostických dat IntelliTrace a Test Impact.|Ano|Ano|Ano|- Tuto možnost použijte pouze v případě, že jsou pro roli klienta vybrány adaptéry diagnostických dat IntelliTrace nebo Test Impact.|
|**ASP.NET profiler:** Můžete vytvořit testovací nastavení, které zahrnuje ASP.NET profilování, které shromažďuje údaje o výkonu ASP.NET webových aplikací.|Ne|Ano (viz poznámky)|Ne|- Tento adaptér diagnostických dat je podporován pouze při spuštění zátěžových testů z sady Visual Studio.|
|**Pokrytí kódu:** Můžete vytvořit nastavení testu, které obsahuje informace o pokrytí kódu, které se používá k prozkoumání, kolik kódu je pokryto testy.|Ne|Ano (viz poznámky)|Ne|- Pokrytí kódu můžete použít pouze při spuštění automatizovaného testu z sady Visual Studio nebo *mstest.exe*a pouze ze zařízení, které spustí test. Vzdálená kolekce není podporována.<br />- Shromažďování dat pokrytí kódu nefunguje, pokud máte také nastavení testu nakonfigurované pro shromažďování informací IntelliTrace. **Poznámka:**  Tento adaptér diagnostických dat je použitelný pouze pro nastavení testu sady Visual Studio. Nepoužívá se pro nastavení testu ve Správci testů společnosti Microsoft. Kromě toho tento adaptér je pro kompatibilitu s testovacími projekty sady Visual Studio 2010. **Poznámka:**  Z důvodu kompatibility se pokrytí kódu použije při spuštění automatizovaných testů ze správce testů společnosti Microsoft nebo vzdáleného testovacího agenta ze sady Visual Studio pomocí staršího spuštění MSTest.|
|**Protokol událostí:** Můžete nakonfigurovat nastavení testu tak, aby zahrnovalo shromažďování protokolu událostí, které je zahrnuto ve výsledcích testu.|Ano|Ano|Ano||
|**IntelliTrace:** Adaptér diagnostických dat pro *intelliTrace* můžete nakonfigurovat tak, aby shromažďoval konkrétní informace o trasování diagnostiky, které pomáhají izolovat chyby, které je obtížné reprodukovat. Tím se vytvoří soubor IntelliTrace, který obsahuje tyto informace. Soubor IntelliTrace má příponu *.iTrace*. Pokud se test nezdaří, můžete vytvořit chybu. Soubor IntelliTrace, který je uložen spolu s výsledky testů je automaticky propojen s touto chybou. Data shromážděná v souboru IntelliTrace zvyšuje produktivitu ladění zkrácením doby potřebné k reprodukci a diagnostice chyby v kódu. Z tohoto souboru IntelliTrace může být místní relace simulována v jiném počítači. Tím se snižuje riziko, že chyba není reprodukovatelná.|Ano|Ano|Ano|- Pokud povolíte shromažďování dat IntelliTrace, shromažďování dat pokrytí kódu nefunguje.<br />- Pokud používáte IntelliTrace pro roli webového klienta, musíte také vybrat ASP.NET proxy klienta pro adaptér diagnostických dat IntelliTrace a Test Impact.<br />- Podporovány jsou pouze následující verze iis: IIS 7.0, IIS 7.5 a IIS 8.0.|
|**Emulace sítě:** Můžete určit, že chcete umístit umělé zatížení sítě na test pomocí nastavení testu. Emulace sítě ovlivňuje komunikaci do a ze zařízení emulací určité rychlosti připojení k síti, například telefonického připojení. |Ne|Ano (viz poznámky)|Ne|Adaptér diagnostických dat emulace sítě můžete použít pro roli klienta nebo serveru. Není třeba používat adaptér na obou těchto rolí, které vzájemně komunikují. **Poznámka:**  Tento adaptér diagnostických dat je použitelný pouze pro nastavení testu sady Visual Studio. Nepoužívá se pro nastavení testu ve Správci testů společnosti Microsoft. **Poznámka:**  Emulaci sítě nelze použít ke zvýšení rychlosti připojení k síti. **Upozornění:**  Pokud do nastavení testu zahrnete adaptér diagnostických dat emulace sítě a chcete jej použít v místním počítači, musíte také svázat ovladač emulace sítě s jedním ze síťových adaptérů počítače. Ovladač emulace sítě je vyžadován pro funkci adaptéru diagnostických dat emulace sítě. Ovladač emulace sítě je nainstalován a vázán na adaptér dvěma způsoby: <ul><li>**Ovladač emulace sítě nainstalovaný s testovacím agentem sady Microsoft Visual Studio:** Testovací agent sady Visual Studio lze použít na vzdálených počítačích i v místním počítači. Při instalaci testovacího agenta sady Visual Studio zahrnuje proces instalace krok konfigurace, který váže ovladač emulace sítě na síťovou kartu. Další informace naleznete v [tématu Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).</li><li>**Ovladač emulace sítě nainstalovaný v aplikaci Microsoft Visual Studio Test Professional:** Při prvním použití emulace sítě budete vyzváni k vytvoření svázání ovladače emulace sítě se síťovou kartou.</li></ul> Ovladač emulace sítě můžete také nainstalovat z příkazového řádku v místním počítači bez instalace testovacího agenta sady Visual Studio pomocí následujícího **příkazu: VSTestConfig NETWORKEMULATION /install** **Upozornění:** Zátěžové testy adaptér emulace sítě ignorují. Místo toho zátěžové testy použít nastavení, které jsou zadány v kombinaci sítě scénáře zátěžového testu.|
|**Systémové informace:** Nastavení testu lze nastavit tak, aby zahrnovalo systémové informace o počítači, na kterém je test spuštěn.|Ano|Ano|Ano||
|**Dopad zkoušky:** Můžete shromažďovat informace o tom, které metody kódu aplikace byly použity při spuštění testovacího případu. To lze použít společně se změnami kódu aplikace, který byl proveden vývojáři k určení, které testy byly ovlivněny těmito změnami vývoje.|Ano|Ano|Ano|- Pokud shromažďujete data dopadu testu pro roli webového klienta, musíte také vybrat ASP.NET proxy klienta pro adaptér diagnostických dat IntelliTrace a Test Impact.<br />- Podporovány jsou pouze následující verze iis: IIS 7.0, IIS 7.5 a IIS 8.0.|
|**Videorekordér:** Při spuštění testu můžete vytvořit videozáznam relace na ploše. Video může pomoci ostatním členům týmu izolovat problémy s aplikacemi, které je obtížné reprodukovat.|Ano|Ano (viz poznámky)|Ano|- Pokud povolíte spuštění softwaru testovacího agenta jako proces namísto služby, můžete při spuštění automatizovaných testů vytvořit záznam videa.|
