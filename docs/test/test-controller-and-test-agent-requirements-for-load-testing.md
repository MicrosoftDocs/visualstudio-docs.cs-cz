---
title: Požadavky testovacího kontroléru a agenta Test Agent pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8a5cc1f58e0cbdb59458311a1b9a4390bf69bbff
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051446"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Testovací kontrolér a testovací agent požadavky pro zátěžové testování

Některé typy včetně částí, výkonu webu, zátěžových testů a ručních testů jsou integrované do sady Visual Studio. Visual Studio umožňuje uživatelům aplikace Visual Studio Application Lifecycle Management ke spuštění testů na vzdálených počítačích pomocí testovacího kontroléru a jednoho nebo více agentů. Zobrazit [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>Požadavky na hardware a software

Testovací kontrolér a testovací počítače agenta mají určité hardwarové a softwarové požadavky. Kromě toho pokud chcete nasadit řadič testu a počítače testovacích agentů ve více jazycích, je nutné naplánovat způsob podpory těchto jazyků.

### <a name="hardware-requirements"></a>Požadavky na hardware

V následující tabulce jsou uvedeny doporučené požadavky na hardware pro nasazení test kontroléru a testovacích agentů.

|**Konfigurace**|**Komponenta**|**CPU**|**HD**|**Paměť**|
|-|-------------------|-|------------|-|
|< 500 virtuálních uživatelů|Testovací agent|2,6 GHz|10 GB|2 GB|
|< 1000 virtuálních uživatelů|Testovací agent|Dvoujádrový procesor 2,6 GHz|10 GB|2 GB|
|N x 1000 virtuálních uživatelů|Testovací agent|Horizontální navýšení kapacity na N agentů každý s duálním procesorem 2,6 Ghz|10GB|2GB|
|\< 30 počítačů v testovacím prostředí. To zahrnuje agenty a servery v rámci testu.|Kontroler testů|2,6 GHz|||
|N x 30 počítačů v testovacím prostředí. To zahrnuje agenty a servery v rámci testu.|Kontroler testů|N procesorů 2,6 GHz|||

> [!NOTE]
> Počet virtuálních uživatelů se liší běžně z testu. Klíčové příčiny této odchylky je odchylka v *časy přemýšlení*, nebo zpoždění uživatele. Další informace najdete v tématu [zvažte úpravy časy pro simulaci prodlev při zásahem ze strany obsluhy webu](../test/edit-think-times-in-load-test-scenarios.md). V rámci zátěžového testu webové testy jsou obecně efektivnější a generují větší zatížení než testování částí. Čísla v předchozí tabulce jsou platné pro spuštění webových testů s 3 až 5 sekund časy přemýšlení u typické webové aplikace.

Zde uvedené pokyny slouží jako obecné pokyny pro plánování hardwaru. Testování výkonu se liší, protože vždycky záleží na objemu testovacích dat a počtu testovacích agentů. Pro testovací agenty bude rychlost procesoru a paměti omezovat zkušební zatížení. Testovací kontroléry vyžadují větší prostředky, v závislosti na počtu testovacích agentů a množství dat v rámci testů.

Server, na kterém běží Visual Studio by měl mít spolehlivé síťové připojení s minimální šířkou pásma 1 MB/s a maximální čekací doba 350 MS. Měla by existovat žádná brána firewall mezi testovacími agenty a testovacím kontrolérem. Pokud váš testovací výkon nesplňuje vaše očekávání, zvažte upgrade konfigurace hardwaru.

### <a name="additional-hardware-considerations"></a>Další hardwarové požadavky

Testovací agenti generuje velké množství dat na testovacích kontrolérech v závislosti na době trvání testu a velikost testu. Obecně platí je třeba naplánovat dalších 10 GB úložiště na pevném disku pro každých 24 hodin testovacích dat.

Kromě zde doporučeného hardwaru byste zvážit další hardware pro kritické servery, například redundantní napájecí zdroje a záložní ventilátory.

### <a name="language-requirements"></a>Jazykové požadavky

Abyste zamezili nedorozumění a zjednodušili operaci, testovací kontrolér a testovací agenty musí být nakonfigurovaný pro použití stejného jazyka jako operační systém a že Team Foundation Server. Pokud testovací agent a testovací kontroler jsou nainstalované na různých počítačích, musí být nakonfigurované používat stejný jazyk. Můžete však nainstalovat jinou jazykovou verzi sady Visual Studio v anglickém operačního systému, tak dlouho, dokud tento jazyk odpovídá nasazení serveru Team Foundation Server.

## <a name="monitor-agent-resources"></a>Sledování prostředků agenta

Můžete monitorovat počítače agentů k určení potřeb prostředků pozorováním *QTAgent\*.exe* procesy, které se spustí a škálování během testů. Nejběžnější problémové místo v *QTAgent\*.exe* procesů je využití procesoru. Pokud využití procesoru je trvale v vysokou nineties je jako ukazatel toho, že agent je silně načítání. Další běžné problémovým místem je využití paměti. Vyhovovat i vašim náročným testy, monitorování těchto prostředků pomůže zjistit, zda by měl zvýšit prostředky počítače nebo jinak distribuci testů.

## <a name="see-also"></a>Viz také:

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)