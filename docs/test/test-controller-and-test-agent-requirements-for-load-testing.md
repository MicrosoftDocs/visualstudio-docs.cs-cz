---
title: Požadavky testovacího kontroléru a agenta Test Agent pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39b174b0b134fdfdf26570565aa6aa756ba43c92
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588639"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Požadavky zkušebního regulátoru a zkušebního činidla pro zátěžové zkoušky

Několik typů testů, včetně jednotky, výkonu webu, zatížení a ruční testy jsou integrovány do sady Visual Studio. Visual Studio umožňuje uživatelům správy životního cyklu aplikací sady Visual Studio spouštět testy ve vzdálených počítačích pomocí testovacího řadiče a jednoho nebo více agentů. Viz [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>Požadavky na hardware a software

Testovací řadič i počítače testovacího agenta mají specifické požadavky na hardware a software. Kromě toho, pokud chcete nasadit testovací řadič a počítače testovacího agenta ve více jazycích, musíte naplánovat, jak tyto jazyky podporovat.

### <a name="hardware-requirements"></a>Požadavky na hardware

V následující tabulce jsou uvedeny doporučené hardwarové požadavky pro nasazení testovacího řadiče a testovacích agentů.

|**Konfigurace**|**Komponenta**|**Cpu**|**Hd**|**Paměti**|
|-|-------------------|-|------------|-|
|< 500 virtuálních uživatelů|Testovací činidlo|2,6 GHz|10 GB|2 GB|
|< 1000 virtuálních uživatelů|Testovací činidlo|Duální procesor 2,6 GHz|10 GB|2 GB|
|N x 1000 virtuálních uživatelů|Testovací činidlo|Horizontální navýšení kapacity pro agenty N s dual2.6 Ghz|10 GB|2 GB|
|\<30 počítačů v testovacím prostředí. To zahrnuje agenty a servery testované.|Testovací řadič|2,6 GHz|||
|N x 30 počítačů v testovacím prostředí. To zahrnuje agenty a servery testované.|Testovací řadič|N 2,6 GHz procesory|||

> [!NOTE]
> Počet virtuálních uživatelů se bude v jednotlivých testech značně lišit. Hlavní příčinou této odchylky je odchylka v *době přemýšlení*nebo zpoždění uživatelů. Další informace naleznete v [tématu Úprava doby přemýšlení pro simulaci zpoždění interakce s lidmi na webu](../test/edit-think-times-in-load-test-scenarios.md). V zátěžovém testu jsou webové testy obecně efektivnější a generují větší zatížení než testy částí. Čísla v předchozí tabulce jsou platná pro spuštění webových testů s 3-5 sekund časy přemýšlení na typické webové aplikace.

Zde uvedené pokyny jsou uvedeny jako obecné pokyny pro plánování hardwaru. Výkon testu se bude značně lišit v závislosti na množství testovacích dat a počtu testovacích agentů. U testovacích agentů bude rychlost procesoru a dostupná paměť omezit zatížení testu. Řadiče testů potřebují větší prostředky v závislosti na počtu testovacích agentů a množství dat zapojených do testů.

Server se spuštěným souborem Visual Studio by měl mít spolehlivé síťové připojení s minimální šířkou pásma 1 Mb/s a latencí maximálně 350 ms. Mezi testovacími agenty a testovacím řadičem by neměla existovat žádná brána firewall. Pokud výkon testu nesplňuje vaše očekávání, zvažte upgrade konfigurace hardwaru.

### <a name="additional-hardware-considerations"></a>Další důležité informace o hardwaru

Testovací agenti generovat velké množství dat na řadiče testu, v závislosti na trvání testu a velikost testu. Obecně byste měli naplánovat dalších 10 GB úložiště pevného disku pro každých 24 hodin testovacích dat.

Kromě zde doporučeného hardwaru byste měli zvážit další hardware pro kritické servery, jako jsou redundantní napájecí zdroje a redundantní ventilátory.

### <a name="language-requirements"></a>Jazykové požadavky

Aby se zabránilo nejasnostem a zjednodušit provoz, testovací řadič a testovací agenti by měly být nakonfigurovány tak, aby používaly stejný jazyk jako operační systém počítače a operační systém Team Foundation Server. Pokud jsou testovací agent a testovací řadič nainstalovány v různých počítačích, musí být nakonfigurovány tak, aby používaly stejný jazyk. Můžete však nainstalovat jinou jazykovou verzi sady Visual Studio do operačního systému v angličtině, pokud se tento jazyk shoduje s jazykem nasazení team foundation serveru.

## <a name="monitor-agent-resources"></a>Monitorování prostředků agenta

Můžete sledovat počítače agentů k určení jejich potřeby prostředků sledováním procesů *QTAgent\*.exe,* které se spouštějí a škálují během testů. Nejběžnější mačkání bodů procesů *QTAgent\*.exe* je využití procesoru. Pokud využití procesoru je konzistentně ve vysokých devadesátých let pak je údaj, že agent je načten silně. Dalším společným kritickým bodem je využití paměti. Pro náročné testy může monitorování těchto prostředků pomoci určit, zda byste měli zvýšit prostředky počítačů nebo distribuovat testy jinak.

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
